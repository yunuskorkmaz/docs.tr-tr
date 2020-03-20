---
title: Zaman Uyumsuz İstemci Yuvası Kullanma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- sending data, sockets
- data requests, sockets
- asynchronous client sockets
- Socket class, asynchronous client sockets
- requesting data from Internet, sockets
- sockets, asynchronous client sockets
- receiving data, sockets
- protocols, sockets
- Internet, sockets
- client sockets
ms.assetid: fd85bc88-e06c-467d-a30d-9fd7cffcfca1
ms.openlocfilehash: 748745ca6799005dccdbfcbcc37a8c2a38f2a88e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180645"
---
# <a name="using-an-asynchronous-client-socket"></a>Zaman Uyumsuz İstemci Yuvası Kullanma
Asenkron istemci soketi, ağ işlemlerinin tamamlanmasını beklerken uygulamayı askıya almaz. Bunun yerine, uygulama özgün iş parçacığı üzerinde çalışma devam ederken bir iş parçacığı üzerinde ağ bağlantısı işlemek için standart .NET Framework asynchronous programlama modeli kullanır. Asenkron soketler, ağı yoğun olarak kullanan veya devam etmeden önce ağ işlemlerinin tamamlanmasını beklemeyen uygulamalar için uygundur.  
  
 Sınıf, <xref:System.Net.Sockets.Socket> eşzamanlı yöntemler için .NET Framework adlandırma deseni; örneğin, senkron <xref:System.Net.Sockets.Socket.Receive%2A> yöntem asynchronous <xref:System.Net.Sockets.Socket.BeginReceive%2A> ve <xref:System.Net.Sockets.Socket.EndReceive%2A> yöntemleri karşılık gelir.  
  
 Eşkron işlemleri, işlemin sonucunu döndürmek için bir geri arama yöntemi gerektirir. Uygulamanızın sonucu bilmesi gerekmiyorsa, geri arama yöntemi gerekmez. Bu bölümdeki örnek kod, bir ağ aygıtına bağlanmaya başlamak için bir yöntem ve bağlantıyı tamamlamak için bir geri arama yöntemi, veri göndermeye başlamak için bir yöntem ve gönderiyi tamamlamak için bir geri arama yöntemi ve veri almaya başlamak için bir yöntem ve veri almayı sona erdirmek için geri arama yöntemi.  
  
 Asynchronous soketleri, ağ bağlantılarını işlemek için sistem iş parçacığı havuzundan birden çok iş parçacığı kullanır. Bir iş parçacığı, veri gönderme veya alma işlemini başlatmaktan sorumludur; diğer iş parçacıkları ağ aygıtına olan bağlantıyı tamamlar ve verileri gönderir veya alır. Aşağıdaki örneklerde, <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> sınıfın örnekleri, yürütmedevam edebilirsiniz ana iş parçacığı ve sinyal yürütme askıya almak için kullanılır.  
  
 Aşağıdaki örnekte, bir asenkron soketi bir ağ `Connect` aygıtına bağlamak için, yöntem <xref:System.Net.Sockets.Socket.Connect%2A?displayProperty=nameWithType> bir **Soket'i** başharfe geçirir ve ardından kanalı temsil eden uzak bir bitiş noktası, bağlantı geri arama yöntemi ni ve eş durumu nesnesini (istemci **Sok)** asynchronous çağrılar arasında durum bilgilerini aktarmak için kullanılır. Örnek, belirtilen `Connect` **Soketi** belirtilen bitiş noktasına bağlamak için yöntemi uygular. Bu adlı `connectDone`genel bir **ManualResetEvent** varsayar.  
  
```vb  
Public Shared Sub Connect(remoteEP As EndPoint, client As Socket)  
    client.BeginConnect(remoteEP, _  
       AddressOf ConnectCallback, client)  
  
    connectDone.WaitOne()  
End Sub 'Connect  
```  
  
```csharp  
public static void Connect(EndPoint remoteEP, Socket client) {  
    client.BeginConnect(remoteEP,
        new AsyncCallback(ConnectCallback), client );  
  
   connectDone.WaitOne();  
}  
```  
  
 Connect geri arama `ConnectCallback` yöntemi <xref:System.AsyncCallback> temsilciyi uygular. Uzak aygıt kullanılabilir olduğunda uzak aygıta bağlanır ve ardından uygulama iş parçacığına **ManualResetEvent'i** `connectDone`ayarlayarak bağlantının tamamlandığına dair sinyal ler bildirir. Aşağıdaki kod `ConnectCallback` yöntemi uygular.  
  
```vb  
Private Shared Sub ConnectCallback(ar As IAsyncResult)  
    Try  
        ' Retrieve the socket from the state object.  
        Dim client As Socket = CType(ar.AsyncState, Socket)  
  
        ' Complete the connection.  
        client.EndConnect(ar)  
  
        Console.WriteLine("Socket connected to {0}", _  
            client.RemoteEndPoint.ToString())  
  
        ' Signal that the connection has been made.  
        connectDone.Set()  
    Catch e As Exception  
        Console.WriteLine(e.ToString())  
    End Try  
End Sub 'ConnectCallback  
```  
  
```csharp  
private static void ConnectCallback(IAsyncResult ar) {  
    try {  
        // Retrieve the socket from the state object.  
        Socket client = (Socket) ar.AsyncState;  
  
        // Complete the connection.  
        client.EndConnect(ar);  
  
        Console.WriteLine("Socket connected to {0}",  
            client.RemoteEndPoint.ToString());  
  
        // Signal that the connection has been made.  
        connectDone.Set();  
    } catch (Exception e) {  
        Console.WriteLine(e.ToString());  
    }  
}  
```  
  
 Örnek yöntem, `Send` belirtilen dize verilerini ASCII formatında kodlar ve belirtilen soket tarafından temsil edilen ağ aygıtına eşzamanlı olarak gönderir. Aşağıdaki örnek yöntemi `Send` uygular.  
  
```vb  
Private Shared Sub Send(client As Socket, data As [String])  
    ' Convert the string data to byte data using ASCII encoding.  
    Dim byteData As Byte() = Encoding.ASCII.GetBytes(data)  
  
    ' Begin sending the data to the remote device.  
    client.BeginSend(byteData, 0, byteData.Length, SocketFlags.None, _  
        AddressOf SendCallback, client)  
End Sub 'Send  
```  
  
```csharp  
private static void Send(Socket client, String data) {  
    // Convert the string data to byte data using ASCII encoding.  
    byte[] byteData = Encoding.ASCII.GetBytes(data);  
  
    // Begin sending the data to the remote device.  
    client.BeginSend(byteData, 0, byteData.Length, SocketFlags.None,  
        new AsyncCallback(SendCallback), client);  
}  
```  
  
 Geri arama yöntemi `SendCallback` temsilciyi <xref:System.AsyncCallback> uygular. Ağ aygıtı almaya hazır olduğunda verileri gönderir. Aşağıdaki örnek yöntemin `SendCallback` uygulanmasını gösterir. Bu adlı `sendDone`genel bir **ManualResetEvent** varsayar.  
  
```vb  
Private Shared Sub SendCallback(ar As IAsyncResult)  
    Try  
        ' Retrieve the socket from the state object.  
        Dim client As Socket = CType(ar.AsyncState, Socket)  
  
        ' Complete sending the data to the remote device.  
        Dim bytesSent As Integer = client.EndSend(ar)  
        Console.WriteLine("Sent {0} bytes to server.", bytesSent)  
  
        ' Signal that all bytes have been sent.  
        sendDone.Set()  
    Catch e As Exception  
        Console.WriteLine(e.ToString())  
    End Try  
End Sub 'SendCallback  
```  
  
```csharp  
private static void SendCallback(IAsyncResult ar) {  
    try {  
        // Retrieve the socket from the state object.  
        Socket client = (Socket) ar.AsyncState;  
  
        // Complete sending the data to the remote device.  
        int bytesSent = client.EndSend(ar);  
        Console.WriteLine("Sent {0} bytes to server.", bytesSent);  
  
        // Signal that all bytes have been sent.  
        sendDone.Set();  
    } catch (Exception e) {  
        Console.WriteLine(e.ToString());  
    }  
}  
```  
  
 İstemci yuvasından veri okuma, eşsenkronize çağrılar arasında değerleri geçen bir durum nesnesi gerektirir. Aşağıdaki sınıf, istemci yuvasından veri almak için örnek bir durum nesnesidir. İstemci yuvası için bir alan, alınan veriler için <xref:System.Text.StringBuilder> bir arabellek ve gelen veri dizesini tutmak için bir alan içerir. Bu alanların durum nesnesine yerleştirilmesi, istemci yuvasından gelen verileri okumak için değerlerinin birden çok çağrı arasında korunmasına olanak tanır.  
  
```vb  
Public Class StateObject  
    ' Client socket.  
    Public workSocket As Socket = Nothing
    ' Size of receive buffer.  
    Public BufferSize As Integer = 256  
    ' Receive buffer.  
    Public buffer(256) As Byte
    ' Received data string.  
    Public sb As New StringBuilder()  
End Class 'StateObject  
```  
  
```csharp  
public class StateObject {  
    // Client socket.  
    public Socket workSocket = null;  
    // Size of receive buffer.  
    public const int BufferSize = 256;  
    // Receive buffer.  
    public byte[] buffer = new byte[BufferSize];  
    // Received data string.  
    public StringBuilder sb = new StringBuilder();  
}  
```  
  
 Örnek `Receive` yöntem durum nesnesini ayarlar ve istemci yuvadaki verileri eşzamanlı olarak okumak için **BeginReceive** yöntemini çağırır. Aşağıdaki örnek yöntemi `Receive` uygular.  
  
```vb  
Private Shared Sub Receive(client As Socket)  
    Try  
        ' Create the state object.  
        Dim state As New StateObject()  
        state.workSocket = client  
  
        ' Begin receiving the data from the remote device.  
        client.BeginReceive(state.buffer, 0, state.BufferSize, 0, _  
            AddressOf ReceiveCallback, state)  
    Catch e As Exception  
        Console.WriteLine(e.ToString())  
    End Try  
End Sub 'Receive  
```  
  
```csharp  
private static void Receive(Socket client) {  
    try {  
        // Create the state object.  
        StateObject state = new StateObject();  
        state.workSocket = client;  
  
        // Begin receiving the data from the remote device.  
        client.BeginReceive( state.buffer, 0, StateObject.BufferSize, 0,  
            new AsyncCallback(ReceiveCallback), state);  
    } catch (Exception e) {  
        Console.WriteLine(e.ToString());  
    }  
}  
```  
  
 Geri alma yöntemi `ReceiveCallback` **AsyncCallback** temsilcisini uygular. Ağ aygıtından verileri alır ve bir ileti dizesi oluşturur. Ağdan bir veya daha fazla bayt veriyi veri arabelleği ne okur ve istemci tarafından gönderilen veriler tamamlanana kadar **BeginReceive** yöntemini yeniden çağırır. Tüm veriler istemciden okunduktan `ReceiveCallback` sonra, uygulama iş parçacığına **ManualResetEvent'i** `sendDone`ayarlayarak verilerin tamamladığını bildirir.  
  
 Aşağıdaki örnek kod `ReceiveCallback` yöntemi uygular. Alınan dize yi `response` ve genel **manualResetevent** adlı genel `receiveDone`bir dize yi varsayar. Sunucu, ağ oturumunu sonlandıracak şekilde istemci yuvasını incelikle kapatmalıdır.  
  
```vb  
Private Shared Sub ReceiveCallback(ar As IAsyncResult)  
    Try  
        ' Retrieve the state object and the client socket
        ' from the asynchronous state object.  
        Dim state As StateObject = CType(ar.AsyncState, StateObject)  
        Dim client As Socket = state.workSocket  
  
        ' Read data from the remote device.  
        Dim bytesRead As Integer = client.EndReceive(ar)  
  
        If bytesRead > 0 Then  
            ' There might be more data, so store the data received so far.  
            state.sb.Append(Encoding.ASCII.GetString(state.buffer, 0, _  
                bytesRead))  
  
            '  Get the rest of the data.  
            client.BeginReceive(state.buffer, 0, state.BufferSize, 0, _  
                AddressOf ReceiveCallback, state)  
        Else  
            ' All the data has arrived; put it in response.  
            If state.sb.Length > 1 Then  
                response = state.sb.ToString()  
            End If  
            ' Signal that all bytes have been received.  
            receiveDone.Set()  
        End If  
    Catch e As Exception  
        Console.WriteLine(e.ToString())  
    End Try  
End Sub 'ReceiveCallback  
```  
  
```csharp  
private static void ReceiveCallback( IAsyncResult ar ) {  
    try {  
        // Retrieve the state object and the client socket
        // from the asynchronous state object.  
        StateObject state = (StateObject) ar.AsyncState;  
        Socket client = state.workSocket;  
        // Read data from the remote device.  
        int bytesRead = client.EndReceive(ar);  
        if (bytesRead > 0) {  
            // There might be more data, so store the data received so far.  
            state.sb.Append(Encoding.ASCII.GetString(state.buffer,0,bytesRead));  
                //  Get the rest of the data.  
            client.BeginReceive(state.buffer,0,StateObject.BufferSize,0,  
                new AsyncCallback(ReceiveCallback), state);  
        } else {  
            // All the data has arrived; put it in response.  
            if (state.sb.Length > 1) {  
                response = state.sb.ToString();  
            }  
            // Signal that all bytes have been received.  
            receiveDone.Set();  
        }  
    } catch (Exception e) {  
        Console.WriteLine(e.ToString());  
    }  
}  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Zaman Uyumlu İstemci Yuvası Kullanma](using-a-synchronous-client-socket.md)
- [Yuvalarla Dinleme](listening-with-sockets.md)
- [Zaman Uyumsuz İstemci Yuvası Örneği](asynchronous-client-socket-example.md)
