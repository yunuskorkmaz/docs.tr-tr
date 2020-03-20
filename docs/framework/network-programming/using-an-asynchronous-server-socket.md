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
ms.openlocfilehash: 467804e685d800643c421ed1aad040a842b42886
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180628"
---
# <a name="using-an-asynchronous-server-socket"></a>Zaman Uyumsuz Sunucu Yuvası Kullanma
Asynchronous sunucu soketleri ağ hizmeti isteklerini işlemek için .NET Framework asynchronous programlama modelini kullanır. Sınıf <xref:System.Net.Sockets.Socket> standart .NET Framework asynchronous adlandırma deseni izler; örneğin, senkron <xref:System.Net.Sockets.Socket.Accept%2A> yöntem asynchronous <xref:System.Net.Sockets.Socket.BeginAccept%2A> ve <xref:System.Net.Sockets.Socket.EndAccept%2A> yöntemleri karşılık gelir.  
  
 Asynchronous sunucu soketi, ağdan bağlantı isteklerini kabul etmeye başlamak için bir yöntem, bağlantı isteklerini işlemek ve ağdan veri almaya başlamak için bir geri arama yöntemi ve verileri almayı sona erdirmek için bir geri arama yöntemi gerektirir. Tüm bu yöntemler bu bölümde daha fazla ele alınmıştır.  
  
 Aşağıdaki örnekte, ağdan bağlantı isteklerini kabul `StartListening` etmeye başlamak için, yöntem **Soketi** başlatır ve ardından yeni bağlantıları kabul etmeye başlamak için **BeginAccept** yöntemini kullanır. Yuvada yeni bir bağlantı isteği alındığı zaman geri aramayı kabul etme yöntemi çağrılır. Bağlantıyı işleyecek **Soket** örneğini almaktan ve bu **Soketi** isteği işleyecek iş parçacığına teslim etmeden sorumludur. Geri aramayı kabul et <xref:System.AsyncCallback> yöntemi temsilciyi uygular; bir boşluk döndürür ve türünden <xref:System.IAsyncResult>tek bir parametre alır. Aşağıdaki örnek, geri arama kabul yönteminin kabuğudur.  
  
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
  
 **BeginAccept** yöntemi iki parametre alır, geri çağırma yı kabul etme yöntemini işaret eden bir **AsyncCallback** temsilcisi ve durum bilgilerini geri arama yöntemine aktarmak için kullanılan bir nesne. Aşağıdaki örnekte, dinleme **Soketi** *durum* parametresi aracılığıyla geri arama yöntemine aktarılır. Bu örnek bir **AsyncCallback** temsilcisi oluşturur ve ağdan bağlantıları kabul etmeye başlar.  
  
```vb  
listener.BeginAccept( _  
    New AsyncCallback(SocketListener.AcceptCallback),_  
    listener)  
```  
  
```csharp  
listener.BeginAccept(new AsyncCallback(SocketListener.AcceptCallback), listener);  
```  
  
 Asynchronous soketleri gelen bağlantıları işlemek için sistem iş parçacığı havuzundan iş parçacığı kullanır. Bir iş parçacığı bağlantıları kabul etmekten sorumludur, gelen her bağlantıyı işlemek için başka bir iş parçacığı kullanılır ve başka bir iş parçacığı bağlantıdan veri almaktan sorumludur. Bunlar, iş parçacığı havuzu tarafından atanan iş parçacığına bağlı olarak aynı iş parçacığı olabilir. Aşağıdaki örnekte, <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> sınıf ana iş parçacığının yürütülmesini askıya adakalır ve yürütmenin ne zaman devam edebileceği sinyalleri iletamama.  
  
 Aşağıdaki örnek, yerel bilgisayarda eşzamanlı bir TCP/IP soketi oluşturan ve bağlantıları kabul etmeye başlayan bir eşzamanlı yöntem gösterir. Bu, adında genel bir **ManualResetEvent** olduğunu `allDone`varsayar, yöntem adlı `SocketListener`bir sınıfın üyesi olduğunu `AcceptCallback` , ve adlı bir geri arama yöntemi tanımlanır.  
  
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
  
 Geri aramayı kabul`AcceptCallback` etme yöntemi (önceki örnekte) ana uygulama iş parçacığının işlemedevam etmesi için sinyal verme, istemciyle bağlantı kurma ve istemciden gelen verilerin eşzamanlı okumasını başlatmaktan sorumludur. Aşağıdaki örnek, `AcceptCallback` yöntemin uygulanmasının ilk bölümüdür. Yöntemin bu bölümü, işleme devam etmek için ana uygulama iş parçacığı sinyalleri ve istemciye bağlantı kurar. Bu adlı `allDone`genel bir **ManualResetEvent** varsayar.  
  
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
  
 İstemci yuvasından veri okuma, eşsenkronize çağrılar arasında değerleri geçen bir durum nesnesi gerektirir. Aşağıdaki örnek, uzak istemciden bir dize almak için bir durum nesnesi uygular. İstemci yuvası için alanlar, veri almak için bir <xref:System.Text.StringBuilder> veri arabelleği ve istemci tarafından gönderilen veri dizesini oluşturmak için bir alan içerir. Bu alanların durum nesnesine yerleştirilmesi, istemci yuvasından gelen verileri okumak için değerlerinin birden çok çağrı arasında korunmasına olanak tanır.  
  
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
  
 Yöntemin `AcceptCallback` istemci soketinden veri almaya başlayan bölümü önce `StateObject` sınıfın bir örneğini başlatır ve ardından istemci soketinden verileri eşzamanlı olarak okumaya başlamak için <xref:System.Net.Sockets.Socket.BeginReceive%2A> yöntemi çağırır.  
  
 Aşağıdaki örnek, tam `AcceptCallback` yöntemi gösterir. `StateObject` **ManualResetEvent** `ReadCallback` Sınıfın tanımlandığını ve yöntemin . `SocketListener` `allDone,`  
  
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
  
 Asynchronous soket sunucusu için uygulanması gereken son yöntem, istemci tarafından gönderilen verileri döndüren okuma geri arama yöntemidir. Geri aramayı kabul et yöntemi gibi, okuma geri arama yöntemi de bir **AsyncCallback** temsilcisidir. Bu yöntem, istemci yuvasından veri arabelleği içine bir veya daha fazla bayt okur ve istemci tarafından gönderilen veriler tamamlanana kadar **BeginReceive** yöntemini yeniden çağırır. İletinin tamamı istemciden okunduktan sonra, dize konsolda görüntülenir ve istemciye bağlantı işleyen sunucu soketi kapatılır.  
  
 Aşağıdaki örnek `ReadCallback` yöntemi uygular. `StateObject` Sınıfın tanımlandığını varsayar.  
  
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

- [Zaman Uyumlu Sunucu Yuvası Kullanma](using-a-synchronous-server-socket.md)
- [Zaman Uyumsuz Sunucu Yuvası Örneği](asynchronous-server-socket-example.md)
- [İş Parçacığı Oluşturma](../../standard/threading/index.md)
- [Yuvalarla Dinleme](listening-with-sockets.md)
