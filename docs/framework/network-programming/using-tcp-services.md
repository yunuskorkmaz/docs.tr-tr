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
# <a name="using-tcp-services"></a>TCP Hizmetleri Kullanma

Sınıf, <xref:System.Net.Sockets.TcpClient> TCP kullanarak bir Internet kaynağından veri ister. **TcpClient'ın** yöntemleri ve özellikleri, TCP kullanarak veri istemek ve almak <xref:System.Net.Sockets.Socket> için ayrıntıları özetler. Uzak aygıta bağlantı bir akış olarak temsil edildiğinden, veriler .NET Framework akışı işleme teknikleri ile okunabilir ve yazılabilir.

TCP protokolü uzak bir uç nokta ile bir bağlantı kurar ve daha sonra veri paketleri göndermek ve almak için bu bağlantıyı kullanır. TCP, veri paketlerinin uç noktaya gönderilmesini ve geldiklerinde doğru sırada bir araya getirildiğinden sorumludur.

TCP bağlantısı oluşturmak için, gereksinim duyduğunuz hizmeti barındıran ağ aygıtının adresini bilmeniz ve hizmetin iletişim kurmak için kullandığı TCP bağlantı noktasını bilmeniz gerekir. Internet Atanmış Sayılar Yetkilisi (Iana), ortak hizmetler için bağlantı noktası numaralarını tanımlar (bkz. [Hizmet Adı ve Taşıma Protokolü Bağlantı Noktası Numarası Kayıt Defteri).](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml) Iana listesinde olmayan hizmetlerin bağlantı noktası numaraları 1.024 ile 65.535 arasında olabilir.

Aşağıdaki örnek, TCP bağlantı noktası 13'teki bir zaman sunucusuna bağlanmak için bir **TcpClient** ayarlıyor:

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

<xref:System.Net.Sockets.TcpListener>gelen istekler için bir TCP bağlantı noktasını izlemek ve ardından istemciyle bağlantıyı yöneten bir **Soket** veya **TcpClient** oluşturmak için kullanılır. Yöntem <xref:System.Net.Sockets.TcpListener.Start%2A> dinlemeyi sağlar ve <xref:System.Net.Sockets.TcpListener.Stop%2A> yöntem bağlantı noktasında dinlemeyi devre dışı kılabilir. Yöntem <xref:System.Net.Sockets.TcpListener.AcceptTcpClient%2A> gelen bağlantı isteklerini kabul eder ve isteği işlemek için bir <xref:System.Net.Sockets.TcpListener.AcceptSocket%2A> **TcpClient** oluşturur ve yöntem gelen bağlantı isteklerini kabul eder ve isteği işlemek için bir **Soket** oluşturur.

Aşağıdaki örnek, TCP bağlantı noktası 13'ü izlemek için bir **TcpListener** kullanarak bir ağ zaman sunucusu oluşturmayı göstermektedir. Gelen bir bağlantı isteği kabul edildiğinde, zaman sunucusu ana bilgisayar sunucusundan geçerli tarih ve saatle yanıt verir.

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
