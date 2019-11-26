BOS.Oracle 介绍: 见证与变革
----------

# 一、背景

区块链广为人知，底层技术已经有了比较大的突破，但是应用场景并不多，主要还是链处于一个封闭的系统，无法与外界信息通讯。但是如果能将人类社会中已有的数据通过**可信的方式**上传到链上，打通区块链与现实世界通路，这样就可以大大增加区块链的应用场景。

在现实世界中，商家如果不能确定能收到钱就不会将商品出售，消费者如果不能确定商品的真伪就不敢贸然购买。“可信”是现实世界中交易的最基本条件，如果我们无法达成信任那么也就无法完成交易。信任对我们来说是如此的重要，然而很多时候难以达成信任，往往只能依赖于交易双方的信誉（这本质上是依托于以往的交易历史，做概率上的估计）或者依托于某个可信的第三方（它是否真的可信，信任的基础又来自于哪里？）。在复杂的现实环境中，这使得我们承担了更多的风险，耗费了更多的精力和资源。怎样解决这一问题？能否结合区块链技术来改变这一现状？BOS 的预言机（Oracle）服务就是我们的答案，希望能够作为区块链与现实世界的数据桥梁。

有些预言机服务的设计是基于可信数据源或者权威数据源这一假设，这样的假设从理论上来说有很大风险，无法保证这种数据源提供数据的真实性。BOS 的预言机系统从构建之初所遵循的原则就是： 

    不依赖于每一个预言机数据提供者一定会提供真实数据，而是承认其不足进而将其作为博弈的参与方加入到系统中来，以期在博弈中达到整体可信

这样在博弈过程中只要将参与方与现实世界的角色进行映射，那么不但能得到区块链输入数据的可信性，同时我们还可以向现实世界输出“信任”。事实上这更像是一个基于区块链的可信平台，而它的服务展示形式是预言机。BOS 预言机将会使得区块链的价值从其货币属性延伸到了交易和规则的构建上，这种延伸将会解决或改进许多现实世界的信任问题，从而扩大区块链的应用边界，并最终让区块链技术可以在交易转账以外场景落地。

# 二、介绍

## 2.1 系统组成
![系统组成](https://raw.githubusercontent.com/boscore/Documentation/master/imgs/oralce/bosoracle_structure.png)

BOS 预言机为了应对不同情形、不同级别的预言机服务冲突，采用“**双向举证**”，通过“**不同仲裁员**”和“**多轮仲裁**”等机制来得到最终仲裁结果。在仲裁中采用抵押机制作为最终处罚锚点，申诉制和检举制同时进行，相互监督；用收益分成以及惩罚金作为奖励的方式激励仲裁员，并且引入信用体系以实现非一次性博弈下模型的稳定和可信。 

预言机服务功能：提供数据、获取数据、仲裁功能

预言机服务角色：提供方、使用方、DAPP合约方、仲裁员

预言机服务特点：仲裁体系完善、博弈模型完备、正向激励系统化、场景覆盖广

## 2.2 提供预言机服务

数据提供方可以在 BOS 上创建自己的数据服务上传数据供大家使用，最终将数据价值变现。

## 2.3 使用预言机服务

数据使用者可以根据自己的需求使用已有预言机服务，也可以作为发起方参与到相应预言机服务当中，并从服务上获取所需的数据。 

针对丰富的预言机服务，使用者可以方便的在 Oracle Store 查询、检索对应的预言机服务。

## 2.4 仲裁功能

仲裁模块是系统公平的来源。为了避免行贿的达成，系统采用了多轮仲裁、每一轮仲裁员人数逐级增加的方案。随着仲裁员规模的扩大将使行贿变越来越困难，成本也急剧提高，最终会导致行贿失败。 

BOS 预言机的仲裁模型中会分成两个阶段：  

- “全职仲裁员”阶段，该阶段的仲裁员共 21 名，他们必须对仲裁案件进行及时的响应；这一阶段总共可以进行3轮仲裁，每一轮人数为3、5、9，并且每轮人数不重复；
- “大众仲裁员”阶段，该阶段会让整个预言机系统的参与者加入，大范围进行仲裁，随机选择抽样，以多数为准；“大众仲裁员”的数量会有一定规则，防止女巫攻击。

![bosoraclegamemodel](https://raw.githubusercontent.com/boscore/Documentation/master/imgs/oralce/bosoracle_game_model.png)  

## 2.5 智能风控

为最大限度的保证安全，“智能风控”始终能够保证数据提供者有足够的抵押 Token 被锁定来对其进行惩罚。它的主要逻辑是使用基于预言机服务DApp的玩家将 Token 直接转入到“智能风控”的账户而不是 DApp 项目方的账户，当有人针对该预言机服务发起仲裁的时候，“智能风控”将会根据数据提供者的历史行为以及当前支出等信息智能的计算出资金冻结时间以及解冻周期。如果整个过程没有出现异常，DApp 项目方可以正常地从“智能风控”账户提取 Token。

“智能风控”是一个可选项，取决于 DApp 项目方是否采用。但从市场竞争的角度来看，为用户提供更多保障的 DApp 将会获得更多的青睐。

![智能风控](https://raw.githubusercontent.com/boscore/Documentation/master/imgs/oralce/bosoracle_risk_control.png)  

## 2.6 文档变量约定

下文出现的变量的含义：

- `${contract_oracle}`： BOS预言机服务合约账户
- `${provider_account}`： 数据提供方账户

## 2.7 预言机全局参数配置

在部署完 Oracle 合约以后，需要进行系统参数初始化。

```
cleos push action ${contract_oracle} setparameter '{"version":1,"parameters":{"core_symbol":"BOS","precision":4,"min_service_stake_limit":1000,"min_appeal_stake_limit":200,"min_reg_arbitrator_stake_limit":10000,"arbitration_correct_rate":60,"round_limit":3,"arbi_timeout_value":86400,"arbi_freeze_stake_duration":259200,"time_deadline":86400,"clear_data_time_length":10800,"max_data_size":256,"min_provider_limit":1,"max_provider_limit":100,"min_update_cycle":1,"max_update_cycle":8640000,"min_duration":1,"max_duration":8640000,"min_acceptance":1,"max_acceptance":100}}' -p ${contract_oracle} -s -j -d  > setconfig.json

cleos multisig propose_trx setconfig bppermission.json setconfig.json  -p ${account}   

cleos multisig approve ${account} setconfig '{"actor":"${account}","permission":"active"}' -p ${account}

cleos multisig exec ${account} setconfig -p ${account}
```

参数说明：

- version：整型，版本必须匹配参数顺序和参数属性数目，初始为 1
- core_symbol：币种名称，默认为 BOS
- precision：币种精度，如1.0000 BOS， 默认为 4
- min_service_stake_limit：提供服务需要抵押的最少金额，默认为 1000
- min_appeal_stake_limit：申诉者或应诉者需要抵押的基数 ，第 N 轮需要抵押金额为`2^(N-1)*min_appeal_stake_limit`，默认为 200
- min_reg_arbitrator_stake_limit：申请仲裁员最少需要抵押的金额，默认为 10000
- arbitration_correct_rate：备选仲裁员的仲裁正确率下限，默认为 60
- round_limit：最大仲裁轮数，该轮结果为最终结果，默认为 3
- arbi_timeout_value：仲裁超时时间，即仲裁案件超时时间、再次申诉超时时间、提供者或仲裁员响应超时时间、上传仲裁结果时间，单位秒，默认为 86400
- arbi_freeze_stake_duration：仲裁过程中，申诉者提起申诉受理后，提供者押金被冻结的时长，单位秒，默认为 259200
- time_deadline：使用者发送数据请求，等待数据的超时时间，超时后提供数据无法获取奖励，单位秒，默认为 86400
- clear_data_time_length：数据表oracledata清理时间，单位秒，默认为 10800
- max_data_size：所有action memo的最大长度，单位字节，默认为 256
- min_provider_limit： 一个服务至少有多少提供者才能创建，默认为 1
- max_provider_limit：一个服务至多不能超过多少提供者，默认为 100
- min_update_cycle：数据最少更新周期，单位秒，默认为 1
- max_update_cycle：数据最大更新周期，单位秒，默认为 8640000
- min_duration：数据最少收集期限，单位秒，默认为 1
- max_duration：数据最大收集期限，单位秒，默认为 8640000
- min_acceptance：确定性数据可显示最少数据提供者数，如该值为5，必须有5个数据提供者在期限内同时提供相同数据，数据才会出现在oracledata表，默认为 1
- max_acceptance：确定性数据服务最大可接受数据提供者数，默认为 100


# 三、数据提供方相关操作

_注：文章中以命令讲解，相关功能都可以在 Oracle Store 页面进行操作_


## 3.1 注册服务

任何人都可以创建数据服务，并由创建者设置服务基本参数。数据服务创建好后，任何人均可以通过转账质押的方式加入并成为数据提供方，注册时需要**抵押保证金，且保证金不低于服务设置的保证金**才能可成为服务的数据提供方。

```
cleos push action ${contract_oracle} regservice '{"account":"${create_account}","base_stake_amount":"1000.0000 BOS","data_format":"json", "data_type":0, "criteria":"以多数人为准", "acceptance":51, "injection_method":0, "duration":500,"provider_limit":3, "update_cycle":600}' -p ${account}
```

**参数说明：**

- `account`：创建服务的账户名
- `base_stake_amount`：服务的最低抵押 Token 的额度 1000
- `data_format`：数据格式，分为：text、json、custom，如果是 json 格式，需要输入`{"xxx":"xxxx"}`
- `data_type`：数据类型，0为确定性，1为不确定性
- `criteria`：服务准则，当有人对服务发起申诉时，仲裁员会根据证据和服务准则进行裁判
- `acceptance`：相同数据提供者所占百分比的最小值，小于该值时数据无效，比如共有10个数据提供者，`51`就意为至少5个提供相同数据
- `injection_method`：注入方式，0为写入表，后续版本实现其他方式 
- `duration`：数据收集持续时间，单位为秒
- `provider_limit`：数据服务开启所需数据提供方数量的最低阈值
- `update_cycle` ：更新周期，超过这个周期将进入下一个 `cycle_number`，单位为秒

## 3.2 加入服务

首先，要查找感兴趣的预言机服务

```
cleos get table ${contract_oracle} ${contract_oracle} dataservices 
```

发现目标服务，通过转账质押 EOS 注册加入相应服务

```
cleos transfer ${provider_account} ${contract_oracle} "1000.0000 BOS" "0,${service_id}"  
```

若创建者没有发现要注册的服务，可以先注册服务，然后再加入。 

**转账抵押 memo 说明：**
- `num`：转账抵押类型，**0为加入服务**
- `service_id`：服务 ID

### 3.2.1 示例

**步骤1：查看所有服务信息**

```
cleos get table ${contract_oracle} ${contract_oracle} dataservices
```

结果：
```
{
  "rows": [{
      "service_id": 1,
      "data_type": 0,
      "status": 1,
      "injection_method": 0,
      "acceptance": 3,
      "duration": 3000,
      "provider_limit": 3,
      "update_cycle": 3600,
      "last_update_number": 0,
      "appeal_freeze_period": 0,
      "exceeded_risk_control_freeze_period": 0,
      "guarantee_id": 0,
      "base_stake_amount": "1000.0000 BOS",
      "risk_control_amount": "0.0000 BOS",
      "pause_service_stake_amount": "0.0000 BOS",
      "data_format": "json",
      "criteria": "以多数人为准",
      "update_start_time": "2019-09-19T03:00:00"
    },{
      "service_id": 2,
      "data_type": 0,
      "status": 0,
      "injection_method": 0,
      "acceptance": 3,
      "duration": 3000,
      "provider_limit": 3,
      "update_cycle": 3600,
      "last_update_number": 0,
      "appeal_freeze_period": 0,
      "exceeded_risk_control_freeze_period": 0,
      "guarantee_id": 0,
      "base_stake_amount": "1000.0000 BOS",
      "risk_control_amount": "0.0000 BOS",
      "pause_service_stake_amount": "0.0000 BOS",
      "data_format": "{\"data\":\"2019-05-07\",\"time\":\"12:22:21\"}",
      "criteria": "以多数人为准",
      "update_start_time": "2019-09-19T03:00:00"
    }
  ],
  "more": false
}
```

一个预言机服务状态`status`有以下几种：

- `service_init`，初始化
- `service_in`，正常可用
- `service_cancel`，取消
- `service_pause`，暂停
- `service_freeze`，冻结
- `service_emergency`，紧急
- `service_pause_insufficient_providers`，由于提供者不足暂停

**步骤2：加入 service_id 为1 的服务**

```
cleos transfer oracleprovi1 ${contract_oracle} "1000.0000 BOS" "0,1"
```

**步骤3：加入成功后，可以通过命令查看到当前服务下有 `oracleprovi1`**

```
cleos get table ${contract_oracle} 1 svcprovision
```

结果：
```
{
  "rows": [{
      "service_id": 1,
      "account": "oracleprovi1",
      "amount": "1000.0000 BOS",
      "freeze_amount": "0.0000 BOS",der
      "service_income": "0.0000 BOS",
      "status": 0,
      "public_information": "",
      "create_time": "2019-09-26T02:30:31"
    }
  ],
  "more": false
}
```


## 3.3 数据提供方减少抵押

数据提供方可减少服务抵押金，但是减少后的抵押金额不能低于服务设置的最低金额。
```
cleos push action ${contract_oracle} unstakeasset '{"service_id":${service_id},"account":"${provider_account}","amount":"1.0000 BOS","memo":"unstake mount"}' -p ${provider_account} 
```

**参数说明：**

- `service_id`：提供方想要解抵押的服务 ID
- `account`：想要解抵押的数据提供方账户
- `amount`：解抵押金额
- `memo`：备注信息

## 3.4 上传数据

预言机服务加入成功后，即可将数据上传：

```
cleos push action ${contract_oracle} pushdata '{"service_id":1,"provider":"${provider_account} ","cycle_number":"3","request_id":0,"data":"1 test data json 3 "}' -p ${provider_account}
```

**参数说明：**
- `service_id`：服务 ID
- `provider`：数据提供方
- `cycle_number`：更新编号，编号是根据服务的 `update_cycle` 计算出来的，计算公式`cycle_number=当前秒数/update_cycle`；每一轮超过时间大于 `duration` 时，不允许上传数据
- `request_id`：数据使用者发起请求时的 id，数据提供方上传数据需要对应，1.0 版本 `request_id` 为 0
- `data`：为上传数据的内容，所有的数据提供方需按照服务的规定上传数据，否则将上传失败


# 四、Dapp 项目方相关操作

Dapp 方可根据 `service_id` 通过查询数据表获取数据。如果服务是确定性数据类型，则每个 `cycle_number` 只能看到一条数据；若服务为不确定性数据类型，服务的每个 `cycle_number` 能看到多条数据，用户需要根据自己的需要进行选择。 

```
cleos get table ${contract_oracle} ${service_id} oracledata
```

**参数说明：**
- `service_id`：服务 ID

## 4.1 确定性数据：
以彩票结果为例，服务 ID 5 为彩票结果服务
```
cleos get table ${contract_oracle} 5 oracledata
{
  "rows": [{
      "record_id": 0,
      "request_id": 0,
      "cycle_number": 2,
      "data": "02 03 01 17 12 04 05",
      "timestamp": 1569554558
    },{
      "record_id": 1,
      "request_id": 0,
      "cycle_number": 4,
      "data": "02 12 34 11 02 04 15",
      "timestamp": 1569563694
    }
  ],
  "more": false
}
```

## 4.2 不确定数据：
以 BTC 价格为例，先查找到当前的服务 ID，发现对应的服务 ID 为7，获取当前服务所有的 BTC 价格：
```
cleos get table ${contract_oracle} 7 oracledata
```

结果：
```
{
  "rows": [{
      "record_id": 0,
      "request_id": 0,
      "cycle_number": 1,
      "data": "time:2019-09-27T03:27:33.216857+00:00,price:8901 USDT",
      "timestamp": 1569552869
    },{
      "record_id": 1,
      "request_id": 0,
      "cycle_number": 1,
      "data": "time:2019-09-27T03:29:33.216857+00:00,price:8911 USDT",
      "timestamp": 1569552932
    },{
      "record_id": 2,
      "request_id": 0,
      "cycle_number": 1,
      "data": "time:2019-09-27T03:29:33.216857+00:00,price:8910 USDT",
      "timestamp": 1569552965
    }
  ],
  "more": false
}
```

# 五、如何进行仲裁

## 5.1 注册仲裁员（抵押）

第一届全职仲裁员由21个指定的 BOS WPS Auditors 来担任；后期开放社区注册，为了保证仲裁有效且公正，仲裁员竞选者需要经过社区的投票，满足条件才有资格当选。注册时最低抵押金为 100000 BOS。

转账抵押注册仲裁员：
```
cleos transfer ${arbitrator_account} ${contract_oracle} "100000.0000 BOS" "${num},${arbitrat_type}" -p ${arbitrator_account}  
```
例如：
```
cleos transfer ${arbitrator_account} ${contract_oracle} "100000.0000 BOS" "4,1" -p ${arbitrator_account}  
```

**转账抵押 memo 说明：**
- `${arbitrator_account}`：仲裁员账户
- `num`：转账抵押类型，4为注册
- `arbitrat_type`：1为全职仲裁员，2为大众仲裁员（后期支持）

## 5.2 仲裁

如果用户或DAPP方在使用过程中，若发现服务数据有问题，可申请仲裁解决。  

说明：

- 如果没有接受应诉，系统会判无响应方定败诉，扣除相应的押金，若为数据提供方则扣除其抵押保证金。
- 如果仲裁员没有应诉，系统会重新从剩余的仲裁员中选择适合的人数发送邀请通知。
- 仲裁过程会通过转账方式发送通知给相关方的账户，Oracle Store 也会通过注册的渠道进行通知推送。

一个仲裁案件共有9中状态，用 `arbi_step` 代表，分别如下：
1. `arbi_init` 仲裁开始
2. `arbi_choosing_arbitrator` 选择仲裁员
3. `arbi_wait_for_resp_appeal` 等待应诉
4. `arbi_wait_for_accept_arbitrate_invitation` 等待仲裁员接受邀请
5. `arbi_wait_for_upload_result` 等待仲裁员上传结果
6. `arbi_wait_for_reappeal` 等待再申诉
7. `arbi_resp_appeal_timeout_end` 应诉超时
8. `arbi_reappeal_timeout_end` 再申诉超时
9. `arbi_public_end` 仲裁公布结果


可以根据 `arbitration_id` 仲裁案件 ID 查看仲裁当前的流程以及相关信息：

```
cleos get table ${contract_oracle} ${arbitration_id} arbicase
```

字段解释: 

- `arbitration_id`：仲裁案件 ID
- `arbi_step`：案件当前状态
- `last_round`：案件最后进行的轮次
- `final_result`: 1 为申诉者胜利，2 为应诉者胜利
- `arbitrators`:  可用仲裁员列表
- `chosen_arbitrators`: 当前选中仲裁员列表
  

比如，查看 `arbitration_id` 为4的仲裁情况：

```
cleos get table ${contract_oracle} 4 arbicase
```

结果：

```
{
  "rows": [{
      "arbitration_id": 4,
      "arbi_step": 6,
      "arbitration_result": 2,
      "last_round": 2,
      "final_result": 0,
      "answer_arbitrators": [
        "arbitrator12",
        "arbitrator14",
        "arbitrator35",
        "arbitrator23",
        "arbitrator15",
        "arbitrator42",
        "arbitrator22",
        "arbitrator13"
      ],
      "chosen_arbitrators": [
        "arbitrator12",
        "arbitrator35",
        "arbitrator14",
        "arbitrator23",
        "arbitrator15",
        "arbitrator42",
        "arbitrator22",
        "arbitrator13"
      ]
    }
  ],
  "more": false
}
```

### 5.2.1 账户发起申诉

数据使用者或者数据提供方发现有人作弊，提供错误的虚假信息，都可发起申诉；申诉时首次抵押金额不得低于200 BOS，后续每轮抵押都不能少于：`200*2^(N-1), N为轮数`。

转账抵押发起申诉：

```
cleos transfer ${initiator_account} ${contract_oracle} "200.0000 BOS" "3,${service_id},'evidence','info','reason','${role}'" -p ${initiator_account} 
```

**转账抵押memo说明：**
- `initiator_account`：发起账户
- `num`：转账抵押类型，**3 为申诉**
- `service_id`: 想要申诉的服务 ID
- `evidence`: 申诉时提交的证据，推荐为 IPFS 文件地址
- `info`: 公示信息
- `reason`: 申诉该服务的原因
- `role`：表示发起诉讼的人的身份，1-代表数据使用者，2-代表数据提供者

申诉命令发出后，会通过 transfer 发出通知，通知给所有受诉方，任何一个账户应诉（包含通知之外的账户），案件均可以成立。

### 5.2.2 受诉账户应诉

当有人申诉时，相关人员会接收申诉通知，这时需要执行应诉命令告知对方接受申诉，这时仲裁流程正式开启；如果没有人应诉，超时后，将直接判定申诉者为胜利一方，如果是数据提供方是败诉方，会将该数据服务所有抵押金扣除，分配给申诉者。

其中应诉抵押金第一轮至少200 BOS，后续每轮抵押都不能少于：`200*2^(N-1), N为轮数`。

```
cleos transfer ${accept_account} ${contract_oracle} "200.0000 BOS" "5,${arbitrat_id},'evidence'" -p ${accept_account} 
```

**转账抵押memo说明：**
- `accept_account`：应诉者账户
- `num`：转账抵押类型，**5 为应诉**
- `arbitrat_id`：仲裁 ID
- `evidence`：应诉时提交的证据，推荐为 IPFS 文件地址

### 5.2.3 仲裁员接受邀请

当数据提供方应诉后，会给仲裁员发送仲裁邀请，只有 `2^N+1` 个仲裁员接受邀请后，才能进入下一步：上传仲裁结果。如果有仲裁员超时接受邀请，则会重新从剩余的仲裁员中选择，直至 `2^N+1` 个仲裁员全部接受， N为轮数。

仲裁员接受邀请：

```
cleos push action ${contract_oracle} acceptarbi '["${arbitrator}",${arbitrat_id}]' -p ${arbitrator}@active 
```

**参数说明：**

- `arbitrator`：接收仲裁邀请的仲裁员账户
- `arbitrat_id`：接收邀请的仲裁 ID

### 5.2.4 仲裁员上传仲裁结果

仲裁员上传仲裁结果：

```
cleos push action ${contract_oracle} uploadresult '["${arbitrator}",${arbitrat_id}, ${result},'memo']' -p {arbitrator}@active
```

**参数说明：**

- `arbitrator`：仲裁员账户
- `arbitrat_id`：仲裁 ID
- `result`： 1 为申诉者胜利，2 为应诉者胜利
- `memo`：备注信息，需要包含裁决过程的 IPFS 文件地址

### 5.2.5 仲裁结束

仲裁结束有两种：

- 仲裁结果上传后，如果没有人再次发起申诉，72小时后，该仲裁关闭；
- 在 1.0 版本中，只支持`全职仲裁员`参与，最多可进行三轮仲裁。

仲裁结束后，本次仲裁得出最终结果，相关账户得奖励/惩罚。

## 5.3 仲裁相关者可以领取仲裁案件的收益

仲裁案件结束之后，参与仲裁的相关人员可以得到奖励，因为仲裁过程中涉及到三个不同的角色，申诉者、应诉者、仲裁员，针对不同的角色收益的分配方式也不同，仲裁收益需要主动领取。

- 仲裁员：激励来源于**败诉者抵押金**
- 数据使用者：如果胜利，则数据提供方所有的**服务抵押金**都会被平均分配给所有的**申诉账户**，申诉抵押金会退还
- 数据提供方：如果胜利，申诉抵押金会退还
- 如果是数据提供方起诉其他数据提供方，胜方均分对方的**服务抵押金**


查看仲裁收益：

```
cleos get table ${contract_oracle} ${account} arbiincomes
```

领取收益：

```
cleos push action ${contract_oracle} claimarbi '["${account}","${receive_account}"]' -p ${account}
```

**参数说明：**
- `account`：在仲裁案件中有收益的账户
- `receive_account`：收益的接收账户

## 5.4 解除仲裁抵押

仲裁结束后，胜诉者可以将自己抵押的 Token 解抵押，通过查表方式查看自己的抵押金额。 

**1. 查询该仲裁当前抵押Token数量：**

```
cleos get table ${contract_oracle} ${arbitrat_id} arbistakeacc
```

参数说明：

`arbitrat_id`：表示想要查询的仲裁案件 ID，若当前仲裁案件已经结束，该值为 `uint64_t(1)<<63 + arbitrat_id`

**2. 解抵押：**

```
cleos push action ${contract_oracle} unstakearbi '{"arbitration_id":${arbitrat_id},"account":"${account}","amount":"100.0000 BOS","memo":"unstake mount"}' -p ${account} 
```

**参数说明：**
- `arbitrat_id`：仲裁 ID
- `account`：解抵押的账户名
- `amount`：解抵押的 Token 的个数，不能大于抵押的数量
- `memo`：备注 

# 六、转账抵押memo说明汇总

memo 说明：`"转账质押类型,服务 ID,……."`

**1. 注册服务：**
memo 说明：`"0,服务 ID"`

```
cleos transfer ${provider_account} ${contract_oracle} "1000.0000 BOS" "0,${service_id}" 
```

**2. 申诉服务：**
memo 说明：`"3,服务 ID,证据,公示信息,申诉原因,角色"`

```
cleos transfer ${initiator_account} ${contract_oracle} "200.0000 BOS" "3,${service_id},'evidence','info','reason','${role}'" -p ${initiator_account}    
```

**3. 注册仲裁员：**
memo 说明：`"4,服务 ID"`

```
cleos transfer ${arbitrator_account}  ${contract_oracle} "10000.0000 BOS" "4,1" -p ${arbitrator_account}  
```

**4. 应诉：**
memo 说明：`"5,服务 ID,证据"`

```
cleos transfer ${accept_account}  ${contract_oracle} "200.0000 BOS" "5,${service_id},'evidence'" -p ${accept_account} 
```


# 七、预言机查表汇总

**1. 查询所有当前服务信息**
```
cleos get table ${contract_oracle} ${contract_oracle} dataservices
```

**2. 查询某个服务的详细信息**
```
cleos get table ${contract_oracle} ${service_id} svcprovision
```

**3. 查询某个服务的所有数据显示**
```
cleos get table ${contract_oracle} ${service_id} oracledata
```

**4. 查询当前所有数据提供方信息**
```
cleos get table ${contract_oracle} ${contract_oracle} providers
```

**5. 查询当前所有仲裁人员信息**
```
cleos get table ${contract_oracle} ${contract_oracle} arbitrators
```

**6. 查询某个仲裁案件的流程进度**
```
cleos get table ${contract_oracle} ${arbitrat_id} arbicase
```

**7. 查询某个仲裁案件上传的证据**
```
cleos get table ${contract_oracle} ${arbitrat_id} arbievidence
```

**8. 查询某个进行中的仲裁案件抵押金信息**
```
cleos get table ${contract_oracle} ${arbitrat_id} arbistakeacc
```

**9. 查询某个已结束的仲裁案件抵押金信息**
```
cleos get table ${contract_oracle}  ${9223372036854775808+arbitrat_id} arbistakeacc
```

**10. 查看仲裁收益表**
```
cleos get table ${contract_oracle} ${account} arbiincomes
```