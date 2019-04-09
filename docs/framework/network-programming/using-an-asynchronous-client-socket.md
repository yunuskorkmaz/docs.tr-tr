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
# <a name="using-an-asynchronous-client-socket"></a><span data-ttu-id="5be52-102">Zaman Uyumsuz İstemci Yuvası Kullanma</span><span class="sxs-lookup"><span data-stu-id="5be52-102">Using an Asynchronous Client Socket</span></span>
<span data-ttu-id="5be52-103">Zaman uyumsuz istemci yuvası ağ işlemlerinin tamamlanması beklenirken uygulama askıya almaz.</span><span class="sxs-lookup"><span data-stu-id="5be52-103">An asynchronous client socket does not suspend the application while waiting for network operations to complete.</span></span> <span data-ttu-id="5be52-104">Bunun yerine, ağ bağlantısı bir iş parçacığı üzerinde uygulama özgün iş parçacığı üzerinde çalışmaya devam ederken işlemek için standart .NET Framework zaman uyumsuz programlama modeli kullanır.</span><span class="sxs-lookup"><span data-stu-id="5be52-104">Instead, it uses the standard .NET Framework asynchronous programming model to process the network connection on one thread while the application continues to run on the original thread.</span></span> <span data-ttu-id="5be52-105">Zaman uyumsuz yuva, ağ kullanımı yoğun oluşturan veya devam etmeden önce tamamlamak ağ işlemleri için sabırsızlanıyoruz uygulamalar için uygundur.</span><span class="sxs-lookup"><span data-stu-id="5be52-105">Asynchronous sockets are appropriate for applications that make heavy use of the network or that cannot wait for network operations to complete before continuing.</span></span>  
  
 <span data-ttu-id="5be52-106"><xref:System.Net.Sockets.Socket> Sınıfı aşağıdaki gibi .NET Framework adlandırma deseni için zaman uyumsuz yöntemler; Örneğin, zaman uyumlu <xref:System.Net.Sockets.Socket.Receive%2A> yöntemi karşılık gelen için zaman uyumsuz <xref:System.Net.Sockets.Socket.BeginReceive%2A> ve <xref:System.Net.Sockets.Socket.EndReceive%2A> yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="5be52-106">The <xref:System.Net.Sockets.Socket> class follows the .NET Framework naming pattern for asynchronous methods; for example, the synchronous <xref:System.Net.Sockets.Socket.Receive%2A> method corresponds to the asynchronous <xref:System.Net.Sockets.Socket.BeginReceive%2A> and <xref:System.Net.Sockets.Socket.EndReceive%2A> methods.</span></span>  
  
 <span data-ttu-id="5be52-107">Zaman uyumsuz işlemleri, işlemin sonucunu döndürmek için bir geri çağırma yöntemini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="5be52-107">Asynchronous operations require a callback method to return the result of the operation.</span></span> <span data-ttu-id="5be52-108">Uygulamanızı sonucu bilmeniz gerekmez, geri çağırma yöntemi yok gereklidir.</span><span class="sxs-lookup"><span data-stu-id="5be52-108">If your application does not need to know the result, then no callback method is required.</span></span> <span data-ttu-id="5be52-109">Bu bölümdeki örnek kodu bir ağ aygıtı ve bağlantı verileri gönder tamamlamak için bir geri çağırma yöntemi göndermek başlatmak için bir yöntem ve veri almaya başlaması için bir yöntem tamamlamak için bir geri çağırma yöntemi bağlamak, başlatmak için bir yöntem kullanılarak gösterir ve Alıcı veri sonlandırmak için geri çağırma yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5be52-109">The example code in this section demonstrates using a method to start connecting to a network device and a callback method to complete the connection, a method to start sending data and a callback method to complete the send, and a method to start receiving data and a callback method to end receiving data.</span></span>  
  
 <span data-ttu-id="5be52-110">Zaman uyumsuz yuva birden çok iş parçacığı işlemi ağ bağlantıları için sistem iş parçacığı havuzu kullanın.</span><span class="sxs-lookup"><span data-stu-id="5be52-110">Asynchronous sockets use multiple threads from the system thread pool to process network connections.</span></span> <span data-ttu-id="5be52-111">Bir iş parçacığına gönderme veya alma veri başlatmaktan sorumludur; diğer iş parçacıklarını ağ aygıtı için bağlantıyı tamamlamak ve veri gönderme veya alma.</span><span class="sxs-lookup"><span data-stu-id="5be52-111">One thread is responsible for initiating the sending or receiving of data; other threads complete the connection to the network device and send or receive the data.</span></span> <span data-ttu-id="5be52-112">Aşağıdaki örneklerde, örneklerini <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> sınıfı, yürütme devam edebilirsiniz, ana iş parçacığı ve sinyal yürütülmesini askıya almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5be52-112">In the following examples, instances of the <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> class are used to suspend execution of the main thread and signal when execution can continue.</span></span>  
  
 <span data-ttu-id="5be52-113">Bir ağ aygıtı için zaman uyumsuz bir yuva bağlanmak için aşağıdaki örnekte `Connect` yöntemi başlatır bir **yuva** ve <xref:System.Net.Sockets.Socket.Connect%2A?displayProperty=nameWithType> yöntemini bir uzak uç noktası ağ aygıtını temsil eder , Bağlan geri çağırma yöntemini ve durum nesnesi (istemci **yuva**), zaman uyumsuz çağrılar arasında durumunu bilgi geçirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5be52-113">In the following example, to connect an asynchronous socket to a network device, the `Connect` method initializes a **Socket** and then calls the <xref:System.Net.Sockets.Socket.Connect%2A?displayProperty=nameWithType> method, passing a remote endpoint that represents the network device, the connect callback method, and a state object (the client **Socket**), which is used to pass state information between asynchronous calls.</span></span> <span data-ttu-id="5be52-114">Örnek uygulayan `Connect` yöntemini belirtilen **yuva** belirtilen uç noktası için.</span><span class="sxs-lookup"><span data-stu-id="5be52-114">The example implements the `Connect` method to connect the specified **Socket** to the specified endpoint.</span></span> <span data-ttu-id="5be52-115">Genel bir varsayar **ManualResetEvent** adlı `connectDone`.</span><span class="sxs-lookup"><span data-stu-id="5be52-115">It assumes a global **ManualResetEvent** named `connectDone`.</span></span>  
  
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
  
 <span data-ttu-id="5be52-116">Connect geri çağırma yöntemi `ConnectCallback` uygulayan <xref:System.AsyncCallback> temsilci.</span><span class="sxs-lookup"><span data-stu-id="5be52-116">The connect callback method `ConnectCallback` implements the <xref:System.AsyncCallback> delegate.</span></span> <span data-ttu-id="5be52-117">Uzak cihaza uzak cihaz olduğunda ve ardından uygulama iş parçacığı bağlantı ayarlayarak tamamlandığını bildirir. bağladığı **ManualResetEvent** `connectDone`.</span><span class="sxs-lookup"><span data-stu-id="5be52-117">It connects to the remote device when the remote device is available and then signals the application thread that the connection is complete by setting the **ManualResetEvent** `connectDone`.</span></span> <span data-ttu-id="5be52-118">Aşağıdaki kod uygulayan `ConnectCallback` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5be52-118">The following code implements the `ConnectCallback` method.</span></span>  
  
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
  
 <span data-ttu-id="5be52-119">Örnek yöntemini `Send` belirtilen dize veri ASCII biçimindedir kodlar ve ağ aygıtına belirtilen yuva tarafından temsil edilen zaman uyumsuz olarak gönderir.</span><span class="sxs-lookup"><span data-stu-id="5be52-119">The example method `Send` encodes the specified string data in ASCII format and sends it asynchronously to the network device represented by the specified socket.</span></span> <span data-ttu-id="5be52-120">Aşağıdaki örnek uygulayan `Send` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5be52-120">The following example implements the `Send` method.</span></span>  
  
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
  
 <span data-ttu-id="5be52-121">Send geri çağırma yöntemi `SendCallback` uygulayan <xref:System.AsyncCallback> temsilci.</span><span class="sxs-lookup"><span data-stu-id="5be52-121">The send callback method `SendCallback` implements the <xref:System.AsyncCallback> delegate.</span></span> <span data-ttu-id="5be52-122">Ağ aygıtı almaya hazır olduğunda verileri gönderir.</span><span class="sxs-lookup"><span data-stu-id="5be52-122">It sends the data when the network device is ready to receive.</span></span> <span data-ttu-id="5be52-123">Aşağıdaki örnek uygulamasını gösterir `SendCallback` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5be52-123">The following example shows the implementation of the `SendCallback` method.</span></span> <span data-ttu-id="5be52-124">Genel bir varsayar **ManualResetEvent** adlı `sendDone`.</span><span class="sxs-lookup"><span data-stu-id="5be52-124">It assumes a global **ManualResetEvent** named `sendDone`.</span></span>  
  
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
  
 <span data-ttu-id="5be52-125">Bir istemci yuvadan verileri okuma değerleri arasında zaman uyumsuz çağrıları geçiren bir durum nesnesi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="5be52-125">Reading data from a client socket requires a state object that passes values between asynchronous calls.</span></span> <span data-ttu-id="5be52-126">Aşağıdaki örnek durumu nesnenin veri istemci yuvası gönderimini sınıftır.</span><span class="sxs-lookup"><span data-stu-id="5be52-126">The following class is an example state object for receiving data from a client socket.</span></span> <span data-ttu-id="5be52-127">Bir alan için istemci yuvası alınan veriler için bir arabellek içerir ve bir <xref:System.Text.StringBuilder> gelen veri dizesi tutacak.</span><span class="sxs-lookup"><span data-stu-id="5be52-127">It contains a field for the client socket, a buffer for the received data, and a <xref:System.Text.StringBuilder> to hold the incoming data string.</span></span> <span data-ttu-id="5be52-128">Bu alanlar durumu nesnesinde yerleştirme istemci yuvadan verileri okumak için birden çok çağrı arasında saklanması değerleri verir.</span><span class="sxs-lookup"><span data-stu-id="5be52-128">Placing these fields in the state object allows their values to be preserved across multiple calls to read data from the client socket.</span></span>  
  
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
  
 <span data-ttu-id="5be52-129">Örnek `Receive` yöntemi durumu nesne ayarlar ve ardından çağırır **BeginReceive** verileri istemci yuvadan zaman uyumsuz olarak okumak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="5be52-129">The example `Receive` method sets up the state object and then calls the **BeginReceive** method to read the data from the client socket asynchronously.</span></span> <span data-ttu-id="5be52-130">Aşağıdaki örnek uygulayan `Receive` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5be52-130">The following example implements the `Receive` method.</span></span>  
  
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
  
 <span data-ttu-id="5be52-131">Receive geri çağırma yöntemi `ReceiveCallback` uygulayan **AsyncCallback** temsilci.</span><span class="sxs-lookup"><span data-stu-id="5be52-131">The receive callback method `ReceiveCallback` implements the **AsyncCallback** delegate.</span></span> <span data-ttu-id="5be52-132">Bu ağ aygıtından verileri alır ve bir ileti dizisi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5be52-132">It receives the data from the network device and builds a message string.</span></span> <span data-ttu-id="5be52-133">Bir veya daha fazla bayt veri ağdan veri arabelleğe okur ve ardından çağırır **BeginReceive** yeniden istemci tarafından gönderilen verilerin kadar yöntemi tamamlandığında.</span><span class="sxs-lookup"><span data-stu-id="5be52-133">It reads one or more bytes of data from the network into the data buffer and then calls the **BeginReceive** method again until the data sent by the client is complete.</span></span> <span data-ttu-id="5be52-134">Tüm verileri okuma sonra istemciden `ReceiveCallback` uygulama iş parçacığı ayarlayarak, verilerin tam olduğunu bildirir **ManualResetEvent** `sendDone`.</span><span class="sxs-lookup"><span data-stu-id="5be52-134">Once all the data is read from the client, `ReceiveCallback` signals the application thread that the data is complete by setting the **ManualResetEvent** `sendDone`.</span></span>  
  
 <span data-ttu-id="5be52-135">Aşağıdaki kod örneği uygulayan `ReceiveCallback` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5be52-135">The following example code implements the `ReceiveCallback` method.</span></span> <span data-ttu-id="5be52-136">Adlı bir genel dize varsayar `response` alınan dize ve genel bir tutan **ManualResetEvent** adlı `receiveDone`.</span><span class="sxs-lookup"><span data-stu-id="5be52-136">It assumes a global string named `response` that holds the received string and a global **ManualResetEvent** named `receiveDone`.</span></span> <span data-ttu-id="5be52-137">Sunucunun, düzgün bir şekilde ağ oturumu sonlandırmak için istemci yuvası kapatmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5be52-137">The server must shut down the client socket gracefully to end the network session.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5be52-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5be52-138">See also</span></span>

- [<span data-ttu-id="5be52-139">Zaman Uyumlu İstemci Yuvası Kullanma</span><span class="sxs-lookup"><span data-stu-id="5be52-139">Using a Synchronous Client Socket</span></span>](../../../docs/framework/network-programming/using-a-synchronous-client-socket.md)
- [<span data-ttu-id="5be52-140">Yuvalarla Dinleme</span><span class="sxs-lookup"><span data-stu-id="5be52-140">Listening with Sockets</span></span>](../../../docs/framework/network-programming/listening-with-sockets.md)
- [<span data-ttu-id="5be52-141">Zaman Uyumsuz İstemci Yuvası Örneği</span><span class="sxs-lookup"><span data-stu-id="5be52-141">Asynchronous Client Socket Example</span></span>](../../../docs/framework/network-programming/asynchronous-client-socket-example.md)
