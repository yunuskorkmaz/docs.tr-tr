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
ms.openlocfilehash: 477095ada6e44f66cbc60cd80375da9a87f38e39
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180612"
---
# <a name="using-udp-services"></a>UDP Hizmetleri Kullanma
Sınıf <xref:System.Net.Sockets.UdpClient> UDP kullanarak ağ hizmetleri ile iletişim kurar. <xref:System.Net.Sockets.UdpClient> Sınıfın özellikleri ve yöntemleri UDP kullanarak <xref:System.Net.Sockets.Socket> veri istemek ve almak için oluşturma ayrıntılarını özetler.

Kullanıcı Datagram Protokolü (UDP), uzak bir ana bilgisayara veri sağlamak için en iyi çabayı gösteren basit bir protokoldür. Ancak, UDP protokolü bağlantısız bir protokol olduğundan, uzak uç noktasına gönderilen UDP verigramlarının gelmesi garanti edilmez ve gönderildikleri sırayla ulaşmaları garanti edilmez. UDP kullanan uygulamalar eksik, yinelenen ve sıra dışı veri gramlarını işlemek için hazırlanmalıdır.

UDP kullanarak bir veri gramı göndermek için, gereksinim duyduğunuz hizmeti barındıran ağ aygıtının ağ adresini ve hizmetin iletişim kurmak için kullandığı UDP bağlantı noktası numarasını bilmeniz gerekir. Internet Atanmış Sayılar Yetkilisi (Iana), ortak hizmetler için bağlantı noktası numaralarını tanımlar (bkz. [Hizmet Adı ve Taşıma Protokolü Bağlantı Noktası Numarası Kayıt Defteri).](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml) Iana listesinde olmayan hizmetlerin bağlantı noktası numaraları 1.024 ile 65.535 arasında olabilir.

ÖZEL ağ adresleri, IP tabanlı ağlardaki UDP yayın iletilerini desteklemek için kullanılır. Aşağıdaki tartışma, Internet'te kullanılan IP sürüm 4 adresi ailesini örnek olarak kullanır.

IP sürüm 4 adresleri bir ağ adresi belirtmek için 32 bit kullanır. 255.255.255.0 netmask kullanarak C sınıfı adresler için bu bitler dört sekizliye ayrılır. Ondalık olarak ifade edildiğinde, dört sekizli 192.168.100.2 gibi tanıdık noktalı dörtlü gösterimi oluşturur. İlk iki sekizli (bu örnekte 192.168) ağ numarasını oluşturur, üçüncü sekizli (100) alt ağı tanımlar ve son sekizli (2) ana bilgisayar tanımlayıcısIdır.

Bir IP adresinin tüm bitlerini bir veya 255.255.255.255 olarak ayarlamak sınırlı yayın adresini oluşturur. Bu adrese bir UDP veri gramı göndermek, iletiyi yerel ağ segmentindeki herhangi bir ana bilgisayara gönderir. Yönlendiriciler bu adrese gönderilen iletileri hiçbir zaman iletmediğinden, yayın iletisini yalnızca ağ segmentindeki ana bilgisayarlar alır.

Yayınlar, ana bilgisayar tanımlayıcısının tüm bitlerini ayarlayarak ağın belirli bölümlerine yönlendirilebilir. Örneğin, 192.168.1 ile başlayan IP adresleri tarafından tanımlanan ağdaki tüm ana bilgisayarlara yayın göndermek için 192.168.1.255 adresini kullanın.

Aşağıdaki kod örneği, <xref:System.Net.Sockets.UdpClient> bağlantı noktası 11.000'deki UDP verigramlarını dinlemek için bir örnek kullanır. İstemci bir ileti dizesi alır ve iletiyi konsola yazar.

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

Aşağıdaki kod örneği, <xref:System.Net.Sockets.Socket> 11.000 no'lu bağlantı noktasını kullanarak UDP veri gramlarını yönlendirilmiş yayın adresi 192.168.1.255'e göndermek için kullanılır. İstemci komut satırında belirtilen ileti dizesini gönderir.

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
