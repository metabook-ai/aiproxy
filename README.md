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
