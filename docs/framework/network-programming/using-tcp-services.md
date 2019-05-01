---
title: TCP Hizmetleri Kullanma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- requesting data from Internet, TCP
- receiving data, TCP
- TcpClient class, about TcpClient class
- data requests, TCP
- application protocols, TCP
- network resources, TCP
- sending data, TCP
- TCP
- protocols, TCP
- Internet, TCP
ms.assetid: d2811830-3bcb-495c-b82d-cda9cf919aad
ms.openlocfilehash: d9b3c9975c4d10649bdecd6f63cf362a2b2a2738
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61788134"
---
# <a name="using-tcp-services"></a><span data-ttu-id="ae314-102">TCP Hizmetleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="ae314-102">Using TCP Services</span></span>

<span data-ttu-id="ae314-103"><xref:System.Net.Sockets.TcpClient> Sınıfı veri TCP kullanarak bir Internet kaynaktan ister.</span><span class="sxs-lookup"><span data-stu-id="ae314-103">The <xref:System.Net.Sockets.TcpClient> class requests data from an Internet resource using TCP.</span></span> <span data-ttu-id="ae314-104">Özellikleri ve yöntemleri **TcpClient** oluşturmak için ayrıntıları soyut bir <xref:System.Net.Sockets.Socket> istemek ve TCP kullanarak veri alma.</span><span class="sxs-lookup"><span data-stu-id="ae314-104">The methods and properties of **TcpClient** abstract the details for creating a <xref:System.Net.Sockets.Socket> for requesting and receiving data using TCP.</span></span> <span data-ttu-id="ae314-105">Uzak cihazla bağlantı bir akış olarak temsil edilir çünkü veri okumak ve .NET Framework akış işleme teknikleri ile yazılır.</span><span class="sxs-lookup"><span data-stu-id="ae314-105">Because the connection to the remote device is represented as a stream, data can be read and written with .NET Framework stream-handling techniques.</span></span>  
  
 <span data-ttu-id="ae314-106">TCP protokolü, uzak uç noktası ile bağlantı kurar ve veri paket göndermek ve almak için bu bağlantıyı kullanır.</span><span class="sxs-lookup"><span data-stu-id="ae314-106">The TCP protocol establishes a connection with a remote endpoint and then uses that connection to send and receive data packets.</span></span> <span data-ttu-id="ae314-107">TCP veri paketleri uç noktaya gönderdi ve doğru sırada ulaştığında bir araya getirilen sağlamaktan sorumludur.</span><span class="sxs-lookup"><span data-stu-id="ae314-107">TCP is responsible for ensuring that data packets are sent to the endpoint and assembled in the correct order when they arrive.</span></span>  
  
 <span data-ttu-id="ae314-108">TCP bağlantısı kurmak için ihtiyacınız hizmet barındırma ağ aygıtı adresini bilmeniz gerekir ve hizmetin iletişim kurmak için kullandığı TCP bağlantı noktasını bilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="ae314-108">To establish a TCP connection, you must know the address of the network device hosting the service you need and you must know the TCP port that the service uses to communicate.</span></span> <span data-ttu-id="ae314-109">Ortak Hizmetleri için bağlantı noktası numaralarını Internet Atanmış Numaralar Yetkilisi (IANA) tanımlar (bkz [hizmet adını ve Aktarım Protokolü bağlantı noktası numarasını kayıt defteri](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)).</span><span class="sxs-lookup"><span data-stu-id="ae314-109">The Internet Assigned Numbers Authority (Iana) defines port numbers for common services (see [Service Name and Transport Protocol Port Number Registry](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)).</span></span> <span data-ttu-id="ae314-110">IANA listede olmayan Hizmetleri bağlantı noktası numaraları için 1024 65,535 aralığında olabilir.</span><span class="sxs-lookup"><span data-stu-id="ae314-110">Services not on the Iana list can have port numbers in the range 1,024 to 65,535.</span></span>  
  
 <span data-ttu-id="ae314-111">Aşağıdaki örnek, yedekleme ayarı gösterir. bir **TcpClient** bağlanmak için bir saat sunucusu TCP bağlantı noktası 13.</span><span class="sxs-lookup"><span data-stu-id="ae314-111">The following example demonstrates setting up a **TcpClient** to connect to a time server on TCP port 13.</span></span>  
  
```vb  
Imports System  
Imports System.Net.Sockets  
Imports System.Text  
  
Public Class TcpTimeClient  
    Private const portNum As Integer = 13  
    Private const hostName As String = "host.contoso.com"  
  
    ' Entry point  that delegates to C-style main Private Function.  
    Public Overloads Shared Sub Main()  
        System.Environment.ExitCode = _  
            Main(System.Environment.GetCommandLineArgs())  
    End Sub  
  
    Overloads Public Shared Function Main(args() As [String]) As Integer  
        Try  
            Dim client As New TcpClient(hostName, portNum)  
  
            Dim ns As NetworkStream = client.GetStream()  
  
            Dim bytes(1024) As Byte  
            Dim bytesRead As Integer = ns.Read(bytes, 0, bytes.Length)  
  
            Console.WriteLine(Encoding.ASCII.GetString(bytes, 0, bytesRead))  
  
        Catch e As Exception  
            Console.WriteLine(e.ToString())  
        End Try  
  
        client.Close()  
  
        Return 0  
    End Function 'Main  
End Class 'TcpTimeClient  
```  
  
```csharp  
using System;  
using System.Net.Sockets;  
using System.Text;  
  
public class TcpTimeClient {  
    private const int portNum = 13;  
    private const string hostName = "host.contoso.com";  
  
    public static int Main(String[] args) {  
        try {  
            TcpClient client = new TcpClient(hostName, portNum);  
  
            NetworkStream ns = client.GetStream();  
  
            byte[] bytes = new byte[1024];  
            int bytesRead = ns.Read(bytes, 0, bytes.Length);  
  
            Console.WriteLine(Encoding.ASCII.GetString(bytes,0,bytesRead));  
  
            client.Close();  
  
        } catch (Exception e) {  
            Console.WriteLine(e.ToString());  
        }  
  
        return 0;  
    }  
}  
```  
  
 <span data-ttu-id="ae314-112"><xref:System.Net.Sockets.TcpListener> bir TCP bağlantı noktası gelen istekler için izleme ve ya da oluşturmak için kullanılan bir **yuva** veya **TcpClient** , istemci bağlantısı yönetir.</span><span class="sxs-lookup"><span data-stu-id="ae314-112"><xref:System.Net.Sockets.TcpListener> is used to monitor a TCP port for incoming requests and then create either a **Socket** or a **TcpClient** that manages the connection to the client.</span></span> <span data-ttu-id="ae314-113"><xref:System.Net.Sockets.TcpListener.Start%2A> Yöntemi dinleme, etkinleştirir ve <xref:System.Net.Sockets.TcpListener.Stop%2A> yöntemi bağlantı noktası üzerinde dinleme devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="ae314-113">The <xref:System.Net.Sockets.TcpListener.Start%2A> method enables listening, and the <xref:System.Net.Sockets.TcpListener.Stop%2A> method disables listening on the port.</span></span> <span data-ttu-id="ae314-114"><xref:System.Net.Sockets.TcpListener.AcceptTcpClient%2A> Yöntemi gelen bağlantı isteklerini kabul eder ve oluşturur bir **TcpClient** isteği işlemek için ve <xref:System.Net.Sockets.TcpListener.AcceptSocket%2A> yöntemi gelen bağlantı isteklerini kabul eder ve oluşturur bir **yuva**isteği işlemek için.</span><span class="sxs-lookup"><span data-stu-id="ae314-114">The <xref:System.Net.Sockets.TcpListener.AcceptTcpClient%2A> method accepts incoming connection requests and creates a **TcpClient** to handle the request, and the <xref:System.Net.Sockets.TcpListener.AcceptSocket%2A> method accepts incoming connection requests and creates a **Socket** to handle the request.</span></span>  
  
 <span data-ttu-id="ae314-115">Aşağıdaki örnek, bir ağ saat sunucusu kullanarak oluşturmayı gösterir. bir **TcpListener** TCP bağlantı noktası 13 izlemek için.</span><span class="sxs-lookup"><span data-stu-id="ae314-115">The following example demonstrates creating a network time server using a **TcpListener** to monitor TCP port 13.</span></span> <span data-ttu-id="ae314-116">Bir gelen bağlantı isteğini kabul edildiğinde, saat sunucusu geçerli tarih ve saat ile konak sunucusundan yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="ae314-116">When an incoming connection request is accepted, the time server responds with the current date and time from the host server.</span></span>  
  
```vb  
Imports System  
Imports System.Net.Sockets  
Imports System.Text  
  
Public Class TcpTimeServer  
  
    Private const portNum As Integer = 13  
  
    ' Entry point that delegates to C-style main Private Function.  
    Public Overloads Shared Sub Main()  
        System.Environment.ExitCode = _  
            Main(System.Environment.GetCommandLineArgs())  
    End Sub  
  
    Overloads Public Shared Function Main(args() As [String]) As Integer  
        Dim done As Boolean = False  
  
        Dim listener As New TcpListener(portNum)  
  
        listener.Start()  
  
        While Not done  
            Console.Write("Waiting for connection...")  
            Dim client As TcpClient = listener.AcceptTcpClient()  
  
            Console.WriteLine("Connection accepted.")  
            Dim ns As NetworkStream = client.GetStream()  
  
            Dim byteTime As Byte() = _  
                Encoding.ASCII.GetBytes(DateTime.Now.ToString())  
  
            Try  
                ns.Write(byteTime, 0, byteTime.Length)  
                ns.Close()  
                client.Close()  
            Catch e As Exception  
                Console.WriteLine(e.ToString())  
            End Try  
        End While  
  
        listener.Stop()  
  
        Return 0  
    End Function 'Main  
End Class 'TcpTimeServer  
```  
  
```csharp  
using System;  
using System.Net.Sockets;  
using System.Text;  
  
public class TcpTimeServer {  
  
    private const int portNum = 13;  
  
    public static int Main(String[] args) {  
        bool done = false;  
  
        TcpListener listener = new TcpListener(portNum);  
  
        listener.Start();  
  
        while (!done) {  
            Console.Write("Waiting for connection...");  
            TcpClient client = listener.AcceptTcpClient();  
  
            Console.WriteLine("Connection accepted.");  
            NetworkStream ns = client.GetStream();  
  
            byte[] byteTime = Encoding.ASCII.GetBytes(DateTime.Now.ToString());  
  
            try {  
                ns.Write(byteTime, 0, byteTime.Length);  
                ns.Close();  
                client.Close();  
            } catch (Exception e) {  
                Console.WriteLine(e.ToString());  
            }  
        }  
  
        listener.Stop();  
  
        return 0;  
    }  
  
}  
```
