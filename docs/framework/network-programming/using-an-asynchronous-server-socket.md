---
title: Zaman Uyumsuz Sunucu Yuvası Kullanma
description: Bu örnekte bir zaman uyumsuz sunucu yuvası gösterilmektedir. Yuva sınıfı, ağ hizmeti isteklerini işlemek için zaman uyumsuz programlama .NET Framework kullanır.
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
ms.openlocfilehash: 8b85afb3ffdf69973eff37ccbb067b470ed44e3a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502034"
---
# <a name="using-an-asynchronous-server-socket"></a><span data-ttu-id="7583a-104">Zaman Uyumsuz Sunucu Yuvası Kullanma</span><span class="sxs-lookup"><span data-stu-id="7583a-104">Using an Asynchronous Server Socket</span></span>
<span data-ttu-id="7583a-105">Zaman uyumsuz sunucu yuvaları, ağ hizmeti isteklerini işlemek için .NET Framework zaman uyumsuz programlama modeli kullanır.</span><span class="sxs-lookup"><span data-stu-id="7583a-105">Asynchronous server sockets use the .NET Framework asynchronous programming model to process network service requests.</span></span> <span data-ttu-id="7583a-106"><xref:System.Net.Sockets.Socket>Sınıfı standart .NET Framework zaman uyumsuz adlandırma düzenine uyar; Örneğin, zaman uyumlu <xref:System.Net.Sockets.Socket.Accept%2A> yöntemi zaman uyumsuz ve yöntemlere karşılık gelir <xref:System.Net.Sockets.Socket.BeginAccept%2A> <xref:System.Net.Sockets.Socket.EndAccept%2A> .</span><span class="sxs-lookup"><span data-stu-id="7583a-106">The <xref:System.Net.Sockets.Socket> class follows the standard .NET Framework asynchronous naming pattern; for example, the synchronous <xref:System.Net.Sockets.Socket.Accept%2A> method corresponds to the asynchronous <xref:System.Net.Sockets.Socket.BeginAccept%2A> and <xref:System.Net.Sockets.Socket.EndAccept%2A> methods.</span></span>  
  
 <span data-ttu-id="7583a-107">Zaman uyumsuz sunucu yuvası, ağdan gelen bağlantı isteklerini kabul etmeye başlamak için bir yöntem, bağlantı isteklerini işlemek için bir geri çağırma yöntemi ve ağdan veri almaya başlamak için bir geri çağırma yöntemi ve verileri almayı bitirmek için bir geri arama yöntemi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="7583a-107">An asynchronous server socket requires a method to begin accepting connection requests from the network, a callback method to handle the connection requests and begin receiving data from the network, and a callback method to end receiving the data.</span></span> <span data-ttu-id="7583a-108">Tüm bu yöntemler, bu bölümde daha ayrıntılı bir şekilde ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="7583a-108">All these methods are discussed further in this section.</span></span>  
  
 <span data-ttu-id="7583a-109">Aşağıdaki örnekte, ağdan gelen bağlantı isteklerini kabul etmeye başlamak için, yöntemi `StartListening` **yuvayı** başlatır ve ardından yeni bağlantıları kabul etmeye başlamak için **BeginAccept** yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="7583a-109">In the following example, to begin accepting connection requests from the network, the method `StartListening` initializes the **Socket** and then uses the **BeginAccept** method to start accepting new connections.</span></span> <span data-ttu-id="7583a-110">Yuva üzerinde yeni bir bağlantı isteği alındığında geri aramayı kabul etme yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="7583a-110">The accept callback method is called when a new connection request is received on the socket.</span></span> <span data-ttu-id="7583a-111">Bağlantıyı işleyecek ve bu **yuvayı** isteği işleyecek iş parçacığına teslim edecek olan **yuva** örneğinin alınması sorumludur.</span><span class="sxs-lookup"><span data-stu-id="7583a-111">It is responsible for getting the **Socket** instance that will handle the connection and handing that **Socket** off to the thread that will process the request.</span></span> <span data-ttu-id="7583a-112">Accept geri çağırma yöntemi temsilciyi uygular <xref:System.AsyncCallback> ; bir void döndürür ve türünde tek bir parametre alır <xref:System.IAsyncResult> .</span><span class="sxs-lookup"><span data-stu-id="7583a-112">The accept callback method implements the <xref:System.AsyncCallback> delegate; it returns a void and takes a single parameter of type <xref:System.IAsyncResult>.</span></span> <span data-ttu-id="7583a-113">Aşağıdaki örnek, Accept geri çağırma yönteminin kabuğudur.</span><span class="sxs-lookup"><span data-stu-id="7583a-113">The following example is the shell of an accept callback method.</span></span>  
  
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
  
 <span data-ttu-id="7583a-114">**BeginAccept** yöntemi iki parametre alır. geri çağırma yöntemini işaret eden bir **AsyncCallback** temsilcisi ve geri çağırma yöntemine durum bilgilerini geçirmek için kullanılan bir nesne.</span><span class="sxs-lookup"><span data-stu-id="7583a-114">The **BeginAccept** method takes two parameters, an **AsyncCallback** delegate that points to the accept callback method and an object that is used to pass state information to the callback method.</span></span> <span data-ttu-id="7583a-115">Aşağıdaki örnekte, dinleme **yuvası** , *durum* parametresi aracılığıyla geri çağırma yöntemine geçirilir.</span><span class="sxs-lookup"><span data-stu-id="7583a-115">In the following example, the listening **Socket** is passed to the callback method through the *state* parameter.</span></span> <span data-ttu-id="7583a-116">Bu örnek, bir **AsyncCallback** temsilcisi oluşturur ve ağdan bağlantıları kabul etmeye başlar.</span><span class="sxs-lookup"><span data-stu-id="7583a-116">This example creates an **AsyncCallback** delegate and starts accepting connections from the network.</span></span>  
  
```vb  
listener.BeginAccept( _  
    New AsyncCallback(SocketListener.AcceptCallback),_  
    listener)  
```  
  
```csharp  
listener.BeginAccept(new AsyncCallback(SocketListener.AcceptCallback), listener);  
```  
  
 <span data-ttu-id="7583a-117">Zaman uyumsuz yuvalar, gelen bağlantıları işlemek için sistem iş parçacığı havuzundan iş parçacıklarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="7583a-117">Asynchronous sockets use threads from the system thread pool to process incoming connections.</span></span> <span data-ttu-id="7583a-118">Bir iş parçacığı bağlantı kabul edilmeden sorumludur, her gelen bağlantıyı işlemek için başka bir iş parçacığı kullanılır ve bağlantıdan veri almaktan başka bir iş parçacığı sorumludur.</span><span class="sxs-lookup"><span data-stu-id="7583a-118">One thread is responsible for accepting connections, another thread is used to handle each incoming connection, and another thread is responsible for receiving data from the connection.</span></span> <span data-ttu-id="7583a-119">Bunlar, iş parçacığı havuzunun hangi iş parçacığına atandığına bağlı olarak aynı iş parçacığı olabilir.</span><span class="sxs-lookup"><span data-stu-id="7583a-119">These could be the same thread, depending on which thread is assigned by the thread pool.</span></span> <span data-ttu-id="7583a-120">Aşağıdaki örnekte, <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> sınıfı ana iş parçacığının yürütülmesini ve yürütme devam edebildikleri sinyalleri askıya alır.</span><span class="sxs-lookup"><span data-stu-id="7583a-120">In the following example, the <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> class suspends execution of the main thread and signals when execution can continue.</span></span>  
  
 <span data-ttu-id="7583a-121">Aşağıdaki örnek, yerel bilgisayarda zaman uyumsuz TCP/IP yuvası oluşturan ve bağlantıları kabul etmeye başlayan bir zaman uyumsuz yöntemi gösterir.</span><span class="sxs-lookup"><span data-stu-id="7583a-121">The following example shows an asynchronous method that creates an asynchronous TCP/IP socket on the local computer and begins accepting connections.</span></span> <span data-ttu-id="7583a-122">Adlı bir genel **ManualResetEvent** olduğunu, yöntemin adlı bir `allDone` sınıfın üyesi olduğunu `SocketListener` ve adlı bir geri çağırma yönteminin tanımlı olduğunu varsayar `AcceptCallback` .</span><span class="sxs-lookup"><span data-stu-id="7583a-122">It assumes that there is a global **ManualResetEvent** named `allDone`, that the method is a member of a class named `SocketListener`, and that a callback method named `AcceptCallback` is defined.</span></span>  
  
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
  
 <span data-ttu-id="7583a-123">Geri aramayı kabul etme yöntemi ( `AcceptCallback` Önceki örnekte), ana uygulama iş parçacığının işleme devam etmesi, istemciyle bağlantı kurulması ve istemciden gelen verilerin zaman uyumsuz okumasından başlamasını sağlamaktan sorumludur.</span><span class="sxs-lookup"><span data-stu-id="7583a-123">The accept callback method (`AcceptCallback` in the preceding example) is responsible for signaling the main application thread to continue processing, establishing the connection with the client, and starting the asynchronous read of data from the client.</span></span> <span data-ttu-id="7583a-124">Aşağıdaki örnek, yöntemi uygulamasının ilk bölümüdür `AcceptCallback` .</span><span class="sxs-lookup"><span data-stu-id="7583a-124">The following example is the first part of an implementation of the `AcceptCallback` method.</span></span> <span data-ttu-id="7583a-125">Yönteminin bu bölümü, işleme devam etmek için ana uygulama iş parçacığını bildirir ve istemciye bağlantı kurar.</span><span class="sxs-lookup"><span data-stu-id="7583a-125">This section of the method signals the main application thread to continue processing and establishes the connection to the client.</span></span> <span data-ttu-id="7583a-126">Adında genel bir **ManualResetEvent** olduğunu varsayar `allDone` .</span><span class="sxs-lookup"><span data-stu-id="7583a-126">It assumes a global **ManualResetEvent** named `allDone`.</span></span>  
  
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
  
 <span data-ttu-id="7583a-127">İstemci yuvalarından veri okuma, zaman uyumsuz çağrılar arasında değer geçiren bir durum nesnesi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="7583a-127">Reading data from a client socket requires a state object that passes values between asynchronous calls.</span></span> <span data-ttu-id="7583a-128">Aşağıdaki örnek, uzak istemciden bir dize almak için bir durum nesnesi uygular.</span><span class="sxs-lookup"><span data-stu-id="7583a-128">The following example implements a state object for receiving a string from the remote client.</span></span> <span data-ttu-id="7583a-129">İstemci yuvasının alanlarını, veri almaya yönelik bir veri arabelleğini ve <xref:System.Text.StringBuilder> istemci tarafından gönderilen veri dizesini oluşturmak için bir içerir.</span><span class="sxs-lookup"><span data-stu-id="7583a-129">It contains fields for the client socket, a data buffer for receiving data, and a <xref:System.Text.StringBuilder> for creating the data string sent by the client.</span></span> <span data-ttu-id="7583a-130">Bu alanların durum nesnesine yerleştirilmesi, değerlerinin istemci yuvasında verileri okumak için birden çok çağrıda saklanması sağlar.</span><span class="sxs-lookup"><span data-stu-id="7583a-130">Placing these fields in the state object allows their values to be preserved across multiple calls to read data from the client socket.</span></span>  
  
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
  
 <span data-ttu-id="7583a-131">İlk olarak, `AcceptCallback` istemci yuvasından verileri almaya başlayan yönteminin bölümü, sınıfının bir örneğini başlatır `StateObject` ve ardından, <xref:System.Net.Sockets.Socket.BeginReceive%2A> istemci yuvasından zaman uyumsuz olarak veri okumaya başlamak için yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="7583a-131">The section of the `AcceptCallback` method that starts receiving the data from the client socket first initializes an instance of the `StateObject` class and then calls the <xref:System.Net.Sockets.Socket.BeginReceive%2A> method to start reading the data from the client socket asynchronously.</span></span>  
  
 <span data-ttu-id="7583a-132">Aşağıdaki örnek, tüm yöntemi gösterir `AcceptCallback` .</span><span class="sxs-lookup"><span data-stu-id="7583a-132">The following example shows the complete `AcceptCallback` method.</span></span> <span data-ttu-id="7583a-133">**ManualResetEvent** `allDone,` `StateObject` Sınıfın tanımlandığını ve `ReadCallback` yönteminin adlı bir sınıfta tanımlandığını belirten küresel bir ManualResetEvent olduğunu varsayar `SocketListener` .</span><span class="sxs-lookup"><span data-stu-id="7583a-133">It assumes that there is a global **ManualResetEvent** named `allDone,` that the `StateObject` class is defined, and that the `ReadCallback` method is defined in a class named `SocketListener`.</span></span>  
  
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
  
 <span data-ttu-id="7583a-134">Zaman uyumsuz yuva sunucusu için uygulanması gereken son yöntem, istemci tarafından gönderilen verileri döndüren okuma geri çağırma yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="7583a-134">The final method that needs to be implemented for the asynchronous socket server is the read callback method that returns the data sent by the client.</span></span> <span data-ttu-id="7583a-135">Geri aramayı kabul et yöntemi gibi Read callback yöntemi bir **AsyncCallback** temsilcisidir.</span><span class="sxs-lookup"><span data-stu-id="7583a-135">Like the accept callback method, the read callback method is an **AsyncCallback** delegate.</span></span> <span data-ttu-id="7583a-136">Bu yöntem, istemci yuvasından veri arabelleğine bir veya daha fazla bayt okur ve ardından istemci tarafından gönderilen veriler tamamlanana kadar **BeginReceive** metodunu yeniden çağırır.</span><span class="sxs-lookup"><span data-stu-id="7583a-136">This method reads one or more bytes from the client socket into the data buffer and then calls the **BeginReceive** method again until the data sent by the client is complete.</span></span> <span data-ttu-id="7583a-137">Tüm ileti istemciden okunduktan sonra, dize konsolda görüntülenir ve istemciyle bağlantıyı işleyen sunucu yuvası kapalıdır.</span><span class="sxs-lookup"><span data-stu-id="7583a-137">Once the entire message has been read from the client, the string is displayed on the console and the server socket handling the connection to the client is closed.</span></span>  
  
 <span data-ttu-id="7583a-138">Aşağıdaki örnek `ReadCallback` yöntemini uygular.</span><span class="sxs-lookup"><span data-stu-id="7583a-138">The following sample implements the `ReadCallback` method.</span></span> <span data-ttu-id="7583a-139">`StateObject`Sınıfın tanımlandığını varsayar.</span><span class="sxs-lookup"><span data-stu-id="7583a-139">It assumes that the `StateObject` class is defined.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7583a-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7583a-140">See also</span></span>

- [<span data-ttu-id="7583a-141">Zaman Uyumlu Sunucu Yuvası Kullanma</span><span class="sxs-lookup"><span data-stu-id="7583a-141">Using a Synchronous Server Socket</span></span>](using-a-synchronous-server-socket.md)
- [<span data-ttu-id="7583a-142">Zaman Uyumsuz Sunucu Yuvası Örneği</span><span class="sxs-lookup"><span data-stu-id="7583a-142">Asynchronous Server Socket Example</span></span>](asynchronous-server-socket-example.md)
- [<span data-ttu-id="7583a-143">İş Parçacığı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="7583a-143">Threading</span></span>](../../standard/threading/index.md)
- [<span data-ttu-id="7583a-144">Yuvalarla Dinleme</span><span class="sxs-lookup"><span data-stu-id="7583a-144">Listening with Sockets</span></span>](listening-with-sockets.md)
