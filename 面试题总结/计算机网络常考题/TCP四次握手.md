# TCP四次握手

服务端A：发送FIN报文（FIN = 1），序列号为u（seq = u），进入FIN-WAIT 1状态。

客户端B：发送ACK确认报文（ACK = 1），序列号为v（seq = v），确认报文u（ack = u + 1），进入CLOSE-WAIT状态，继续传送数据。

服务端A：收到上述报文进入FIN-WAIT2状态，继续接受B传输的数据。

客户端B：数据传输完毕后，发送FIN报文（FIN = 1，ACK = 1），序列号为w（seq = w），确认报文u（ack = u + 1），进入LAST-ACK状态。

服务端A：发送ACK确认报文（ACK = 1），序列号为u+1（seq = u + 1），确认报文w（ack = w + 1），进入TIME-WAIT状态，等待2MSL（最长报文段寿命），进入CLOSED状态。

客户端B：收到后上述报文后进入CLOSED状态。

