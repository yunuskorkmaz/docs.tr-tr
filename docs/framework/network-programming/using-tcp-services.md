---
title: TCP Hizmetleri kullanma
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
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: d11566182cc9d0b4f2634350868ec94a0685d996
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="using-tcp-services"></a>TCP Hizmetleri kullanma
<xref:System.Net.Sockets.TcpClient> Sınıfı TCP kullanarak bir Internet kaynağından veri ister. Özellikleri ve yöntemleri **TcpClient** oluşturmak için ayrıntıları soyut bir <xref:System.Net.Sockets.Socket> isteme ve TCP kullanarak veri almak için. Uzak aygıt bağlantısı bir akış olarak temsil edilir çünkü veri okumak ve .NET Framework akış işleme teknikleri ile yazılır.  
  
 TCP protokolü uzak uç noktasıyla bağlantı kurar ve veri paket göndermek ve almak için bu bağlantıyı kullanır. TCP veri paketlerinin uç noktasına gönderilen ve doğru sırada geldiğinde birleştirilen emin sorumludur.  
  
 TCP bağlantı kurmak için gereksinim duyduğunuz hizmetini barındıran ağ aygıtı adresini bilmeniz gerekir ve hizmetin iletişim kurmak için kullandığı TCP bağlantı noktasını bilmesi gerekir. Internet Atanmış Numaralar Yetkilisi (IANA) (www.iana.org/assignments/port-numbers bakın) ortak Hizmetleri için bağlantı noktası numaralarını tanımlar. IANA listede olmayan Hizmetleri bağlantı noktası numaraları 1024 65. 535'ı için aralığında olabilir.  
  
 Aşağıdaki örnek, Yukarı ayarını gösterir. bir **TcpClient** numaralı TCP bağlantı noktasında 13 zaman sunucuya bağlanılamadı.  
  
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
  
 <xref:System.Net.Sockets.TcpListener> bir TCP bağlantı noktası gelen istekler için izleme ve ya da oluşturmak için kullanılan bir **yuva** veya **TcpClient** istemciye bağlantıyı yönetir. <xref:System.Net.Sockets.TcpListener.Start%2A> Yöntemi etkinleştirir dinleme ve <xref:System.Net.Sockets.TcpListener.Stop%2A> yöntemi bağlantı noktası üzerinde dinleme devre dışı bırakır. <xref:System.Net.Sockets.TcpListener.AcceptTcpClient%2A> Yöntemi gelen bağlantı isteklerini kabul eder ve oluşturur bir **TcpClient** isteği işlemek üzere ve <xref:System.Net.Sockets.TcpListener.AcceptSocket%2A> yöntemi gelen bağlantı isteklerini kabul eder ve oluşturur bir **yuva**isteği işlemek üzere.  
  
 Aşağıdaki örnek, bir ağ zaman sunucu kullanarak oluşturma gösterir bir **TcpListener** TCP bağlantı noktası 13 izlemek için. Gelen bir bağlantı isteği kabul edildiğinde zaman sunucu geçerli tarih ve saat konak sunucusundan yanıt verir.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 
