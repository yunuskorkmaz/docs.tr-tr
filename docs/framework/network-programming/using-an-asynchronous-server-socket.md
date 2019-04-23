---
title: Zaman Uyumsuz Sunucu Yuvası Kullanma
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
ms.openlocfilehash: 32a2a99d5f71cb500dca467433f138a893d01e5b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59119931"
---
# <a name="using-an-asynchronous-server-socket"></a><span data-ttu-id="03117-102">Zaman Uyumsuz Sunucu Yuvası Kullanma</span><span class="sxs-lookup"><span data-stu-id="03117-102">Using an Asynchronous Server Socket</span></span>
<span data-ttu-id="03117-103">Zaman uyumsuz sunucu yuvası ağ hizmeti isteklerini işlemek için .NET Framework zaman uyumsuz programlama modeli kullanımı.</span><span class="sxs-lookup"><span data-stu-id="03117-103">Asynchronous server sockets use the .NET Framework asynchronous programming model to process network service requests.</span></span> <span data-ttu-id="03117-104"><xref:System.Net.Sockets.Socket> Sınıfı aşağıdaki standart .NET Framework zaman uyumsuz adlandırma deseni; Örneğin, zaman uyumlu <xref:System.Net.Sockets.Socket.Accept%2A> yöntemi karşılık gelen için zaman uyumsuz <xref:System.Net.Sockets.Socket.BeginAccept%2A> ve <xref:System.Net.Sockets.Socket.EndAccept%2A> yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="03117-104">The <xref:System.Net.Sockets.Socket> class follows the standard .NET Framework asynchronous naming pattern; for example, the synchronous <xref:System.Net.Sockets.Socket.Accept%2A> method corresponds to the asynchronous <xref:System.Net.Sockets.Socket.BeginAccept%2A> and <xref:System.Net.Sockets.Socket.EndAccept%2A> methods.</span></span>  
  
 <span data-ttu-id="03117-105">Zaman uyumsuz sunucu yuvası veri alma sonlandırmak için ağ bağlantı isteklerini işlemek ve ağdan veri almaya başlamak için bir geri çağırma yöntemini ve bir geri çağırma yöntemi gelen bağlantı istekleri kabul başlamak için bir yöntem gerektirir.</span><span class="sxs-lookup"><span data-stu-id="03117-105">An asynchronous server socket requires a method to begin accepting connection requests from the network, a callback method to handle the connection requests and begin receiving data from the network, and a callback method to end receiving the data.</span></span> <span data-ttu-id="03117-106">Tüm bu yöntemleri ele alınmıştır Bu bölümde daha fazla.</span><span class="sxs-lookup"><span data-stu-id="03117-106">All these methods are discussed further in this section.</span></span>  
  
 <span data-ttu-id="03117-107">Yöntem ağ üzerinden bağlantı isteklerini kabul eden başlamak için aşağıdaki örnekte `StartListening` başlatır **yuva** ve ardından **BeginAccept** yeni kabul başlatmak için yöntemi bağlantılar.</span><span class="sxs-lookup"><span data-stu-id="03117-107">In the following example, to begin accepting connection requests from the network, the method `StartListening` initializes the **Socket** and then uses the **BeginAccept** method to start accepting new connections.</span></span> <span data-ttu-id="03117-108">Kabul et geri çağırma yöntemi, yuva yeni bir bağlantı isteği alındığında çağrılır.</span><span class="sxs-lookup"><span data-stu-id="03117-108">The accept callback method is called when a new connection request is received on the socket.</span></span> <span data-ttu-id="03117-109">Dağıtımından sorumlu **yuva** bağlantı ve, teslim etme işleyecek örneği **yuva** isteği işleyen iş parçacığına kapalı.</span><span class="sxs-lookup"><span data-stu-id="03117-109">It is responsible for getting the **Socket** instance that will handle the connection and handing that **Socket** off to the thread that will process the request.</span></span> <span data-ttu-id="03117-110">Kabul et geri çağırma yöntemini uygulayan <xref:System.AsyncCallback> temsilci; void döndürür ve türünde tek bir parametre alan <xref:System.IAsyncResult>.</span><span class="sxs-lookup"><span data-stu-id="03117-110">The accept callback method implements the <xref:System.AsyncCallback> delegate; it returns a void and takes a single parameter of type <xref:System.IAsyncResult>.</span></span> <span data-ttu-id="03117-111">Aşağıdaki örnek, bir accept geri çağırma yöntemini kabuktur.</span><span class="sxs-lookup"><span data-stu-id="03117-111">The following example is the shell of an accept callback method.</span></span>  
  
```vb  
Sub AcceptCallback(ar As IAsyncResult)  
    ' Add the callback code here.  
End Sub 'AcceptCallback  
```  
  
```csharp  
void AcceptCallback(IAsyncResult ar)
{  
    // Add the callback code here.  
}  
```  
  
 <span data-ttu-id="03117-112">**BeginAccept** yöntemi, iki parametre alan bir **AsyncCallback** accept geri çağırma yöntemini ve durum bilgilerini geri çağırma yöntemine geçirmek için kullanılan nesneyi işaret eden bir temsilci.</span><span class="sxs-lookup"><span data-stu-id="03117-112">The **BeginAccept** method takes two parameters, an **AsyncCallback** delegate that points to the accept callback method and an object that is used to pass state information to the callback method.</span></span> <span data-ttu-id="03117-113">Aşağıdaki örnekte dinleme **yuva** geri çağırma yöntemine geçirilen *durumu* parametresi.</span><span class="sxs-lookup"><span data-stu-id="03117-113">In the following example, the listening **Socket** is passed to the callback method through the *state* parameter.</span></span> <span data-ttu-id="03117-114">Bu örnekte bir **AsyncCallback** temsilci ve ağ üzerinden bağlantı kabul başlatır.</span><span class="sxs-lookup"><span data-stu-id="03117-114">This example creates an **AsyncCallback** delegate and starts accepting connections from the network.</span></span>  
  
```vb  
listener.BeginAccept( _  
    New AsyncCallback(SocketListener.AcceptCallback),_  
    listener)  
```  
  
```csharp  
listener.BeginAccept(new AsyncCallback(SocketListener.AcceptCallback), listener);  
```  
  
 <span data-ttu-id="03117-115">Zaman uyumsuz yuva gelen bağlantıları işlemek için sistem iş parçacığı havuzu iş parçacıkları kullanın.</span><span class="sxs-lookup"><span data-stu-id="03117-115">Asynchronous sockets use threads from the system thread pool to process incoming connections.</span></span> <span data-ttu-id="03117-116">Bir iş parçacığı bağlantıları kabul etmek için sorumlu, başka bir iş parçacığı her bir gelen bağlantı işlemek için kullanılır ve başka bir iş parçacığı, veri bağlantısı almak için sorumludur.</span><span class="sxs-lookup"><span data-stu-id="03117-116">One thread is responsible for accepting connections, another thread is used to handle each incoming connection, and another thread is responsible for receiving data from the connection.</span></span> <span data-ttu-id="03117-117">Bunlar iş parçacığı havuzu tarafından atanmış iş parçacığı bağlı olarak aynı iş parçacığı olabilir.</span><span class="sxs-lookup"><span data-stu-id="03117-117">These could be the same thread, depending on which thread is assigned by the thread pool.</span></span> <span data-ttu-id="03117-118">Aşağıdaki örnekte, <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> sınıf ana iş parçacığının yürütülmesini askıya alır ve yürütme devam edebilirsiniz, bildirir.</span><span class="sxs-lookup"><span data-stu-id="03117-118">In the following example, the <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> class suspends execution of the main thread and signals when execution can continue.</span></span>  
  
 <span data-ttu-id="03117-119">Aşağıdaki örnek, yerel bilgisayarda uyumsuz bir TCP/IP yuva oluşturur ve bağlantıları kabul başlar zaman uyumsuz bir yöntemi gösterir.</span><span class="sxs-lookup"><span data-stu-id="03117-119">The following example shows an asynchronous method that creates an asynchronous TCP/IP socket on the local computer and begins accepting connections.</span></span> <span data-ttu-id="03117-120">Olduğunu genel varsayar **ManualResetEvent** adlı `allDone`, yöntem adlı bir sınıf üyesi olduğunu `SocketListener`, ve bir geri çağırma yöntemi adlı `AcceptCallback` tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="03117-120">It assumes that there is a global **ManualResetEvent** named `allDone`, that the method is a member of a class named `SocketListener`, and that a callback method named `AcceptCallback` is defined.</span></span>  
  
```vb  
Public Sub StartListening()  
    Dim ipHostInfo As IPHostEntry = Dns.Resolve(Dns.GetHostName())  
    Dim localEP = New IPEndPoint(ipHostInfo.AddressList(0), 11000)  
  
    Console.WriteLine($"Local address and port : {localEP.ToString()}")  
  
    Dim listener As New Socket(localEP.Address.AddressFamily, _  
       SocketType.Stream, ProtocolType.Tcp)  
  
    Try  
        listener.Bind(localEP)  
        listener.Listen(10)  
  
        While True  
            allDone.Reset()  
  
            Console.WriteLine("Waiting for a connection...")  
            listener.BeginAccept(New _  
                AsyncCallback(SocketListener.AcceptCallback), _  
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
public void StartListening()
{  
    IPHostEntry ipHostInfo = Dns.Resolve(Dns.GetHostName());  
    IPEndPoint localEP = new IPEndPoint(ipHostInfo.AddressList[0], 11000);  
  
    Console.WriteLine($"Local address and port : {localEP.ToString()}");  
  
    Socket listener = new Socket(localEP.Address.AddressFamily, SocketType.Stream, ProtocolType.Tcp);  
  
    try 
    {  
        listener.Bind(localEP);  
        listener.Listen(10);  
  
        while (true)
        {  
            allDone.Reset();  
  
            Console.WriteLine("Waiting for a connection...");  
            listener.BeginAccept(new AsyncCallback(SocketListener.AcceptCallback), listener);  
  
            allDone.WaitOne();  
        }  
    }
    catch (Exception e)
    {  
        Console.WriteLine(e.ToString());  
    }  
  
    Console.WriteLine("Closing the listener...");  
}  
```  
  
 <span data-ttu-id="03117-121">Kabul et geri çağırma yöntemi (`AcceptCallback` önceki örnekte) istemciden okunan veri işleme, istemci ile bağlantı kurma ve zaman uyumsuz başlatılıyor devam etmek için ana uygulama iş parçacığı sinyal için sorumludur.</span><span class="sxs-lookup"><span data-stu-id="03117-121">The accept callback method (`AcceptCallback` in the preceding example) is responsible for signaling the main application thread to continue processing, establishing the connection with the client, and starting the asynchronous read of data from the client.</span></span> <span data-ttu-id="03117-122">Aşağıdaki örnek uygulaması ilk parçasıdır `AcceptCallback` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="03117-122">The following example is the first part of an implementation of the `AcceptCallback` method.</span></span> <span data-ttu-id="03117-123">Bu bölümde yönteminin ana uygulama iş parçacığının işlemeye devam eder ve istemci bağlantı kurar.</span><span class="sxs-lookup"><span data-stu-id="03117-123">This section of the method signals the main application thread to continue processing and establishes the connection to the client.</span></span> <span data-ttu-id="03117-124">Genel bir varsayar **ManualResetEvent** adlı `allDone`.</span><span class="sxs-lookup"><span data-stu-id="03117-124">It assumes a global **ManualResetEvent** named `allDone`.</span></span>  
  
```vb  
Public Sub AcceptCallback(ar As IAsyncResult)  
    allDone.Set()  
  
    Dim listener As Socket = CType(ar.AsyncState, Socket)  
    Dim handler As Socket = listener.EndAccept(ar)  
  
    ' Additional code to read data goes here.  
End Sub 'AcceptCallback  
```  
  
```csharp  
public void AcceptCallback(IAsyncResult ar) 
{  
    allDone.Set();  
  
    Socket listener = (Socket) ar.AsyncState;  
    Socket handler = listener.EndAccept(ar);  
  
    // Additional code to read data goes here.    
}  
```  
  
 <span data-ttu-id="03117-125">Bir istemci yuvadan verileri okuma değerleri arasında zaman uyumsuz çağrıları geçiren bir durum nesnesi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="03117-125">Reading data from a client socket requires a state object that passes values between asynchronous calls.</span></span> <span data-ttu-id="03117-126">Aşağıdaki örnek, bir dize uzak istemciden almak için bir durum nesnesi uygular.</span><span class="sxs-lookup"><span data-stu-id="03117-126">The following example implements a state object for receiving a string from the remote client.</span></span> <span data-ttu-id="03117-127">İstemci yuvası, verileri almak için bir veri arabelleği için alanları içerir ve bir <xref:System.Text.StringBuilder> istemci tarafından gönderilen veri dizesi oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="03117-127">It contains fields for the client socket, a data buffer for receiving data, and a <xref:System.Text.StringBuilder> for creating the data string sent by the client.</span></span> <span data-ttu-id="03117-128">Bu alanlar durumu nesnesinde yerleştirme istemci yuvadan verileri okumak için birden çok çağrı arasında saklanması değerleri verir.</span><span class="sxs-lookup"><span data-stu-id="03117-128">Placing these fields in the state object allows their values to be preserved across multiple calls to read data from the client socket.</span></span>  
  
```vb  
Public Class StateObject  
    Public workSocket As Socket = Nothing  
    Public BufferSize As Integer = 1024  
    Public buffer(BufferSize) As Byte  
    Public sb As New StringBuilder()  
End Class 'StateObject  
```  
  
```csharp  
public class StateObject 
{  
    public Socket workSocket = null;  
    public const int BufferSize = 1024;  
    public byte[] buffer = new byte[BufferSize];  
    public StringBuilder sb = new StringBuilder();  
}  
```  
  
 <span data-ttu-id="03117-129">Bölümünü `AcceptCallback` istemci yuvadan veri almaya başlar yöntemi ilk kez bir örneğini başlatır `StateObject` sınıfı ve çağrıları <xref:System.Net.Sockets.Socket.BeginReceive%2A> verileri zaman uyumsuz olarak istemci yuvadan okumaya başlamak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="03117-129">The section of the `AcceptCallback` method that starts receiving the data from the client socket first initializes an instance of the `StateObject` class and then calls the <xref:System.Net.Sockets.Socket.BeginReceive%2A> method to start reading the data from the client socket asynchronously.</span></span>  
  
 <span data-ttu-id="03117-130">Aşağıdaki örnek, tam gösterir `AcceptCallback` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="03117-130">The following example shows the complete `AcceptCallback` method.</span></span> <span data-ttu-id="03117-131">Olduğunu genel varsayar **ManualResetEvent** adlı `allDone,` , `StateObject` sınıfı tanımlanır ve `ReadCallback` yöntemi adlı bir sınıfta tanımlanan `SocketListener`.</span><span class="sxs-lookup"><span data-stu-id="03117-131">It assumes that there is a global **ManualResetEvent** named `allDone,` that the `StateObject` class is defined, and that the `ReadCallback` method is defined in a class named `SocketListener`.</span></span>  
  
```vb  
Public Shared Sub AcceptCallback(ar As IAsyncResult)  
    ' Get the socket that handles the client request.  
    Dim listener As Socket = CType(ar.AsyncState, Socket)  
    Dim handler As Socket = listener.EndAccept(ar)  
  
    ' Signal the main thread to continue.  
    allDone.Set()  
  
    ' Create the state object.  
    Dim state As New StateObject()  
    state.workSocket = handler  
    handler.BeginReceive(state.buffer, 0, state.BufferSize, 0, _  
        AddressOf AsynchronousSocketListener.ReadCallback, state)  
End Sub 'AcceptCallback  
```  
  
```csharp  
public static void AcceptCallback(IAsyncResult ar)
{  
    // Get the socket that handles the client request.  
    Socket listener = (Socket) ar.AsyncState;  
    Socket handler = listener.EndAccept(ar);  
  
    // Signal the main thread to continue.  
    allDone.Set();  
  
    // Create the state object.  
    StateObject state = new StateObject();  
    state.workSocket = handler;  
    handler.BeginReceive(state.buffer, 0, StateObject.BufferSize, 0,  
        new AsyncCallback(AsynchronousSocketListener.ReadCallback), state);  
}  
```  
  
 <span data-ttu-id="03117-132">Zaman uyumsuz yuvası sunucusu için uygulanması gereken son yöntemi istemci tarafından gönderilen verileri döndüren okuma geri çağırma yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="03117-132">The final method that needs to be implemented for the asynchronous socket server is the read callback method that returns the data sent by the client.</span></span> <span data-ttu-id="03117-133">Kabul et geri çağırma yöntemine benzer okuma geri çağırma yöntemi olan bir **AsyncCallback** temsilci.</span><span class="sxs-lookup"><span data-stu-id="03117-133">Like the accept callback method, the read callback method is an **AsyncCallback** delegate.</span></span> <span data-ttu-id="03117-134">Bu yöntem, bir veya daha fazla bayt veri arabelleğe istemci yuvadan okur ve ardından çağırır **BeginReceive** yeniden istemci tarafından gönderilen verilerin kadar yöntemi tamamlandığında.</span><span class="sxs-lookup"><span data-stu-id="03117-134">This method reads one or more bytes from the client socket into the data buffer and then calls the **BeginReceive** method again until the data sent by the client is complete.</span></span> <span data-ttu-id="03117-135">Tüm ileti istemciden okunan sonra dize konsolda görüntülenir ve istemci bağlantısı işleme sunucu yuvası kapatılır.</span><span class="sxs-lookup"><span data-stu-id="03117-135">Once the entire message has been read from the client, the string is displayed on the console and the server socket handling the connection to the client is closed.</span></span>  
  
 <span data-ttu-id="03117-136">Aşağıdaki örnek uygular `ReadCallback` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="03117-136">The following sample implements the `ReadCallback` method.</span></span> <span data-ttu-id="03117-137">Olduğunu varsayar `StateObject` sınıfı tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="03117-137">It assumes that the `StateObject` class is defined.</span></span>  
  
```vb  
Public Shared Sub ReadCallback(ar As IAsyncResult)  
    Dim state As StateObject = CType(ar.AsyncState, StateObject)  
    Dim handler As Socket = state.workSocket  
  
    ' Read data from the client socket.   
    Dim read As Integer = handler.EndReceive(ar)  
  
    ' Data was read from the client socket.  
    If read > 0 Then  
        state.sb.Append(Encoding.ASCII.GetString(state.buffer, 0, read))  
        handler.BeginReceive(state.buffer, 0, state.BufferSize, 0, _  
            AddressOf ReadCallback, state)  
    Else  
        If state.sb.Length > 1 Then  
            ' All the data has been read from the client;  
            ' display it on the console.  
            Dim content As String = state.sb.ToString()  
            Console.WriteLine($"Read {content.Length} bytes from socket. {ControlChars.Cr} Data : {content}")  
        End If  
    End If  
End Sub 'ReadCallback  
```  
  
```csharp  
public static void ReadCallback(IAsyncResult ar)
{  
    StateObject state = (StateObject) ar.AsyncState;  
    Socket handler = state.WorkSocket;  
  
    // Read data from the client socket.  
    int read = handler.EndReceive(ar);  
  
    // Data was read from the client socket.  
    if (read > 0)
    {  
        state.sb.Append(Encoding.ASCII.GetString(state.buffer,0,read));  
        handler.BeginReceive(state.buffer, 0, StateObject.BufferSize, 0,  
            new AsyncCallback(ReadCallback), state);  
    } 
    else 
    {  
        if (state.sb.Length > 1) 
        {  
            // All the data has been read from the client;  
            // display it on the console.  
            string content = state.sb.ToString();  
            Console.WriteLine($"Read {content.Length} bytes from socket.\n Data : {content}");
        }  
        handler.Close();  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="03117-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="03117-138">See also</span></span>

- [<span data-ttu-id="03117-139">Zaman Uyumlu Sunucu Yuvası Kullanma</span><span class="sxs-lookup"><span data-stu-id="03117-139">Using a Synchronous Server Socket</span></span>](../../../docs/framework/network-programming/using-a-synchronous-server-socket.md)
- [<span data-ttu-id="03117-140">Zaman Uyumsuz Sunucu Yuvası Örneği</span><span class="sxs-lookup"><span data-stu-id="03117-140">Asynchronous Server Socket Example</span></span>](../../../docs/framework/network-programming/asynchronous-server-socket-example.md)
- [<span data-ttu-id="03117-141">İş parçacığı oluşturma</span><span class="sxs-lookup"><span data-stu-id="03117-141">Threading</span></span>](../../../docs/standard/threading/index.md)
- [<span data-ttu-id="03117-142">Yuvalarla Dinleme</span><span class="sxs-lookup"><span data-stu-id="03117-142">Listening with Sockets</span></span>](../../../docs/framework/network-programming/listening-with-sockets.md)
