---
title: UDP Hizmetleri kullanma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- protocols, UDP
- network resources, UDP
- requesting data from Internet, UDP
- UDP
- receiving data, UDP
- Internet, UDP
- broadcasting messages to multiple addresses
- data requests, UDP
- UdpClient class, about UdpClient class
- sending data, UDP
- application protocols, UDP
ms.assetid: d5c3477a-e798-454c-a890-738ba14c5707
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: bc325a551afd0190ea71b46cc53a275de635bda3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33397640"
---
# <a name="using-udp-services"></a>UDP Hizmetleri kullanma
<xref:System.Net.Sockets.UdpClient> Sınıfı için UDP kullanan ağ hizmetleri ile iletişim kurar. Özellikleri ve yöntemleri <xref:System.Net.Sockets.UdpClient> oluşturma ayrıntılarını soyut sınıf bir <xref:System.Net.Sockets.Socket> isteme ve UDP kullanarak veri almak için.  
  
 Kullanıcı Veri Birimi Protokolü (UDP) uzaktaki bir ana bilgisayara verileri sunmak için bir en iyi çaba sağlayan basit bir protokoldür. Ancak, UDP protokolünü bağlantısız bir protokol olduğundan, uzak uç noktasına gönderilen UDP veri birimleri gelmesi garanti edilmez ve bunlar gönderilme sırayla gelmesi garanti. Eksik, yinelenen ve sıra dışı veri birimi işlemek için UDP kullanan uygulamalar hazırlanması gerekir.  
  
 UDP kullanan bir veri birimi göndermek için gereksinim duyduğunuz hizmeti ve hizmetin iletişim kurmak için kullandığı UDP bağlantı noktası numarası barındırma ağ aygıtı ağ adresini bilmeniz gerekir. Internet Atanmış Numaralar Yetkilisi (IANA) (www.iana.org/assignments/port-numbers bakın) ortak Hizmetleri için bağlantı noktası numaralarını tanımlar. IANA listede olmayan Hizmetleri bağlantı noktası numaraları 1024 65. 535'ı için aralığında olabilir.  
  
 Özel ağ adresleri, IP tabanlı ağlarda UDP yayın iletileri desteklemek için kullanılır. Aşağıdaki tartışma örnek olarak Internet'te kullanılan IP sürüm 4 Adres ailesi kullanır.  
  
 IP sürüm 4 adresleri 32 bit bir ağ adresi belirtmek için kullanın. Ağ maskesi 255.255.255.0 kullanarak C sınıfı adresleri için bu BITS dört sekizli ayrılır. Ondalık belirtildiğinde, dört sekizli 192.168.100.2 gibi bilinen noktalı dört gösterimini oluşturur. İlk iki sekizli (Bu örnekte 192.168) ağ numarası form, üçüncü sekizli (100) alt ağı tanımlar ve son sekizli (2) ana bilgisayar tanımlayıcısıdır.  
  
 Bir veya 255.255.255.255, bir IP adresi tüm bit düzeyi ayarını sınırlı yayın adresi oluşturur. UDP veri birimi bu adrese gönderdiği iletiyi yerel ağ kesimindeki herhangi bir ana sunar. Yönlendiriciler hiçbir zaman bu adrese gönderilen iletileri iletmek için yalnızca ağ kesimindeki ana yayın iletisi alırsınız.  
  
 Yayınları belirli kısımlarını bir ağ için ana bilgisayar tanımlayıcısı tüm bitleri ayarlayarak yönlendirilebilir. Örneğin, bir yayın 192.168.1 ile başlayan IP adresleri ile tanımlanan ağdaki tüm ana bilgisayarlara göndermek için 192.168.1.255 adresi kullanın.  
  
 Aşağıdaki kod örneğinde bir <xref:System.Net.Sockets.UdpClient> 192.168.1.255 11.000 bağlantı noktasında yönlendirme yapılan yayın adresine gönderilen UDP veri birimleri dinlemek için. İstemci bir ileti dizesi alır ve ileti konsola yazar.  
  
```vb  
Imports System  
Imports System.Net  
Imports System.Net.Sockets  
Imports System.Text  
  
Public Class UDPListener  
   Private Const listenPort As Integer = 11000  
  
   Private Shared Sub StartListener()  
      Dim done As Boolean = False  
      Dim listener As New UdpClient(listenPort)  
      Dim groupEP As New IPEndPoint(IPAddress.Any, listenPort)  
      Try  
         While Not done  
            Console.WriteLine("Waiting for broadcast")  
            Dim bytes As Byte() = listener.Receive(groupEP)  
            Console.WriteLine("Received broadcast from {0} :", _  
                groupEP.ToString())   
            Console.WriteLine( _  
                Encoding.ASCII.GetString(bytes, 0, bytes.Length))  
            Console.WriteLine()  
         End While  
      Catch e As Exception  
         Console.WriteLine(e.ToString())  
      Finally  
         listener.Close()  
      End Try  
   End Sub 'StartListener  
  
   Public Shared Function Main() As Integer  
      StartListener()  
      Return 0  
   End Function 'Main  
End Class 'UDPListener  
```  
  
```csharp  
using System;  
using System.Net;  
using System.Net.Sockets;  
using System.Text;  
  
public class UDPListener   
{  
    private const int listenPort = 11000;  
  
    private static void StartListener()   
    {  
        bool done = false;  
  
        UdpClient listener = new UdpClient(listenPort);  
        IPEndPoint groupEP = new IPEndPoint(IPAddress.Any,listenPort);  
  
        try   
        {  
            while (!done)   
            {  
                Console.WriteLine("Waiting for broadcast");  
                byte[] bytes = listener.Receive( ref groupEP);  
  
                Console.WriteLine("Received broadcast from {0} :\n {1}\n",  
                    groupEP.ToString(),  
                    Encoding.ASCII.GetString(bytes,0,bytes.Length));  
            }  
  
        }   
        catch (Exception e)   
        {  
            Console.WriteLine(e.ToString());  
        }  
        finally  
        {  
            listener.Close();  
        }  
    }  
  
    public static int Main()   
    {  
        StartListener();  
  
        return 0;  
    }  
}  
```  
  
 Aşağıdaki kod örneğinde bir <xref:System.Net.Sockets.UdpClient> bağlantı noktası 11.000 kullanarak yönlendirme yapılan yayın adresine için 192.168.1.255, UDP veri birimleri göndermek için. İstemci komut satırında belirtilen ileti dizesi gönderir.  
  
```vb  
Imports System  
Imports System.Net  
Imports System.Net.Sockets  
Imports System.Text  
  
Public Class Program  
  
    Overloads Public Shared Function Main(args() As [String]) As Integer  
      Dim s As New Socket(AddressFamily.InterNetwork, SocketType.Dgram,  
          ProtocolType.Udp)  
      Dim broadcast As IPAddress = IPAddress.Parse("192.168.1.255")  
      Dim sendbuf As Byte() = Encoding.ASCII.GetBytes(args(0))  
      Dim ep As New IPEndPoint(broadcast, 11000)  
      s.SendTo(sendbuf, ep)  
      Console.WriteLine("Message sent to the broadcast address")  
   End Function 'Main  
End Class   
```  
  
```csharp  
using System;  
using System.Net;  
using System.Net.Sockets;  
using System.Text;  
  
class Program   
{  
    static void Main(string[] args)   
    {  
        Socket s = new Socket(AddressFamily.InterNetwork, SocketType.Dgram,  
            ProtocolType.Udp);  
  
        IPAddress broadcast = IPAddress.Parse("192.168.1.255");  
  
        byte[] sendbuf = Encoding.ASCII.GetBytes(args[0]);  
        IPEndPoint ep = new IPEndPoint(broadcast, 11000);  
  
        s.SendTo(sendbuf, ep);  
  
        Console.WriteLine("Message sent to the broadcast address");  
    }  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Net.Sockets.UdpClient>  
 <xref:System.Net.IPAddress>  
 
