---
title: Zaman uyumsuz Server yuva kullanma
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: c5c696e04b940923d53eb79c055330a91734e1a0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="using-an-asynchronous-server-socket"></a>Zaman uyumsuz Server yuva kullanma
Zaman uyumsuz server yuva ağ hizmet isteklerini işlemek için .NET Framework zaman uyumsuz programlama modeli kullanın. <xref:System.Net.Sockets.Socket> Sınıfı izleyen standart .NET Framework zaman uyumsuz adlandırma deseni; Örneğin, zaman uyumlu <xref:System.Net.Sockets.Socket.Accept%2A> yöntemi karşılık gelen için zaman uyumsuz <xref:System.Net.Sockets.Socket.BeginAccept%2A> ve <xref:System.Net.Sockets.Socket.EndAccept%2A> yöntemleri.  
  
 Zaman uyumsuz server yuva veri alma sona erdirmek için ağ, bağlantı isteklerini işler ve ağ üzerinden veri almaya başlamak için bir geri çağırma yöntemini ve bir geri çağırma yöntemi gelen bağlantı istekleri kabul başlamak için bir yöntem gerektirir. Tüm bu yöntemleri ele alınan bu bölümün sonraki kısımlarında.  
  
 Yöntemi ağ gelen bağlantı istekleri kabul başlamak için aşağıdaki örnekte, `StartListening` başlatır **yuva** ve ardından **BeginAccept** yeni kabul başlatmak için yöntemi bağlantılar. Yeni bir bağlantı isteği yuvada alındığında kabul geri çağırma yöntemi çağrılır. Dağıtımından sorumlu **yuva** bağlantı ve, teslim etme işleyecek örneği **yuva** isteği işleyen iş parçacığına kapalı. Accept geri çağırma yöntemini uygulayan <xref:System.AsyncCallback> temsilci; tek bir parametre türü alır ve bir geçersiz kılma döndürür <xref:System.IAsyncResult>. Aşağıdaki örnek bir accept geri çağırma yöntemini Kabuk aynıdır.  
  
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
  
 **BeginAccept** yöntemi iki parametre alan bir **AsyncCallback** accept geri çağırma yöntemini ve durum bilgilerini geri çağırma yöntemi iletmek için kullanılan nesneyi işaret eden temsilci. Aşağıdaki örnekte dinleme **yuva** geri çağırma yöntemine geçirilen *durumu* parametresi. Bu örnekte bir **AsyncCallback** temsilci ve ağ gelen bağlantıları kabul başlatır.  
  
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
  
 Zaman uyumsuz yuva iş parçacıkları sistem iş parçacığı havuzundan gelen bağlantıları işlemek için kullanın. Bir iş parçacığı bağlantıları kabul etmek için sorumlu olduğu, başka bir iş parçacığı her gelen bağlantı işlemek için kullanılır ve başka bir iş parçacığı bağlantısından veri almak için sorumludur. Bu iş parçacığı havuzu tarafından atanan iş parçacığı bağlı olarak, aynı iş parçacığı olabilir. Aşağıdaki örnekte, <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> sınıf ana iş parçacığı yürütmesi askıya alır ve yürütme devam ederken işaret eder.  
  
 Aşağıdaki örnekte, yerel bilgisayarda bir zaman uyumsuz TCP/IP'yi yuva oluşturur ve bağlantıları kabul başlar zaman uyumsuz bir yöntem gösterilmektedir. Bunu olduğunu genel varsaydığını **ManualResetEvent** adlı `allDone`, yöntem adlı bir sınıf üyesi olduğunu `SocketListener`, ve bir geri çağırma yöntemi adlı `acceptCallback` tanımlanır.  
  
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
  
 Kabul et geri çağırma yöntemi (`acceptCallback` önceki örnekte) işleme, istemci ile bağlantı kurma ve zaman uyumsuz başlatılıyor devam etmek için ana uygulama iş parçacığı sinyal verilerin istemciden okumak için sorumludur. Aşağıdaki örnek uygulaması ilk parçası olan `acceptCallback` yöntemi. Bu bölümde yönteminin işleme devam etmek için ana uygulama iş parçacığı bildirir ve istemci bağlantı kurar. Bir genel varsayar **ManualResetEvent** adlı `allDone`.  
  
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
  
 Bir istemci yuvadan veri okunurken değerleri arasında zaman uyumsuz çağrılar geçiren bir durum nesnesi gerektirir. Aşağıdaki örnek uzak istemci tarafından bir dizesini almak için bir durum nesnesi uygular. Alan veri almak için bir veri arabelleğini istemci yuva için içeriyor ve bir <xref:System.Text.StringBuilder> istemci tarafından gönderilen veri dizesi oluşturmak için. Bu alanların durumu nesnesinde yerleştirme istemci yuvadan verileri okumak için birden fazla çağrı arasında korunması değerlerine izin verir.  
  
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
  
 Bölümünü `acceptCallback` istemci yuvadan veri alma başlatır yöntemi ilk örneği başlatır `StateObject` sınıfı ve çağrıları <xref:System.Net.Sockets.Socket.BeginReceive%2A> verileri zaman uyumsuz olarak istemci yuvadan okumaya başlamak için yöntem.  
  
 Aşağıdaki örnek eksiksiz gösterir `acceptCallback` yöntemi. Bunu olduğunu genel varsaydığını **ManualResetEvent** adlı `allDone,` , `StateObject` sınıfı tanımlanır ve `readCallback` yöntemi adlı bir sınıf içinde tanımlanan `SocketListener`.  
  
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
  
 Zaman uyumsuz yuvası sunucusu için uygulanması gereken son yöntemi istemci tarafından gönderilen verileri döndüren okuma geri çağırma yöntemidir. Kabul et geri çağırma yöntemi gibi okuma geri çağırma yöntemi olan bir **AsyncCallback** temsilci. Bu yöntem, bir veya daha fazla bayt veri arabelleğe istemci yuvadan okur ve daha sonra çağırır **BeginReceive** yeniden istemci tarafından gönderilen verileri kadar yöntemi tamamlanmıştır. İletinin tamamını istemciden okunan sonra dize konsolda görüntülenir ve istemci bağlantısı işleme server yuva kapalı.  
  
 Aşağıdaki örnek uygulayan `readCallback` yöntemi. Varsayılmaktadır `StateObject` sınıfı tanımlanır.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Zaman uyumlu Server yuva kullanma](../../../docs/framework/network-programming/using-a-synchronous-server-socket.md)  
 [Zaman uyumsuz Server yuva örneği](../../../docs/framework/network-programming/asynchronous-server-socket-example.md)  
 [İş parçacığı oluşturma](../../../docs/standard/threading/index.md)  
 [Yuva başına dinleme](../../../docs/framework/network-programming/listening-with-sockets.md)
