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
ms.openlocfilehash: 4d7020b6bc5049101ec08329d53d966771e38035
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59168902"
---
# <a name="using-an-asynchronous-client-socket"></a>Zaman Uyumsuz İstemci Yuvası Kullanma
Zaman uyumsuz istemci yuvası ağ işlemlerinin tamamlanması beklenirken uygulama askıya almaz. Bunun yerine, ağ bağlantısı bir iş parçacığı üzerinde uygulama özgün iş parçacığı üzerinde çalışmaya devam ederken işlemek için standart .NET Framework zaman uyumsuz programlama modeli kullanır. Zaman uyumsuz yuva, ağ kullanımı yoğun oluşturan veya devam etmeden önce tamamlamak ağ işlemleri için sabırsızlanıyoruz uygulamalar için uygundur.  
  
 <xref:System.Net.Sockets.Socket> Sınıfı aşağıdaki gibi .NET Framework adlandırma deseni için zaman uyumsuz yöntemler; Örneğin, zaman uyumlu <xref:System.Net.Sockets.Socket.Receive%2A> yöntemi karşılık gelen için zaman uyumsuz <xref:System.Net.Sockets.Socket.BeginReceive%2A> ve <xref:System.Net.Sockets.Socket.EndReceive%2A> yöntemleri.  
  
 Zaman uyumsuz işlemleri, işlemin sonucunu döndürmek için bir geri çağırma yöntemini gerektirir. Uygulamanızı sonucu bilmeniz gerekmez, geri çağırma yöntemi yok gereklidir. Bu bölümdeki örnek kodu bir ağ aygıtı ve bağlantı verileri gönder tamamlamak için bir geri çağırma yöntemi göndermek başlatmak için bir yöntem ve veri almaya başlaması için bir yöntem tamamlamak için bir geri çağırma yöntemi bağlamak, başlatmak için bir yöntem kullanılarak gösterir ve Alıcı veri sonlandırmak için geri çağırma yöntemi.  
  
 Zaman uyumsuz yuva birden çok iş parçacığı işlemi ağ bağlantıları için sistem iş parçacığı havuzu kullanın. Bir iş parçacığına gönderme veya alma veri başlatmaktan sorumludur; diğer iş parçacıklarını ağ aygıtı için bağlantıyı tamamlamak ve veri gönderme veya alma. Aşağıdaki örneklerde, örneklerini <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> sınıfı, yürütme devam edebilirsiniz, ana iş parçacığı ve sinyal yürütülmesini askıya almak için kullanılır.  
  
 Bir ağ aygıtı için zaman uyumsuz bir yuva bağlanmak için aşağıdaki örnekte `Connect` yöntemi başlatır bir **yuva** ve <xref:System.Net.Sockets.Socket.Connect%2A?displayProperty=nameWithType> yöntemini bir uzak uç noktası ağ aygıtını temsil eder , Bağlan geri çağırma yöntemini ve durum nesnesi (istemci **yuva**), zaman uyumsuz çağrılar arasında durumunu bilgi geçirmek için kullanılır. Örnek uygulayan `Connect` yöntemini belirtilen **yuva** belirtilen uç noktası için. Genel bir varsayar **ManualResetEvent** adlı `connectDone`.  
  
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
  
 Connect geri çağırma yöntemi `ConnectCallback` uygulayan <xref:System.AsyncCallback> temsilci. Uzak cihaza uzak cihaz olduğunda ve ardından uygulama iş parçacığı bağlantı ayarlayarak tamamlandığını bildirir. bağladığı **ManualResetEvent** `connectDone`. Aşağıdaki kod uygulayan `ConnectCallback` yöntemi.  
  
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
  
 Örnek yöntemini `Send` belirtilen dize veri ASCII biçimindedir kodlar ve ağ aygıtına belirtilen yuva tarafından temsil edilen zaman uyumsuz olarak gönderir. Aşağıdaki örnek uygulayan `Send` yöntemi.  
  
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
  
 Send geri çağırma yöntemi `SendCallback` uygulayan <xref:System.AsyncCallback> temsilci. Ağ aygıtı almaya hazır olduğunda verileri gönderir. Aşağıdaki örnek uygulamasını gösterir `SendCallback` yöntemi. Genel bir varsayar **ManualResetEvent** adlı `sendDone`.  
  
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
  
 Bir istemci yuvadan verileri okuma değerleri arasında zaman uyumsuz çağrıları geçiren bir durum nesnesi gerektirir. Aşağıdaki örnek durumu nesnenin veri istemci yuvası gönderimini sınıftır. Bir alan için istemci yuvası alınan veriler için bir arabellek içerir ve bir <xref:System.Text.StringBuilder> gelen veri dizesi tutacak. Bu alanlar durumu nesnesinde yerleştirme istemci yuvadan verileri okumak için birden çok çağrı arasında saklanması değerleri verir.  
  
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
  
 Örnek `Receive` yöntemi durumu nesne ayarlar ve ardından çağırır **BeginReceive** verileri istemci yuvadan zaman uyumsuz olarak okumak için yöntem. Aşağıdaki örnek uygulayan `Receive` yöntemi.  
  
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
  
 Receive geri çağırma yöntemi `ReceiveCallback` uygulayan **AsyncCallback** temsilci. Bu ağ aygıtından verileri alır ve bir ileti dizisi oluşturur. Bir veya daha fazla bayt veri ağdan veri arabelleğe okur ve ardından çağırır **BeginReceive** yeniden istemci tarafından gönderilen verilerin kadar yöntemi tamamlandığında. Tüm verileri okuma sonra istemciden `ReceiveCallback` uygulama iş parçacığı ayarlayarak, verilerin tam olduğunu bildirir **ManualResetEvent** `sendDone`.  
  
 Aşağıdaki kod örneği uygulayan `ReceiveCallback` yöntemi. Adlı bir genel dize varsayar `response` alınan dize ve genel bir tutan **ManualResetEvent** adlı `receiveDone`. Sunucunun, düzgün bir şekilde ağ oturumu sonlandırmak için istemci yuvası kapatmanız gerekir.  
  
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

- [Zaman Uyumlu İstemci Yuvası Kullanma](../../../docs/framework/network-programming/using-a-synchronous-client-socket.md)
- [Yuvalarla Dinleme](../../../docs/framework/network-programming/listening-with-sockets.md)
- [Zaman Uyumsuz İstemci Yuvası Örneği](../../../docs/framework/network-programming/asynchronous-client-socket-example.md)
