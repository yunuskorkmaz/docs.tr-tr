---
title: TCP Hizmetleri Kullanma
description: TcpClient sınıfı, TCP kullanarak veri istemek ve almak için bir yuva oluşturmak üzere ayrıntıları soyutlar. Veri okumak ve yazmak için akış işleme .NET Framework kullanın.
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
ms.openlocfilehash: 329701e8f11ca7f87c40ee8b2cc6a337435242b5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501969"
---
# <a name="using-tcp-services"></a>TCP Hizmetleri Kullanma

<xref:System.Net.Sockets.TcpClient>Sınıfı, TCP kullanarak bir Internet kaynağından veri ister. **TcpClient** 'ın yöntemleri ve ÖZELLIKLERI, <xref:System.Net.Sockets.Socket> TCP kullanarak veri istemek ve almak için oluşturma ayrıntılarını soyutlar. Uzak cihazla bağlantı bir akış olarak temsil ettiğinden, veriler .NET Framework akış işleme teknikleriyle okunabilir ve yazılabilir.

TCP protokolü, uzak bir uç nokta ile bağlantı kurar ve ardından bu bağlantıyı veri paketleri göndermek ve almak için kullanır. TCP, veri paketlerinin uç noktaya gönderilmesini ve ulaştığında doğru sırada derlenmesinden emin olmanın sorumluluğundadır.

TCP bağlantısı kurmak için, ihtiyacınız olan hizmeti barındıran ağ cihazının adresini bilmeniz ve hizmetin iletişim kurmak için kullandığı TCP bağlantı noktasını bilmeniz gerekir. Internet atanmış numaralar yetkilisi (IANA), ortak hizmetler için bağlantı noktası numaralarını tanımlar (bkz. [hizmet adı ve Aktarım Protokolü bağlantı noktası numarası kayıt defteri](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)). IANA listesinde bulunmayan hizmetler 1.024-65.535 aralığında bağlantı noktası numaralarına sahip olabilir.

Aşağıdaki örnek, TCP bağlantı noktası 13 ' te bir zaman sunucusuna bağlanmak için bir **TcpClient** ayarlamayı göstermektedir:

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

<xref:System.Net.Sockets.TcpListener>, gelen istekler için bir TCP bağlantı noktasını izlemek ve ardından istemciyle bağlantıyı yöneten bir **yuva** ya da **TcpClient** oluşturmak için kullanılır. <xref:System.Net.Sockets.TcpListener.Start%2A>Yöntemi dinlemeyi etkinleştirilir ve <xref:System.Net.Sockets.TcpListener.Stop%2A> yöntemi bağlantı noktasında dinlemeyi devre dışı bırakır. <xref:System.Net.Sockets.TcpListener.AcceptTcpClient%2A>Yöntemi gelen bağlantı isteklerini kabul eder ve isteği işlemek için bir **TcpClient** oluşturur ve <xref:System.Net.Sockets.TcpListener.AcceptSocket%2A> yöntemi gelen bağlantı isteklerini kabul eder ve Isteği işlemek için bir **yuva** oluşturur.

Aşağıdaki örnek, TCP bağlantı noktası 13 ' ü izlemek için bir **TcpListener** kullanarak bir ağ zaman sunucusu oluşturmayı göstermektedir. Gelen bir bağlantı isteği kabul edildiğinde, sunucu, ana bilgisayar sunucusundan geçerli tarih ve saat ile yanıt verir.

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
