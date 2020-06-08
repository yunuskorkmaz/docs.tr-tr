---
title: Zaman Uyumsuz İstemci Yuvası Kullanma
description: Bu örnek, zaman uyumsuz bir istemci yuvasını gösterir. .NET Framework zaman uyumsuz programlama, bir bağlantıyı işlerken uygulamanın çalışmaya devam etmesine olanak tanır.
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
ms.openlocfilehash: 9cf46e9519bcecf4d7a20ff99b86fa5f66af2087
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502047"
---
# <a name="using-an-asynchronous-client-socket"></a><span data-ttu-id="6038c-104">Zaman Uyumsuz İstemci Yuvası Kullanma</span><span class="sxs-lookup"><span data-stu-id="6038c-104">Using an Asynchronous Client Socket</span></span>
<span data-ttu-id="6038c-105">Zaman uyumsuz bir istemci yuvası, ağ işlemlerinin tamamlanmasını beklerken uygulamayı askıya almaz.</span><span class="sxs-lookup"><span data-stu-id="6038c-105">An asynchronous client socket does not suspend the application while waiting for network operations to complete.</span></span> <span data-ttu-id="6038c-106">Bunun yerine, uygulama orijinal iş parçacığında çalışmaya devam ederken bir iş parçacığında ağ bağlantısını işlemek için standart .NET Framework zaman uyumsuz programlama modelini kullanır.</span><span class="sxs-lookup"><span data-stu-id="6038c-106">Instead, it uses the standard .NET Framework asynchronous programming model to process the network connection on one thread while the application continues to run on the original thread.</span></span> <span data-ttu-id="6038c-107">Zaman uyumsuz yuvalar, ağı yoğun şekilde kullanan veya devam etmeden önce ağ işlemlerinin tamamlanmasını bekleyemez uygulamalar için uygundur.</span><span class="sxs-lookup"><span data-stu-id="6038c-107">Asynchronous sockets are appropriate for applications that make heavy use of the network or that cannot wait for network operations to complete before continuing.</span></span>  
  
 <span data-ttu-id="6038c-108"><xref:System.Net.Sockets.Socket>Sınıfı, zaman uyumsuz metotlar için .NET Framework adlandırma düzeniyle uyar; Örneğin, zaman uyumlu <xref:System.Net.Sockets.Socket.Receive%2A> Yöntem zaman uyumsuz <xref:System.Net.Sockets.Socket.BeginReceive%2A> ve yöntemlere karşılık gelir <xref:System.Net.Sockets.Socket.EndReceive%2A> .</span><span class="sxs-lookup"><span data-stu-id="6038c-108">The <xref:System.Net.Sockets.Socket> class follows the .NET Framework naming pattern for asynchronous methods; for example, the synchronous <xref:System.Net.Sockets.Socket.Receive%2A> method corresponds to the asynchronous <xref:System.Net.Sockets.Socket.BeginReceive%2A> and <xref:System.Net.Sockets.Socket.EndReceive%2A> methods.</span></span>  
  
 <span data-ttu-id="6038c-109">Zaman uyumsuz işlemler işlemin sonucunu döndürmek için bir geri çağırma yöntemi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="6038c-109">Asynchronous operations require a callback method to return the result of the operation.</span></span> <span data-ttu-id="6038c-110">Uygulamanızın sonucu bilmeleri gerekmiyorsa, geri arama yöntemi gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="6038c-110">If your application does not need to know the result, then no callback method is required.</span></span> <span data-ttu-id="6038c-111">Bu bölümdeki örnek kod, bir ağ cihazına bağlanmaya başlamak için bir yöntem ve bağlantıyı tamamlamaya yönelik bir geri çağırma yöntemi, gönderimi tamamlamaya yönelik bir yöntem ve gönderme yöntemi ile verileri almaya başlamak için bir yöntem ve geri çağırma yöntemi kullanmayı göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="6038c-111">The example code in this section demonstrates using a method to start connecting to a network device and a callback method to complete the connection, a method to start sending data and a callback method to complete the send, and a method to start receiving data and a callback method to end receiving data.</span></span>  
  
 <span data-ttu-id="6038c-112">Zaman uyumsuz yuvalar, ağ bağlantılarını işlemek için sistem iş parçacığı havuzundan birden çok iş parçacığı kullanır.</span><span class="sxs-lookup"><span data-stu-id="6038c-112">Asynchronous sockets use multiple threads from the system thread pool to process network connections.</span></span> <span data-ttu-id="6038c-113">Bir iş parçacığı, verilerin gönderilmesini veya alınmasını başlatmaktan sorumludur; diğer iş parçacıkları ağ cihazına bağlantıyı tamamlar ve verileri gönderir veya alır.</span><span class="sxs-lookup"><span data-stu-id="6038c-113">One thread is responsible for initiating the sending or receiving of data; other threads complete the connection to the network device and send or receive the data.</span></span> <span data-ttu-id="6038c-114">Aşağıdaki örneklerde, sınıfının örnekleri, <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> yürütme devam edebilme durumunda ana iş parçacığı ve sinyalin yürütülmesini askıya almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6038c-114">In the following examples, instances of the <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> class are used to suspend execution of the main thread and signal when execution can continue.</span></span>  
  
 <span data-ttu-id="6038c-115">Aşağıdaki örnekte, bir ağ cihazına zaman uyumsuz bir yuva bağlamak için `Connect` yöntemi bir **yuva** başlatır ve sonra, <xref:System.Net.Sockets.Socket.Connect%2A?displayProperty=nameWithType> ağ cihazını temsil eden bir uzak uç nokta, Connect callback yöntemi ve zaman uyumsuz çağrılar arasında durum bilgilerini geçirmek için kullanılan bir durum nesnesi (istemci **yuvası**) geçirerek yöntemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="6038c-115">In the following example, to connect an asynchronous socket to a network device, the `Connect` method initializes a **Socket** and then calls the <xref:System.Net.Sockets.Socket.Connect%2A?displayProperty=nameWithType> method, passing a remote endpoint that represents the network device, the connect callback method, and a state object (the client **Socket**), which is used to pass state information between asynchronous calls.</span></span> <span data-ttu-id="6038c-116">Örnek, `Connect` belirtilen **yuvayı** belirtilen uç noktaya bağlamak için yöntemini uygular.</span><span class="sxs-lookup"><span data-stu-id="6038c-116">The example implements the `Connect` method to connect the specified **Socket** to the specified endpoint.</span></span> <span data-ttu-id="6038c-117">Adında genel bir **ManualResetEvent** olduğunu varsayar `connectDone` .</span><span class="sxs-lookup"><span data-stu-id="6038c-117">It assumes a global **ManualResetEvent** named `connectDone`.</span></span>  
  
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
  
 <span data-ttu-id="6038c-118">Connect callback yöntemi `ConnectCallback` <xref:System.AsyncCallback> temsilciyi uygular.</span><span class="sxs-lookup"><span data-stu-id="6038c-118">The connect callback method `ConnectCallback` implements the <xref:System.AsyncCallback> delegate.</span></span> <span data-ttu-id="6038c-119">Uzak cihaz kullanılabilir olduğunda uzak cihaza bağlanır ve ardından **ManualResetEvent** ayarlanarak bağlantının tamamlandığını uygulamanın iş parçacığına bildirir `connectDone` .</span><span class="sxs-lookup"><span data-stu-id="6038c-119">It connects to the remote device when the remote device is available and then signals the application thread that the connection is complete by setting the **ManualResetEvent** `connectDone`.</span></span> <span data-ttu-id="6038c-120">Aşağıdaki kod `ConnectCallback` yöntemini uygular.</span><span class="sxs-lookup"><span data-stu-id="6038c-120">The following code implements the `ConnectCallback` method.</span></span>  
  
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
  
 <span data-ttu-id="6038c-121">Örnek yöntem, `Send` ASCII biçiminde belirtilen dize verilerini kodlar ve belirtilen yuva tarafından temsil edilen ağ cihazına zaman uyumsuz olarak gönderir.</span><span class="sxs-lookup"><span data-stu-id="6038c-121">The example method `Send` encodes the specified string data in ASCII format and sends it asynchronously to the network device represented by the specified socket.</span></span> <span data-ttu-id="6038c-122">Aşağıdaki örnek `Send` yöntemini uygular.</span><span class="sxs-lookup"><span data-stu-id="6038c-122">The following example implements the `Send` method.</span></span>  
  
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
  
 <span data-ttu-id="6038c-123">Geri arama gönder yöntemi `SendCallback` temsilciyi uygular <xref:System.AsyncCallback> .</span><span class="sxs-lookup"><span data-stu-id="6038c-123">The send callback method `SendCallback` implements the <xref:System.AsyncCallback> delegate.</span></span> <span data-ttu-id="6038c-124">Ağ aygıtı almaya hazırsa verileri gönderir.</span><span class="sxs-lookup"><span data-stu-id="6038c-124">It sends the data when the network device is ready to receive.</span></span> <span data-ttu-id="6038c-125">Aşağıdaki örnek yönteminin uygulamasını gösterir `SendCallback` .</span><span class="sxs-lookup"><span data-stu-id="6038c-125">The following example shows the implementation of the `SendCallback` method.</span></span> <span data-ttu-id="6038c-126">Adında genel bir **ManualResetEvent** olduğunu varsayar `sendDone` .</span><span class="sxs-lookup"><span data-stu-id="6038c-126">It assumes a global **ManualResetEvent** named `sendDone`.</span></span>  
  
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
  
 <span data-ttu-id="6038c-127">İstemci yuvalarından veri okuma, zaman uyumsuz çağrılar arasında değer geçiren bir durum nesnesi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="6038c-127">Reading data from a client socket requires a state object that passes values between asynchronous calls.</span></span> <span data-ttu-id="6038c-128">Aşağıdaki sınıf, bir istemci yuvasından veri almak için örnek bir durum nesnesidir.</span><span class="sxs-lookup"><span data-stu-id="6038c-128">The following class is an example state object for receiving data from a client socket.</span></span> <span data-ttu-id="6038c-129">İstemci yuvası için bir alan, alınan veriler için bir arabellek ve <xref:System.Text.StringBuilder> gelen veri dizesini tutacak bir alanı içerir.</span><span class="sxs-lookup"><span data-stu-id="6038c-129">It contains a field for the client socket, a buffer for the received data, and a <xref:System.Text.StringBuilder> to hold the incoming data string.</span></span> <span data-ttu-id="6038c-130">Bu alanların durum nesnesine yerleştirilmesi, değerlerinin istemci yuvasında verileri okumak için birden çok çağrıda saklanması sağlar.</span><span class="sxs-lookup"><span data-stu-id="6038c-130">Placing these fields in the state object allows their values to be preserved across multiple calls to read data from the client socket.</span></span>  
  
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
  
 <span data-ttu-id="6038c-131">Örnek `Receive` Yöntem, durum nesnesini ayarlar ve ardından, istemci yuvasından zaman uyumsuz olarak veri okumak Için **BeginReceive** yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="6038c-131">The example `Receive` method sets up the state object and then calls the **BeginReceive** method to read the data from the client socket asynchronously.</span></span> <span data-ttu-id="6038c-132">Aşağıdaki örnek `Receive` yöntemini uygular.</span><span class="sxs-lookup"><span data-stu-id="6038c-132">The following example implements the `Receive` method.</span></span>  
  
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
  
 <span data-ttu-id="6038c-133">Alma geri çağırma yöntemi `ReceiveCallback` , **AsyncCallback** temsilcisini uygular.</span><span class="sxs-lookup"><span data-stu-id="6038c-133">The receive callback method `ReceiveCallback` implements the **AsyncCallback** delegate.</span></span> <span data-ttu-id="6038c-134">Ağ cihazından verileri alır ve bir ileti dizesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6038c-134">It receives the data from the network device and builds a message string.</span></span> <span data-ttu-id="6038c-135">Ağ üzerinden veri arabelleğine bir veya daha fazla bayt okur ve ardından istemci tarafından gönderilen veriler tamamlanana kadar **BeginReceive** metodunu yeniden çağırır.</span><span class="sxs-lookup"><span data-stu-id="6038c-135">It reads one or more bytes of data from the network into the data buffer and then calls the **BeginReceive** method again until the data sent by the client is complete.</span></span> <span data-ttu-id="6038c-136">Tüm veriler istemciden okunduktan sonra, `ReceiveCallback` **ManualResetEvent** ayarlanarak, verilerin tamamlandığını uygulamanın iş parçacığına bildirir `sendDone` .</span><span class="sxs-lookup"><span data-stu-id="6038c-136">Once all the data is read from the client, `ReceiveCallback` signals the application thread that the data is complete by setting the **ManualResetEvent** `sendDone`.</span></span>  
  
 <span data-ttu-id="6038c-137">Aşağıdaki örnek kod `ReceiveCallback` yöntemi uygular.</span><span class="sxs-lookup"><span data-stu-id="6038c-137">The following example code implements the `ReceiveCallback` method.</span></span> <span data-ttu-id="6038c-138">`response`Alınan dizeyi ve genel **ManualResetEvent** 'i tutan adlı bir genel dizeyi kabul eder `receiveDone` .</span><span class="sxs-lookup"><span data-stu-id="6038c-138">It assumes a global string named `response` that holds the received string and a global **ManualResetEvent** named `receiveDone`.</span></span> <span data-ttu-id="6038c-139">Ağ oturumunu sonlandırmak için sunucu istemci yuvasını sorunsuz bir şekilde kapatması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6038c-139">The server must shut down the client socket gracefully to end the network session.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6038c-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6038c-140">See also</span></span>

- [<span data-ttu-id="6038c-141">Zaman Uyumlu İstemci Yuvası Kullanma</span><span class="sxs-lookup"><span data-stu-id="6038c-141">Using a Synchronous Client Socket</span></span>](using-a-synchronous-client-socket.md)
- [<span data-ttu-id="6038c-142">Yuvalarla Dinleme</span><span class="sxs-lookup"><span data-stu-id="6038c-142">Listening with Sockets</span></span>](listening-with-sockets.md)
- [<span data-ttu-id="6038c-143">Zaman Uyumsuz İstemci Yuvası Örneği</span><span class="sxs-lookup"><span data-stu-id="6038c-143">Asynchronous Client Socket Example</span></span>](asynchronous-client-socket-example.md)
