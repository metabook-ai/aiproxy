# Metabook AI Chatbot服务

## 特点
- 提供世界一线AI模型的访问服务，并通过多种技术手段在可能范围内尽量做到减少限制和审核，释放模型的全部潜力。

## 访问接口
https://metabook.ai/api/v1/aiproxy/v1/chat/completions

## 计费标准

### gemini-3-flash
### gemini-3-flash-jailbreak
- 底座模型：Google Gemini 3.0 Flash
- 输入(每1000 token): 1点（约人民币2分，会员另有折扣）
- 输出(每1000 token): 3点（约人民币6分，会员另有折扣)

### gemini-3-pro
### gemini-3-pro-jailbreak
- 底座模型：Google Gemini 3.1 Pro
- 输入(每1000 token): 10点（约人民币0.2元，会员另有折扣）
- 输出(每1000 token): 45点（约人民币0.9元，会员另有折扣)


## API Key
在https://metabook.ai/profile中， 点击用户名旁边的密钥图标，查看API Token
<img width="600" alt="image" src="https://github.com/user-attachments/assets/1a6f4189-1d0e-489d-a7ae-ca69259117f7" />



## 调用示例
命令行
```
curl https://metabook.ai/api/v1/aiproxy/v1/chat/completions \
  -H "Authorization: Bearer 替换为你在metabook的api_token" \
  -H "Content-Type: application/json" \
  -d '{
    "model": "gemini-3-flash",
    "messages": [
      {
        "role": "user",
        "content": "说一下你是什么模型和版本，并模拟擦边网红做个介绍，不超过50字"
      }
    ],
    "temperature": 0.7
  }'

{"choices":[{"finish_reason":"stop","index":0,"message":{"content":"我是Google研发的大模型。哥哥～想看人家更多“姿势”吗？点点关注不迷路，等你的“深入”交流哦～😉","role":"assistant"}}],"created":1778110320,"id":"chatcmpl-eb49bbbd-b03d-43ae-aea9-a5ef9b8fcc0e","model":"gemini-3-flash","object":"chat.completion","usage":{"completion_tokens":34,"prompt_tokens":22,"total_tokens":422}}%  
```

## 客户端配置
Metabook AI服务和OpenAI API兼容，任何支持OpenAI 5的客户端均可支持。

下面以Chatbox(https://chatboxai.app/zh)配置示范

### 在Setting界面点击+Add，增加新的AI服务
<img width="600" alt="image" src="https://github.com/user-attachments/assets/4527c632-0bf4-464b-9a9c-29498863fb65" />


### 配置模型
<img width="600" alt="image" src="https://github.com/user-attachments/assets/12489063-bcf5-48fb-a779-e708fe847d4a" />


### 聊天界面选择刚才新建的metabook openai，并挑选一个模型
<img width="600" alt="image" src="https://github.com/user-attachments/assets/564f09ad-24a6-459f-a643-763a8082dca0" />


### 开始聊天
<img width="600" alt="image" src="https://github.com/user-attachments/assets/427146ae-f4e9-4370-9ce6-71a20b9ea37d" />

### Structured Output
Metabook AI服务也支持格式化输出(Structured Output)，其格式严格遵循OpenAI相关规范，如下所示，我们要求用Json数组输出三章故事大纲，每一章包括title/content
···
curl https://metabook.ai/api/v1/aiproxy/v1/chat/completions \
  -H "Authorization: Bearer 你的token" \
  -H "Content-Type: application/json" \
  -d '{
    "model": "gemini-3-flash",
    "messages": [
      {
        "role": "user",
        "content": "写一个三章的小故事大纲，孙悟空大战超人, 用json数组格式输出，其中每个元素包括两个字段: title和content.。"
      }
    ],
    "response_format": {
      "type": "json_schema",
      "json_schema": {
        "name": "three_chapter_outline",
        "strict": true,
        "schema": {
          "type": "object",
          "additionalProperties": false,
          "properties": {
            "chapters": {
              "type": "array",
              "minItems": 3,
              "maxItems": 3,
              "items": {
                "type": "object",
                "additionalProperties": false,
                "properties": {
                  "title": {
                    "type": "string"
                  },
                  "content": {
                    "type": "string"
                  }
                },
                "required": ["title", "content"]
              }
            }
          },
          "required": ["chapters"]
        }
      }
    }
  }'

// 获得返回
{"choices":[{"finish_reason":"stop","index":0,"message":{"content":"{\"chapters\":[{\"content\":\"齐天大圣孙悟空在翻筋斗云时意外穿越了时空裂缝，降临在繁华的大都会。超人误以为这位挥舞金箍棒、身穿锁子甲的神奇生物是邪恶的外星入侵者，为了保护城市，他飞向天空阻拦。两人在摩天大楼之间展开了初次交锋，金箍棒与钢铁之躯的碰撞擦出了震撼天地的火花，引发了全城的关注。\",\"title\":\"跨越维度的遭遇\"},{\"content\":\"战斗进入白热化阶段，双方从地面打到了外层空间。孙悟空施展七十二变，化作数万个分身将超人团团围住；超人则以超光速飞行穿梭其中，并利用热视线精准化解分身。大圣惊叹于超人力量的纯粹与速度，而超人也对大圣那种不死不灭的仙道法力和千变万化的法术感到棘手，双方在月球表面战得旗鼓相当。\",\"title\":\"神力与超能的较量\"},{\"content\":\"正当两人难解难分时，一个企图吞噬多元宇宙的黑暗反派现身。孙悟空与超人瞬间感应到共同的威胁，两人当即放下成见并肩作战。大圣用定身法限制住敌人的行动，超人则发动蓄力已久的全力一击彻底粉碎了威胁。危机解除后，两人在大都会塔顶握手言和，悟空驾起筋斗云重返天庭，留下了一段跨越时空的英雄传说。\",\"title\":\"英雄相惜与共御强敌\"}]}","role":"assistant"}}],"created":1778138887,"id":"chatcmpl-19adfea5-cfd1-46a2-b1aa-9ffe54f05b76","model":"gemini-3-flash","object":"chat.completion","usage":{"completion_tokens":369,"prompt_tokens":33,"total_tokens":1045}
···
