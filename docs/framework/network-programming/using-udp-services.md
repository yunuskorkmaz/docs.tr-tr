---
title: UDP Hizmetleri Kullanma
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
ms.openlocfilehash: 397c51501ac333d6df699064b3fe82920bc38152
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61788108"
---
# <a name="using-udp-services"></a>UDP Hizmetleri Kullanma
<xref:System.Net.Sockets.UdpClient> Sınıfı UDP kullanarak Ağ Hizmetleri ile iletişim kurar. Özellikleri ve yöntemleri <xref:System.Net.Sockets.UdpClient> oluşturma ayrıntıları soyut sınıf bir <xref:System.Net.Sockets.Socket> istemek ve UDP kullanarak verileri alma.

Kullanıcı Veri Birimi Protokolü (UDP), uzak bir konağa verileri sunmak için bir en iyi hale getiren basit bir protokoldür. Ancak, bağlantısız bir protokol UDP protokolünü olduğundan, uzak uç noktaya gönderdi UDP veri birimi ulşamasını garanti değil ya da, bunlar gönderildiği sırada ulşamasını garanti. UDP kullanan uygulamalar, eksik, yinelenen ve sıra dışı veri birimi işlemek için hazırlanması gerekir.

Bir veri biriminde UDP kullanarak göndermek için barındırma hizmeti ve hizmetin iletişim kurmak için kullandığı UDP bağlantı noktası numarasını ağ cihaz ağ adresini bilmeniz gerekir. Ortak Hizmetleri için bağlantı noktası numaralarını Internet Atanmış Numaralar Yetkilisi (IANA) tanımlar (bkz [hizmet adını ve Aktarım Protokolü bağlantı noktası numarasını kayıt defteri](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)). IANA listede olmayan Hizmetleri bağlantı noktası numaraları için 1024 65,535 aralığında olabilir.

Özel ağ adresleri, IP tabanlı ağlarda UDP yayın iletilerini desteklemek için kullanılır. Aşağıdaki tartışma örnek olarak Internet'te kullanılan IP sürüm 4 Adres ailesi kullanır.

IP sürüm 4 adresleri 32 bit bir ağ adresi belirtmek için kullanın. Bir ağ maskesi 255.255.255.0 kullanarak sınıfı C adres için bu bit dört sekizlik tabanda ayrılır. Ondalık olarak belirtildiğinde, dört sekizlik tabanda 192.168.100.2 gibi tanıdık dört noktalı gösterimde oluşturur. İlk iki sekizlik tabanda (Bu örnekte 192.168) ağ sayısı form, üçüncü sekizli (100) alt ağı tanımlar ve son sekizli (2) konak tanımlayıcısıdır.

Bir veya 255.255.255.255, tüm bit'leri bir IP adresi ayarlama sınırlı yayın adresini oluşturur. Bu adrese bir UDP veri birimi gönderme yerel ağ kesimindeki tüm Konaklara iletiyi teslim eder. Yönlendiriciler hiçbir zaman bu adrese gönderilen iletileri iletmek için yalnızca ağ kesimindeki ana yayın iletisi alırsınız.

Yayınları tüm bitlerinin ana tanımlayıcısının ayarlayarak bir ağ belirli kısımlarını yönlendirilebilir. Örneğin, bir yayın 192.168.1 ile başlangıç IP adresi ile tanımlanan ağdaki tüm konaklar göndermek üzere 192.168.1.255 aralığındaki adresi kullanın.

Aşağıdaki kod örneğinde bir <xref:System.Net.Sockets.UdpClient> UDP veri birimi 11.000 numaralı bağlantı noktasında dinleyecek şekilde. İstemci, bir ileti dizesi alır ve ileti konsola yazar.

```vb
Imports System.Net
Imports System.Net.Sockets
Imports System.Text

Public Class UDPListener
   Private Const listenPort As Integer = 11000
   
   Private Shared Sub StartListener()
      Dim listener As New UdpClient(listenPort)
      Dim groupEP As New IPEndPoint(IPAddress.Any, listenPort)
      Try
         While True
            Console.WriteLine("Waiting for broadcast")
            Dim bytes As Byte() = listener.Receive(groupEP)
            Console.WriteLine("Received broadcast from {0} :", groupEP)
            Console.WriteLine(Encoding.ASCII.GetString(bytes, 0, bytes.Length))
         End While
      Catch e As SocketException
         Console.WriteLine(e)
      Finally
         listener.Close()
      End Try
   End Sub 'StartListener
   
   Public Shared Sub Main()
      StartListener()
   End Sub 'Main
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
        UdpClient listener = new UdpClient(listenPort);
        IPEndPoint groupEP = new IPEndPoint(IPAddress.Any, listenPort);
        
        try
        {
            while (true)
            {
                Console.WriteLine("Waiting for broadcast");
                byte[] bytes = listener.Receive(ref groupEP);
                
                Console.WriteLine($"Received broadcast from {groupEP} :");
                Console.WriteLine($" {Encoding.ASCII.GetString(bytes, 0, bytes.Length)}");
            }
        }
        catch (SocketException e)
        {
            Console.WriteLine(e);
        }
        finally
        {
            listener.Close();
        }
    }
    
    public static void Main()
    {
        StartListener();
    }
}
```

Aşağıdaki kod örneğinde bir <xref:System.Net.Sockets.Socket> 11.000 numaralı bağlantı noktasını kullanan yayın adresine için 192.168.1.255 aralığındaki, UDP veri birimi göndermek için. İstemci, komut satırında belirtilen ileti dizesi gönderir.

```vb
Imports System.Net
Imports System.Net.Sockets
Imports System.Text

Public Class Program
    Public Shared Sub Main(args() As [String])
      Dim s As New Socket(AddressFamily.InterNetwork, SocketType.Dgram, ProtocolType.Udp)
      Dim broadcast As IPAddress = IPAddress.Parse("192.168.1.255")
      Dim sendbuf As Byte() = Encoding.ASCII.GetBytes(args(0))
      Dim ep As New IPEndPoint(broadcast, 11000)
      s.SendTo(sendbuf, ep)
      Console.WriteLine("Message sent to the broadcast address")
   End Sub 'Main
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
        Socket s = new Socket(AddressFamily.InterNetwork, SocketType.Dgram, ProtocolType.Udp);
        
        IPAddress broadcast = IPAddress.Parse("192.168.1.255");
        
        byte[] sendbuf = Encoding.ASCII.GetBytes(args[0]);
        IPEndPoint ep = new IPEndPoint(broadcast, 11000);
        
        s.SendTo(sendbuf, ep);
        
        Console.WriteLine("Message sent to the broadcast address");
    }
}
```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Net.Sockets.UdpClient>
- <xref:System.Net.IPAddress>
