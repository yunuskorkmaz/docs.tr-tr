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
ms.openlocfilehash: 58c9e0846e09774d8c97089016086ecddd2d17ee
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938406"
---
# <a name="using-an-asynchronous-server-socket"></a>Zaman Uyumsuz Sunucu Yuvası Kullanma
Zaman uyumsuz sunucu yuvaları, ağ hizmeti isteklerini işlemek için .NET Framework zaman uyumsuz programlama modeli kullanır. Sınıfı standart .NET Framework zaman uyumsuz adlandırma düzenine uyar; Örneğin, zaman uyumlu <xref:System.Net.Sockets.Socket.Accept%2A> yöntemi zaman uyumsuz <xref:System.Net.Sockets.Socket.BeginAccept%2A> ve <xref:System.Net.Sockets.Socket.EndAccept%2A> yöntemlere karşılık gelir. <xref:System.Net.Sockets.Socket>  
  
 Zaman uyumsuz sunucu yuvası, ağdan gelen bağlantı isteklerini kabul etmeye başlamak için bir yöntem, bağlantı isteklerini işlemek için bir geri çağırma yöntemi ve ağdan veri almaya başlamak için bir geri çağırma yöntemi ve verileri almayı bitirmek için bir geri arama yöntemi gerektirir. Tüm bu yöntemler, bu bölümde daha ayrıntılı bir şekilde ele alınmıştır.  
  
 Aşağıdaki örnekte, ağdan gelen bağlantı isteklerini kabul etmeye başlamak için, yöntemi `StartListening` **yuvayı** başlatır ve ardından yeni bağlantıları kabul etmeye başlamak için **BeginAccept** yöntemini kullanır. Yuva üzerinde yeni bir bağlantı isteği alındığında geri aramayı kabul etme yöntemi çağrılır. Bağlantıyı işleyecek ve bu **yuvayı** isteği işleyecek iş parçacığına teslim edecek olan **yuva** örneğinin alınması sorumludur. Accept geri çağırma yöntemi <xref:System.AsyncCallback> temsilciyi uygular; bir void döndürür ve türünde <xref:System.IAsyncResult>tek bir parametre alır. Aşağıdaki örnek, Accept geri çağırma yönteminin kabuğudur.  
  
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
  
 **BeginAccept** yöntemi iki parametre alır. geri çağırma yöntemini işaret eden bir **AsyncCallback** temsilcisi ve geri çağırma yöntemine durum bilgilerini geçirmek için kullanılan bir nesne. Aşağıdaki örnekte, dinleme **yuvası** , *durum* parametresi aracılığıyla geri çağırma yöntemine geçirilir. Bu örnek, bir **AsyncCallback** temsilcisi oluşturur ve ağdan bağlantıları kabul etmeye başlar.  
  
```vb  
listener.BeginAccept( _  
    New AsyncCallback(SocketListener.AcceptCallback),_  
    listener)  
```  
  
```csharp  
listener.BeginAccept(new AsyncCallback(SocketListener.AcceptCallback), listener);  
```  
  
 Zaman uyumsuz yuvalar, gelen bağlantıları işlemek için sistem iş parçacığı havuzundan iş parçacıklarını kullanır. Bir iş parçacığı bağlantı kabul edilmeden sorumludur, her gelen bağlantıyı işlemek için başka bir iş parçacığı kullanılır ve bağlantıdan veri almaktan başka bir iş parçacığı sorumludur. Bunlar, iş parçacığı havuzunun hangi iş parçacığına atandığına bağlı olarak aynı iş parçacığı olabilir. Aşağıdaki örnekte, <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> sınıfı ana iş parçacığının yürütülmesini ve yürütme devam edebildikleri sinyalleri askıya alır.  
  
 Aşağıdaki örnek, yerel bilgisayarda zaman uyumsuz TCP/IP yuvası oluşturan ve bağlantıları kabul etmeye başlayan bir zaman uyumsuz yöntemi gösterir. Adlı bir genel **ManualResetEvent** `allDone`olduğunu, yöntemin adlı bir sınıfın `SocketListener`üyesi olduğunu ve adlı `AcceptCallback` bir geri çağırma yönteminin tanımlı olduğunu varsayar.  
  
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
  
 Geri aramayı kabul etme yöntemi`AcceptCallback` (önceki örnekte), ana uygulama iş parçacığının işleme devam etmesi, istemciyle bağlantı kurulması ve istemciden gelen verilerin zaman uyumsuz okumasından başlamasını sağlamaktan sorumludur. Aşağıdaki örnek, `AcceptCallback` yöntemi uygulamasının ilk bölümüdür. Yönteminin bu bölümü, işleme devam etmek için ana uygulama iş parçacığını bildirir ve istemciye bağlantı kurar. Adında`allDone`genel bir **ManualResetEvent** olduğunu varsayar.  
  
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
  
 İstemci yuvalarından veri okuma, zaman uyumsuz çağrılar arasında değer geçiren bir durum nesnesi gerektirir. Aşağıdaki örnek, uzak istemciden bir dize almak için bir durum nesnesi uygular. İstemci yuvasının alanlarını, veri almaya yönelik bir veri arabelleğini ve istemci tarafından gönderilen veri dizesini oluşturmak <xref:System.Text.StringBuilder> için bir içerir. Bu alanların durum nesnesine yerleştirilmesi, değerlerinin istemci yuvasında verileri okumak için birden çok çağrıda saklanması sağlar.  
  
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
  
 İlk olarak `AcceptCallback` , istemci yuvasından verileri almaya başlayan yönteminin bölümü, `StateObject` <xref:System.Net.Sockets.Socket.BeginReceive%2A> sınıfının bir örneğini başlatır ve ardından, istemci yuvasından zaman uyumsuz olarak veri okumaya başlamak için yöntemini çağırır.  
  
 Aşağıdaki örnek, tüm `AcceptCallback` yöntemi gösterir. `StateObject` `allDone,` Sınıfıntanımlandığını`SocketListener`veyöntemininadlıbir sınıfta tanımlandığını belirten küresel bir **ManualResetEvent olduğunu** varsayar.`ReadCallback`  
  
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
  
 Zaman uyumsuz yuva sunucusu için uygulanması gereken son yöntem, istemci tarafından gönderilen verileri döndüren okuma geri çağırma yöntemidir. Geri aramayı kabul et yöntemi gibi Read callback yöntemi bir **AsyncCallback** temsilcisidir. Bu yöntem, istemci yuvasından veri arabelleğine bir veya daha fazla bayt okur ve ardından istemci tarafından gönderilen veriler tamamlanana kadar **BeginReceive** metodunu yeniden çağırır. Tüm ileti istemciden okunduktan sonra, dize konsolda görüntülenir ve istemciyle bağlantıyı işleyen sunucu yuvası kapalıdır.  
  
 Aşağıdaki örnek `ReadCallback` yöntemini uygular. `StateObject` Sınıfın tanımlandığını varsayar.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [Zaman Uyumlu Sunucu Yuvası Kullanma](../../../docs/framework/network-programming/using-a-synchronous-server-socket.md)
- [Zaman Uyumsuz Sunucu Yuvası Örneği](../../../docs/framework/network-programming/asynchronous-server-socket-example.md)
- [İş parçacığı oluşturma](../../standard/threading/index.md)
- [Yuvalarla Dinleme](../../../docs/framework/network-programming/listening-with-sockets.md)
