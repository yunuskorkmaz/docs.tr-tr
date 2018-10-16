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
ms.openlocfilehash: 6c586416daedca63628672ddf090fa808fad3f4e
ms.sourcegitcommit: fd8d4587cc26e53f0e27e230d6e27d828ef4306b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2018
ms.locfileid: "49347608"
---
# <a name="using-tcp-services"></a>TCP Hizmetleri kullanma
<xref:System.Net.Sockets.TcpClient> Sınıfı veri TCP kullanarak bir Internet kaynaktan ister. Özellikleri ve yöntemleri **TcpClient** oluşturmak için ayrıntıları soyut bir <xref:System.Net.Sockets.Socket> istemek ve TCP kullanarak veri alma. Uzak cihazla bağlantı bir akış olarak temsil edilir çünkü veri okumak ve .NET Framework akış işleme teknikleri ile yazılır.  
  
 TCP protokolü, uzak uç noktası ile bağlantı kurar ve veri paket göndermek ve almak için bu bağlantıyı kullanır. TCP veri paketleri uç noktaya gönderdi ve doğru sırada ulaştığında bir araya getirilen sağlamaktan sorumludur.  
  
 TCP bağlantısı kurmak için ihtiyacınız hizmet barındırma ağ aygıtı adresini bilmeniz gerekir ve hizmetin iletişim kurmak için kullandığı TCP bağlantı noktasını bilmesi gerekir. Ortak Hizmetleri için bağlantı noktası numaralarını Internet Atanmış Numaralar Yetkilisi (IANA) tanımlar (bkz [hizmet adını ve Aktarım Protokolü bağlantı noktası numarasını kayıt defteri](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)). IANA listede olmayan Hizmetleri bağlantı noktası numaraları için 1024 65,535 aralığında olabilir.  
  
 Aşağıdaki örnek, yedekleme ayarı gösterir. bir **TcpClient** bağlanmak için bir saat sunucusu TCP bağlantı noktası 13.  
  
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
  
 <xref:System.Net.Sockets.TcpListener> bir TCP bağlantı noktası gelen istekler için izleme ve ya da oluşturmak için kullanılan bir **yuva** veya **TcpClient** , istemci bağlantısı yönetir. <xref:System.Net.Sockets.TcpListener.Start%2A> Yöntemi dinleme, etkinleştirir ve <xref:System.Net.Sockets.TcpListener.Stop%2A> yöntemi bağlantı noktası üzerinde dinleme devre dışı bırakır. <xref:System.Net.Sockets.TcpListener.AcceptTcpClient%2A> Yöntemi gelen bağlantı isteklerini kabul eder ve oluşturur bir **TcpClient** isteği işlemek için ve <xref:System.Net.Sockets.TcpListener.AcceptSocket%2A> yöntemi gelen bağlantı isteklerini kabul eder ve oluşturur bir **yuva**isteği işlemek için.  
  
 Aşağıdaki örnek, bir ağ saat sunucusu kullanarak oluşturmayı gösterir. bir **TcpListener** TCP bağlantı noktası 13 izlemek için. Bir gelen bağlantı isteğini kabul edildiğinde, saat sunucusu geçerli tarih ve saat ile konak sunucusundan yanıt verir.  
  
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
 
