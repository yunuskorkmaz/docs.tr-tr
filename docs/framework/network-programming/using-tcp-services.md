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
ms.openlocfilehash: 3678586647dcf9c47b4494197fbf56cab865b3d3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73039485"
---
# <a name="using-tcp-services"></a><span data-ttu-id="b41b2-102">TCP Hizmetleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="b41b2-102">Using TCP Services</span></span>

<span data-ttu-id="b41b2-103">Sınıf, <xref:System.Net.Sockets.TcpClient> TCP kullanarak bir Internet kaynağından veri ister.</span><span class="sxs-lookup"><span data-stu-id="b41b2-103">The <xref:System.Net.Sockets.TcpClient> class requests data from an Internet resource using TCP.</span></span> <span data-ttu-id="b41b2-104">**TcpClient'ın** yöntemleri ve özellikleri, TCP kullanarak veri istemek ve almak <xref:System.Net.Sockets.Socket> için ayrıntıları özetler.</span><span class="sxs-lookup"><span data-stu-id="b41b2-104">The methods and properties of **TcpClient** abstract the details for creating a <xref:System.Net.Sockets.Socket> for requesting and receiving data using TCP.</span></span> <span data-ttu-id="b41b2-105">Uzak aygıta bağlantı bir akış olarak temsil edildiğinden, veriler .NET Framework akışı işleme teknikleri ile okunabilir ve yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="b41b2-105">Because the connection to the remote device is represented as a stream, data can be read and written with .NET Framework stream-handling techniques.</span></span>

<span data-ttu-id="b41b2-106">TCP protokolü uzak bir uç nokta ile bir bağlantı kurar ve daha sonra veri paketleri göndermek ve almak için bu bağlantıyı kullanır.</span><span class="sxs-lookup"><span data-stu-id="b41b2-106">The TCP protocol establishes a connection with a remote endpoint and then uses that connection to send and receive data packets.</span></span> <span data-ttu-id="b41b2-107">TCP, veri paketlerinin uç noktaya gönderilmesini ve geldiklerinde doğru sırada bir araya getirildiğinden sorumludur.</span><span class="sxs-lookup"><span data-stu-id="b41b2-107">TCP is responsible for ensuring that data packets are sent to the endpoint and assembled in the correct order when they arrive.</span></span>

<span data-ttu-id="b41b2-108">TCP bağlantısı oluşturmak için, gereksinim duyduğunuz hizmeti barındıran ağ aygıtının adresini bilmeniz ve hizmetin iletişim kurmak için kullandığı TCP bağlantı noktasını bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b41b2-108">To establish a TCP connection, you must know the address of the network device hosting the service you need and you must know the TCP port that the service uses to communicate.</span></span> <span data-ttu-id="b41b2-109">Internet Atanmış Sayılar Yetkilisi (Iana), ortak hizmetler için bağlantı noktası numaralarını tanımlar (bkz. [Hizmet Adı ve Taşıma Protokolü Bağlantı Noktası Numarası Kayıt Defteri).](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)</span><span class="sxs-lookup"><span data-stu-id="b41b2-109">The Internet Assigned Numbers Authority (Iana) defines port numbers for common services (see [Service Name and Transport Protocol Port Number Registry](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)).</span></span> <span data-ttu-id="b41b2-110">Iana listesinde olmayan hizmetlerin bağlantı noktası numaraları 1.024 ile 65.535 arasında olabilir.</span><span class="sxs-lookup"><span data-stu-id="b41b2-110">Services not on the Iana list can have port numbers in the range 1,024 to 65,535.</span></span>

<span data-ttu-id="b41b2-111">Aşağıdaki örnek, TCP bağlantı noktası 13'teki bir zaman sunucusuna bağlanmak için bir **TcpClient** ayarlıyor:</span><span class="sxs-lookup"><span data-stu-id="b41b2-111">The following example demonstrates setting up a **TcpClient** to connect to a time server on TCP port 13:</span></span>

```vb
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

    Overloads Public Shared Function Main(args As String()) As Integer
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
    End Function
End Class
```

```csharp
using System;
using System.Net.Sockets;
using System.Text;

public class TcpTimeClient
{
    private const int portNum = 13;
    private const string hostName = "host.contoso.com";

    public static int Main(String[] args)
    {
        try
        {
            var client = new TcpClient(hostName, portNum);

            NetworkStream ns = client.GetStream();

            byte[] bytes = new byte[1024];
            int bytesRead = ns.Read(bytes, 0, bytes.Length);

            Console.WriteLine(Encoding.ASCII.GetString(bytes,0,bytesRead));

            client.Close();

        }
        catch (Exception e)
        {
            Console.WriteLine(e.ToString());
        }

        return 0;
    }
}
```

<span data-ttu-id="b41b2-112"><xref:System.Net.Sockets.TcpListener>gelen istekler için bir TCP bağlantı noktasını izlemek ve ardından istemciyle bağlantıyı yöneten bir **Soket** veya **TcpClient** oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b41b2-112"><xref:System.Net.Sockets.TcpListener> is used to monitor a TCP port for incoming requests and then create either a **Socket** or a **TcpClient** that manages the connection to the client.</span></span> <span data-ttu-id="b41b2-113">Yöntem <xref:System.Net.Sockets.TcpListener.Start%2A> dinlemeyi sağlar ve <xref:System.Net.Sockets.TcpListener.Stop%2A> yöntem bağlantı noktasında dinlemeyi devre dışı kılabilir.</span><span class="sxs-lookup"><span data-stu-id="b41b2-113">The <xref:System.Net.Sockets.TcpListener.Start%2A> method enables listening, and the <xref:System.Net.Sockets.TcpListener.Stop%2A> method disables listening on the port.</span></span> <span data-ttu-id="b41b2-114">Yöntem <xref:System.Net.Sockets.TcpListener.AcceptTcpClient%2A> gelen bağlantı isteklerini kabul eder ve isteği işlemek için bir <xref:System.Net.Sockets.TcpListener.AcceptSocket%2A> **TcpClient** oluşturur ve yöntem gelen bağlantı isteklerini kabul eder ve isteği işlemek için bir **Soket** oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b41b2-114">The <xref:System.Net.Sockets.TcpListener.AcceptTcpClient%2A> method accepts incoming connection requests and creates a **TcpClient** to handle the request, and the <xref:System.Net.Sockets.TcpListener.AcceptSocket%2A> method accepts incoming connection requests and creates a **Socket** to handle the request.</span></span>

<span data-ttu-id="b41b2-115">Aşağıdaki örnek, TCP bağlantı noktası 13'ü izlemek için bir **TcpListener** kullanarak bir ağ zaman sunucusu oluşturmayı göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="b41b2-115">The following example demonstrates creating a network time server using a **TcpListener** to monitor TCP port 13.</span></span> <span data-ttu-id="b41b2-116">Gelen bir bağlantı isteği kabul edildiğinde, zaman sunucusu ana bilgisayar sunucusundan geçerli tarih ve saatle yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="b41b2-116">When an incoming connection request is accepted, the time server responds with the current date and time from the host server.</span></span>

```vb
Imports System.Net
Imports System.Net.Sockets
Imports System.Text

Public Class TcpTimeServer

    Private const portNum As Integer = 13

    ' Entry point that delegates to C-style main Private Function.
    Public Overloads Shared Sub Main()
        System.Environment.ExitCode = _
            Main(System.Environment.GetCommandLineArgs())
    End Sub

    Overloads Public Shared Function Main(args As String()) As Integer
        Dim done As Boolean = False

        Dim listener As New TcpListener(IPAddress.Any, portNum)

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
    End Function
End Class
```

```csharp
using System;
using System.Net;
using System.Net.Sockets;
using System.Text;

public class TcpTimeServer
{

    private const int portNum = 13;

    public static int Main(String[] args)
    {
        bool done = false;

        var listener = new TcpListener(IPAddress.Any, portNum);

        listener.Start();

        while (!done)
        {
            Console.Write("Waiting for connection...");
            TcpClient client = listener.AcceptTcpClient();

            Console.WriteLine("Connection accepted.");
            NetworkStream ns = client.GetStream();

            byte[] byteTime = Encoding.ASCII.GetBytes(DateTime.Now.ToString());

            try
            {
                ns.Write(byteTime, 0, byteTime.Length);
                ns.Close();
                client.Close();
            }
            catch (Exception e)
            {
                Console.WriteLine(e.ToString());
            }
        }

        listener.Stop();

        return 0;
    }

}
```
