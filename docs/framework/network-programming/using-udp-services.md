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
ms.openlocfilehash: 8aabd71a841af2b01c644d52806f213ca9c92ec2
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/08/2018
ms.locfileid: "48873183"
---
# <a name="using-udp-services"></a>UDP Hizmetleri kullanma
<xref:System.Net.Sockets.UdpClient> Sınıfı UDP kullanarak Ağ Hizmetleri ile iletişim kurar. Özellikleri ve yöntemleri <xref:System.Net.Sockets.UdpClient> oluşturma ayrıntıları soyut sınıf bir <xref:System.Net.Sockets.Socket> istemek ve UDP kullanarak verileri alma.  
  
 Kullanıcı Veri Birimi Protokolü (UDP), uzak bir konağa verileri sunmak için bir en iyi hale getiren basit bir protokoldür. Ancak, bağlantısız bir protokol UDP protokolünü olduğundan, uzak uç noktaya gönderdi UDP veri birimi ulşamasını garanti değil ya da, bunlar gönderildiği sırada ulşamasını garanti. UDP kullanan uygulamalar, eksik, yinelenen ve sıra dışı veri birimi işlemek için hazırlanması gerekir.  
  
 Bir veri biriminde UDP kullanarak göndermek için barındırma hizmeti ve hizmetin iletişim kurmak için kullandığı UDP bağlantı noktası numarasını ağ cihaz ağ adresini bilmeniz gerekir. Bağlantı noktası numaralarını (www.iana.org/assignments/port-numbers bakın) ortak Hizmetleri için Internet Atanmış Numaralar Yetkilisi (IANA) tanımlar. IANA listede olmayan Hizmetleri bağlantı noktası numaraları için 1024 65,535 aralığında olabilir.  
  
 Özel ağ adresleri, IP tabanlı ağlarda UDP yayın iletilerini desteklemek için kullanılır. Aşağıdaki tartışma örnek olarak Internet'te kullanılan IP sürüm 4 Adres ailesi kullanır.  
  
 IP sürüm 4 adresleri 32 bit bir ağ adresi belirtmek için kullanın. Bir ağ maskesi 255.255.255.0 kullanarak sınıfı C adres için bu bit dört sekizlik tabanda ayrılır. Ondalık olarak belirtildiğinde, dört sekizlik tabanda 192.168.100.2 gibi tanıdık dört noktalı gösterimde oluşturur. İlk iki sekizlik tabanda (Bu örnekte 192.168) ağ sayısı form, üçüncü sekizli (100) alt ağı tanımlar ve son sekizli (2) konak tanımlayıcısıdır.  
  
 Bir veya 255.255.255.255, tüm bit'leri bir IP adresi ayarlama sınırlı yayın adresini oluşturur. Bu adrese bir UDP veri birimi gönderme yerel ağ kesimindeki tüm Konaklara iletiyi teslim eder. Yönlendiriciler hiçbir zaman bu adrese gönderilen iletileri iletmek için yalnızca ağ kesimindeki ana yayın iletisi alırsınız.  
  
 Yayınları tüm bitlerinin ana tanımlayıcısının ayarlayarak bir ağ belirli kısımlarını yönlendirilebilir. Örneğin, bir yayın 192.168.1 ile başlangıç IP adresi ile tanımlanan ağdaki tüm konaklar göndermek üzere 192.168.1.255 aralığındaki adresi kullanın.  
  
 Aşağıdaki kod örneğinde bir <xref:System.Net.Sockets.UdpClient> yayın adresine 192.168.1.255 aralığındaki 11.000 numaralı bağlantı noktasında gönderilecek UDP veri birimi dinlemek için. İstemci, bir ileti dizesi alır ve ileti konsola yazar.  
  
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
  
 Aşağıdaki kod örneğinde bir <xref:System.Net.Sockets.UdpClient> 11.000 numaralı bağlantı noktasını kullanan yayın adresine için 192.168.1.255 aralığındaki, UDP veri birimi göndermek için. İstemci, komut satırında belirtilen ileti dizesi gönderir.  
  
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
 
