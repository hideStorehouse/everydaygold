# everydaygold
// Quantumult X 脚本示例：获取每日金价  
  
// 定义一个函数来发送HTTP GET请求  
function sendHttpRequest(url, callback) {  
    var xhr = new XMLHttpRequest();  
    xhr.open("GET", url, true);  
    xhr.onreadystatechange = function () {  
        if (xhr.readyState == 4 && xhr.status == 200) {  
            // 请求成功，调用回调函数并传入响应文本  
            callback(xhr.responseText);  
        }  
    };  
    xhr.send();  
}  
  
// 调用API并处理响应  
var apiUrl = "https://api.tanshuapi.com/api/gold/v1/shgold?key=00a7c17b548077eac8d848d7e0bcf22e"; // 替换为真实的API URL  
sendHttpRequest(apiUrl, function(response) {  
    // 假设API返回的是JSON格式的数据  
    try {  
        var data = JSON.parse(response);  
        // 提取金价信息，这里假设金价在data.price字段中  
        var goldPrice = data.price; // 根据实际API的返回结构进行调整  
        console.log("今日金价: " + goldPrice); // 在Quantumult X的日志中打印金价  
        // 你可以在这里添加其他逻辑，比如将金价显示在通知栏中  
    } catch (e) {  
        console.error("解析API响应失败: ", e);  
    }  
});
