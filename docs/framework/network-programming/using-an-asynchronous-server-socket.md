---
title: Zaman uyumsuz Server yuva kullanma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- sending data, sockets
- Socket class, asynchronous server sockets
- data requests, sockets
- sockets, asynchronous server sockets
- requesting data from Internet, sockets
- server sockets
- receiving data, sockets
- asynchronous server sockets
- protocols, sockets
- Internet, sockets
ms.assetid: 813489a9-3efd-41b6-a33f-371d55397676
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: ad52291f5f5f40a65d2f9ec1c07bfb3a3f39fc01
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33396613"
---
# <a name="using-an-asynchronous-server-socket"></a><span data-ttu-id="7d2dd-102">Zaman uyumsuz Server yuva kullanma</span><span class="sxs-lookup"><span data-stu-id="7d2dd-102">Using an Asynchronous Server Socket</span></span>
<span data-ttu-id="7d2dd-103">Zaman uyumsuz server yuva ağ hizmet isteklerini işlemek için .NET Framework zaman uyumsuz programlama modeli kullanın.</span><span class="sxs-lookup"><span data-stu-id="7d2dd-103">Asynchronous server sockets use the .NET Framework asynchronous programming model to process network service requests.</span></span> <span data-ttu-id="7d2dd-104"><xref:System.Net.Sockets.Socket> Sınıfı izleyen standart .NET Framework zaman uyumsuz adlandırma deseni; Örneğin, zaman uyumlu <xref:System.Net.Sockets.Socket.Accept%2A> yöntemi karşılık gelen için zaman uyumsuz <xref:System.Net.Sockets.Socket.BeginAccept%2A> ve <xref:System.Net.Sockets.Socket.EndAccept%2A> yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="7d2dd-104">The <xref:System.Net.Sockets.Socket> class follows the standard .NET Framework asynchronous naming pattern; for example, the synchronous <xref:System.Net.Sockets.Socket.Accept%2A> method corresponds to the asynchronous <xref:System.Net.Sockets.Socket.BeginAccept%2A> and <xref:System.Net.Sockets.Socket.EndAccept%2A> methods.</span></span>  
  
 <span data-ttu-id="7d2dd-105">Zaman uyumsuz server yuva veri alma sona erdirmek için ağ, bağlantı isteklerini işler ve ağ üzerinden veri almaya başlamak için bir geri çağırma yöntemini ve bir geri çağırma yöntemi gelen bağlantı istekleri kabul başlamak için bir yöntem gerektirir.</span><span class="sxs-lookup"><span data-stu-id="7d2dd-105">An asynchronous server socket requires a method to begin accepting connection requests from the network, a callback method to handle the connection requests and begin receiving data from the network, and a callback method to end receiving the data.</span></span> <span data-ttu-id="7d2dd-106">Tüm bu yöntemleri ele alınan bu bölümün sonraki kısımlarında.</span><span class="sxs-lookup"><span data-stu-id="7d2dd-106">All these methods are discussed further in this section.</span></span>  
  
 <span data-ttu-id="7d2dd-107">Yöntemi ağ gelen bağlantı istekleri kabul başlamak için aşağıdaki örnekte, `StartListening` başlatır **yuva** ve ardından **BeginAccept** yeni kabul başlatmak için yöntemi bağlantılar.</span><span class="sxs-lookup"><span data-stu-id="7d2dd-107">In the following example, to begin accepting connection requests from the network, the method `StartListening` initializes the **Socket** and then uses the **BeginAccept** method to start accepting new connections.</span></span> <span data-ttu-id="7d2dd-108">Yeni bir bağlantı isteği yuvada alındığında kabul geri çağırma yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="7d2dd-108">The accept callback method is called when a new connection request is received on the socket.</span></span> <span data-ttu-id="7d2dd-109">Dağıtımından sorumlu **yuva** bağlantı ve, teslim etme işleyecek örneği **yuva** isteği işleyen iş parçacığına kapalı.</span><span class="sxs-lookup"><span data-stu-id="7d2dd-109">It is responsible for getting the **Socket** instance that will handle the connection and handing that **Socket** off to the thread that will process the request.</span></span> <span data-ttu-id="7d2dd-110">Accept geri çağırma yöntemini uygulayan <xref:System.AsyncCallback> temsilci; tek bir parametre türü alır ve bir geçersiz kılma döndürür <xref:System.IAsyncResult>.</span><span class="sxs-lookup"><span data-stu-id="7d2dd-110">The accept callback method implements the <xref:System.AsyncCallback> delegate; it returns a void and takes a single parameter of type <xref:System.IAsyncResult>.</span></span> <span data-ttu-id="7d2dd-111">Aşağıdaki örnek bir accept geri çağırma yöntemini Kabuk aynıdır.</span><span class="sxs-lookup"><span data-stu-id="7d2dd-111">The following example is the shell of an accept callback method.</span></span>  
  
```vb  
Sub acceptCallback(ar As IAsyncResult)  
    ' Add the callback code here.  
End Sub 'acceptCallback  
```  
  
```csharp  
void acceptCallback( IAsyncResult ar) {  
    // Add the callback code here.  
}  
```  
  
 <span data-ttu-id="7d2dd-112">**BeginAccept** yöntemi iki parametre alan bir **AsyncCallback** accept geri çağırma yöntemini ve durum bilgilerini geri çağırma yöntemi iletmek için kullanılan nesneyi işaret eden temsilci.</span><span class="sxs-lookup"><span data-stu-id="7d2dd-112">The **BeginAccept** method takes two parameters, an **AsyncCallback** delegate that points to the accept callback method and an object that is used to pass state information to the callback method.</span></span> <span data-ttu-id="7d2dd-113">Aşağıdaki örnekte dinleme **yuva** geri çağırma yöntemine geçirilen *durumu* parametresi.</span><span class="sxs-lookup"><span data-stu-id="7d2dd-113">In the following example, the listening **Socket** is passed to the callback method through the *state* parameter.</span></span> <span data-ttu-id="7d2dd-114">Bu örnekte bir **AsyncCallback** temsilci ve ağ gelen bağlantıları kabul başlatır.</span><span class="sxs-lookup"><span data-stu-id="7d2dd-114">This example creates an **AsyncCallback** delegate and starts accepting connections from the network.</span></span>  
  
```vb  
listener.BeginAccept( _  
    New AsyncCallback(SocketListener.acceptCallback),_  
    listener)  
```  
  
```csharp  
listener.BeginAccept(  
    new AsyncCallback(SocketListener.acceptCallback),   
    listener);  
```  
  
 <span data-ttu-id="7d2dd-115">Zaman uyumsuz yuva iş parçacıkları sistem iş parçacığı havuzundan gelen bağlantıları işlemek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="7d2dd-115">Asynchronous sockets use threads from the system thread pool to process incoming connections.</span></span> <span data-ttu-id="7d2dd-116">Bir iş parçacığı bağlantıları kabul etmek için sorumlu olduğu, başka bir iş parçacığı her gelen bağlantı işlemek için kullanılır ve başka bir iş parçacığı bağlantısından veri almak için sorumludur.</span><span class="sxs-lookup"><span data-stu-id="7d2dd-116">One thread is responsible for accepting connections, another thread is used to handle each incoming connection, and another thread is responsible for receiving data from the connection.</span></span> <span data-ttu-id="7d2dd-117">Bu iş parçacığı havuzu tarafından atanan iş parçacığı bağlı olarak, aynı iş parçacığı olabilir.</span><span class="sxs-lookup"><span data-stu-id="7d2dd-117">These could be the same thread, depending on which thread is assigned by the thread pool.</span></span> <span data-ttu-id="7d2dd-118">Aşağıdaki örnekte, <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> sınıf ana iş parçacığı yürütmesi askıya alır ve yürütme devam ederken işaret eder.</span><span class="sxs-lookup"><span data-stu-id="7d2dd-118">In the following example, the <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> class suspends execution of the main thread and signals when execution can continue.</span></span>  
  
 <span data-ttu-id="7d2dd-119">Aşağıdaki örnekte, yerel bilgisayarda bir zaman uyumsuz TCP/IP'yi yuva oluşturur ve bağlantıları kabul başlar zaman uyumsuz bir yöntem gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7d2dd-119">The following example shows an asynchronous method that creates an asynchronous TCP/IP socket on the local computer and begins accepting connections.</span></span> <span data-ttu-id="7d2dd-120">Bunu olduğunu genel varsaydığını **ManualResetEvent** adlı `allDone`, yöntem adlı bir sınıf üyesi olduğunu `SocketListener`, ve bir geri çağırma yöntemi adlı `acceptCallback` tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="7d2dd-120">It assumes that there is a global **ManualResetEvent** named `allDone`, that the method is a member of a class named `SocketListener`, and that a callback method named `acceptCallback` is defined.</span></span>  
  
```vb  
Public Sub StartListening()  
    Dim ipHostInfo As IPHostEntry = Dns.Resolve(Dns.GetHostName())  
    Dim localEP = New IPEndPoint(ipHostInfo.AddressList(0), 11000)  
  
    Console.WriteLine("Local address and port : {0}", localEP.ToString())  
  
    Dim listener As New Socket(localEP.Address.AddressFamily, _  
       SocketType.Stream, ProtocolType.Tcp)  
  
    Try  
        listener.Bind(localEP)  
        listener.Listen(10)  
  
        While True  
            allDone.Reset()  
  
            Console.WriteLine("Waiting for a connection...")  
            listener.BeginAccept(New _  
                AsyncCallback(SocketListener.acceptCallback), _  
                listener)  
  
            allDone.WaitOne()  
        End While  
    Catch e As Exception  
        Console.WriteLine(e.ToString())  
    End Try  
    Console.WriteLine("Closing the listener...")  
End Sub 'StartListening  
```  
  
```csharp  
public void StartListening() {  
    IPHostEntry ipHostInfo = Dns.Resolve(Dns.GetHostName());  
    IPEndPoint localEP = new IPEndPoint(ipHostInfo.AddressList[0],11000);  
  
    Console.WriteLine("Local address and port : {0}",localEP.ToString());  
  
    Socket listener = new Socket( localEP.Address.AddressFamily,  
        SocketType.Stream, ProtocolType.Tcp );  
  
    try {  
        listener.Bind(localEP);  
        listener.Listen(10);  
  
        while (true) {  
            allDone.Reset();  
  
            Console.WriteLine("Waiting for a connection...");  
            listener.BeginAccept(  
                new AsyncCallback(SocketListener.acceptCallback),   
                listener );  
  
            allDone.WaitOne();  
        }  
    } catch (Exception e) {  
        Console.WriteLine(e.ToString());  
    }  
  
    Console.WriteLine( "Closing the listener...");  
}  
```  
  
 <span data-ttu-id="7d2dd-121">Kabul et geri çağırma yöntemi (`acceptCallback` önceki örnekte) işleme, istemci ile bağlantı kurma ve zaman uyumsuz başlatılıyor devam etmek için ana uygulama iş parçacığı sinyal verilerin istemciden okumak için sorumludur.</span><span class="sxs-lookup"><span data-stu-id="7d2dd-121">The accept callback method (`acceptCallback` in the preceding example) is responsible for signaling the main application thread to continue processing, establishing the connection with the client, and starting the asynchronous read of data from the client.</span></span> <span data-ttu-id="7d2dd-122">Aşağıdaki örnek uygulaması ilk parçası olan `acceptCallback` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7d2dd-122">The following example is the first part of an implementation of the `acceptCallback` method.</span></span> <span data-ttu-id="7d2dd-123">Bu bölümde yönteminin işleme devam etmek için ana uygulama iş parçacığı bildirir ve istemci bağlantı kurar.</span><span class="sxs-lookup"><span data-stu-id="7d2dd-123">This section of the method signals the main application thread to continue processing and establishes the connection to the client.</span></span> <span data-ttu-id="7d2dd-124">Bir genel varsayar **ManualResetEvent** adlı `allDone`.</span><span class="sxs-lookup"><span data-stu-id="7d2dd-124">It assumes a global **ManualResetEvent** named `allDone`.</span></span>  
  
```vb  
Public Sub acceptCallback(ar As IAsyncResult)  
    allDone.Set()  
  
    Dim listener As Socket = CType(ar.AsyncState, Socket)  
    Dim handler As Socket = listener.EndAccept(ar)  
  
    ' Additional code to read data goes here.  
End Sub 'acceptCallback  
```  
  
```csharp  
public void acceptCallback(IAsyncResult ar) {  
    allDone.Set();  
  
    Socket listener = (Socket) ar.AsyncState;  
    Socket handler = listener.EndAccept(ar);  
  
    // Additional code to read data goes here.    
}  
```  
  
 <span data-ttu-id="7d2dd-125">Bir istemci yuvadan veri okunurken değerleri arasında zaman uyumsuz çağrılar geçiren bir durum nesnesi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="7d2dd-125">Reading data from a client socket requires a state object that passes values between asynchronous calls.</span></span> <span data-ttu-id="7d2dd-126">Aşağıdaki örnek uzak istemci tarafından bir dizesini almak için bir durum nesnesi uygular.</span><span class="sxs-lookup"><span data-stu-id="7d2dd-126">The following example implements a state object for receiving a string from the remote client.</span></span> <span data-ttu-id="7d2dd-127">Alan veri almak için bir veri arabelleğini istemci yuva için içeriyor ve bir <xref:System.Text.StringBuilder> istemci tarafından gönderilen veri dizesi oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="7d2dd-127">It contains fields for the client socket, a data buffer for receiving data, and a <xref:System.Text.StringBuilder> for creating the data string sent by the client.</span></span> <span data-ttu-id="7d2dd-128">Bu alanların durumu nesnesinde yerleştirme istemci yuvadan verileri okumak için birden fazla çağrı arasında korunması değerlerine izin verir.</span><span class="sxs-lookup"><span data-stu-id="7d2dd-128">Placing these fields in the state object allows their values to be preserved across multiple calls to read data from the client socket.</span></span>  
  
```vb  
Public Class StateObject  
    Public workSocket As Socket = Nothing  
    Public BufferSize As Integer = 1024  
    Public buffer(BufferSize) As Byte  
    Public sb As New StringBuilder()  
End Class 'StateObject  
```  
  
```csharp  
public class StateObject {  
    public Socket workSocket = null;  
    public const int BufferSize = 1024;  
    public byte[] buffer = new byte[BufferSize];  
    public StringBuilder sb = new StringBuilder();  
}  
```  
  
 <span data-ttu-id="7d2dd-129">Bölümünü `acceptCallback` istemci yuvadan veri alma başlatır yöntemi ilk örneği başlatır `StateObject` sınıfı ve çağrıları <xref:System.Net.Sockets.Socket.BeginReceive%2A> verileri zaman uyumsuz olarak istemci yuvadan okumaya başlamak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="7d2dd-129">The section of the `acceptCallback` method that starts receiving the data from the client socket first initializes an instance of the `StateObject` class and then calls the <xref:System.Net.Sockets.Socket.BeginReceive%2A> method to start reading the data from the client socket asynchronously.</span></span>  
  
 <span data-ttu-id="7d2dd-130">Aşağıdaki örnek eksiksiz gösterir `acceptCallback` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7d2dd-130">The following example shows the complete `acceptCallback` method.</span></span> <span data-ttu-id="7d2dd-131">Bunu olduğunu genel varsaydığını **ManualResetEvent** adlı `allDone,` , `StateObject` sınıfı tanımlanır ve `readCallback` yöntemi adlı bir sınıf içinde tanımlanan `SocketListener`.</span><span class="sxs-lookup"><span data-stu-id="7d2dd-131">It assumes that there is a global **ManualResetEvent** named `allDone,` that the `StateObject` class is defined, and that the `readCallback` method is defined in a class named `SocketListener`.</span></span>  
  
```vb  
Public Shared Sub acceptCallback(ar As IAsyncResult)  
    ' Get the socket that handles the client request.  
    Dim listener As Socket = CType(ar.AsyncState, Socket)  
    Dim handler As Socket = listener.EndAccept(ar)  
  
    ' Signal the main thread to continue.  
    allDone.Set()  
  
    ' Create the state object.  
    Dim state As New StateObject()  
    state.workSocket = handler  
    handler.BeginReceive(state.buffer, 0, state.BufferSize, 0, _  
        AddressOf AsynchronousSocketListener.readCallback, state)  
End Sub 'acceptCallback  
```  
  
```csharp  
public static void acceptCallback(IAsyncResult ar) {  
    // Get the socket that handles the client request.  
    Socket listener = (Socket) ar.AsyncState;  
    Socket handler = listener.EndAccept(ar);  
  
    // Signal the main thread to continue.  
    allDone.Set();  
  
    // Create the state object.  
    StateObject state = new StateObject();  
    state.workSocket = handler;  
    handler.BeginReceive( state.buffer, 0, StateObject.BufferSize, 0,  
        new AsyncCallback(AsynchronousSocketListener.readCallback), state);  
}  
```  
  
 <span data-ttu-id="7d2dd-132">Zaman uyumsuz yuvası sunucusu için uygulanması gereken son yöntemi istemci tarafından gönderilen verileri döndüren okuma geri çağırma yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="7d2dd-132">The final method that needs to be implemented for the asynchronous socket server is the read callback method that returns the data sent by the client.</span></span> <span data-ttu-id="7d2dd-133">Kabul et geri çağırma yöntemi gibi okuma geri çağırma yöntemi olan bir **AsyncCallback** temsilci.</span><span class="sxs-lookup"><span data-stu-id="7d2dd-133">Like the accept callback method, the read callback method is an **AsyncCallback** delegate.</span></span> <span data-ttu-id="7d2dd-134">Bu yöntem, bir veya daha fazla bayt veri arabelleğe istemci yuvadan okur ve daha sonra çağırır **BeginReceive** yeniden istemci tarafından gönderilen verileri kadar yöntemi tamamlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="7d2dd-134">This method reads one or more bytes from the client socket into the data buffer and then calls the **BeginReceive** method again until the data sent by the client is complete.</span></span> <span data-ttu-id="7d2dd-135">İletinin tamamını istemciden okunan sonra dize konsolda görüntülenir ve istemci bağlantısı işleme server yuva kapalı.</span><span class="sxs-lookup"><span data-stu-id="7d2dd-135">Once the entire message has been read from the client, the string is displayed on the console and the server socket handling the connection to the client is closed.</span></span>  
  
 <span data-ttu-id="7d2dd-136">Aşağıdaki örnek uygulayan `readCallback` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7d2dd-136">The following sample implements the `readCallback` method.</span></span> <span data-ttu-id="7d2dd-137">Varsayılmaktadır `StateObject` sınıfı tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="7d2dd-137">It assumes that the `StateObject` class is defined.</span></span>  
  
```vb  
Public Shared Sub readCallback(ar As IAsyncResult)  
    Dim state As StateObject = CType(ar.AsyncState, StateObject)  
    Dim handler As Socket = state.workSocket  
  
    ' Read data from the client socket.   
    Dim read As Integer = handler.EndReceive(ar)  
  
    ' Data was read from the client socket.  
    If read > 0 Then  
        state.sb.Append(Encoding.ASCII.GetString(state.buffer, 0, read))  
        handler.BeginReceive(state.buffer, 0, state.BufferSize, 0, _  
            AddressOf readCallback, state)  
    Else  
        If state.sb.Length > 1 Then  
            ' All the data has been read from the client;  
            ' display it on the console.  
            Dim content As String = state.sb.ToString()  
            Console.WriteLine("Read {0} bytes from socket." + _  
                ControlChars.Cr + " Data : {1}", content.Length, content)  
        End If  
    End If  
End Sub 'readCallback  
```  
  
```csharp  
public static void readCallback(IAsyncResult ar) {  
    StateObject state = (StateObject) ar.AsyncState;  
    Socket handler = state.WorkSocket;  
  
    // Read data from the client socket.  
    int read = handler.EndReceive(ar);  
  
    // Data was read from the client socket.  
    if (read > 0) {  
        state.sb.Append(Encoding.ASCII.GetString(state.buffer,0,read));  
        handler.BeginReceive(state.buffer,0,StateObject.BufferSize, 0,  
            new AsyncCallback(readCallback), state);  
    } else {  
        if (state.sb.Length > 1) {  
            // All the data has been read from the client;  
            // display it on the console.  
            string content = state.sb.ToString();  
            Console.WriteLine("Read {0} bytes from socket.\n Data : {1}",  
               content.Length, content);  
        }  
        handler.Close();  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="7d2dd-138">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7d2dd-138">See Also</span></span>  
 [<span data-ttu-id="7d2dd-139">Zaman Uyumlu Sunucu Yuvası Kullanma</span><span class="sxs-lookup"><span data-stu-id="7d2dd-139">Using a Synchronous Server Socket</span></span>](../../../docs/framework/network-programming/using-a-synchronous-server-socket.md)  
 [<span data-ttu-id="7d2dd-140">Zaman Uyumsuz Sunucu Yuvası Örneği</span><span class="sxs-lookup"><span data-stu-id="7d2dd-140">Asynchronous Server Socket Example</span></span>](../../../docs/framework/network-programming/asynchronous-server-socket-example.md)  
 [<span data-ttu-id="7d2dd-141">İş parçacığı oluşturma</span><span class="sxs-lookup"><span data-stu-id="7d2dd-141">Threading</span></span>](../../../docs/standard/threading/index.md)  
 [<span data-ttu-id="7d2dd-142">Yuvalarla Dinleme</span><span class="sxs-lookup"><span data-stu-id="7d2dd-142">Listening with Sockets</span></span>](../../../docs/framework/network-programming/listening-with-sockets.md)
