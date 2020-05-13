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
ms.openlocfilehash: 5ff40e8759b1732d4ad228b1414f96f9c37e5ac5
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209779"
---
# <a name="use-udp-services"></a>UDP hizmetlerini kullanma

<xref:System.Net.Sockets.UdpClient>Sınıfı, UDP kullanarak ağ hizmetleriyle iletişim kurar. Sınıfının özellikleri ve yöntemleri, <xref:System.Net.Sockets.UdpClient> <xref:System.Net.Sockets.Socket> UDP kullanarak veri istemek ve almak için oluşturma ayrıntılarını soyutlar.

Kullanıcı veri birimi Protokolü (UDP), uzak bir konağa veri teslim etmeyi en iyi şekilde kolaylaştıran bir basit protokoldür. Bununla birlikte, UDP protokolü bağlantısız bir protokol olduğundan, uzak uç noktaya gönderilen UDP veri birimlerinin gelmesi garanti edilmez, ne de gönderildikleri sırada gelmesi garanti edilir. UDP kullanan uygulamalar eksik, yinelenen ve dizi dışı datagramları işleyecek şekilde hazırlanmalıdır.

UDP kullanarak bir veri birimi göndermek için, ihtiyacınız olan hizmeti barındıran ağ cihazının ağ adresini ve hizmetin iletişim kurmak için kullandığı UDP bağlantı noktası numarasını bilmeniz gerekir. Internet atanmış numaralar yetkilisi (ıANA), ortak hizmetler için bağlantı noktası numaralarını tanımlar (bkz. [hizmet adı ve Aktarım Protokolü bağlantı noktası numarası kayıt defteri](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)). IANA listesinde bulunmayan hizmetler 1.024-65.535 aralığında bağlantı noktası numaralarına sahip olabilir.

Özel ağ adresleri IP tabanlı ağlardaki UDP yayın iletilerini desteklemek için kullanılır. Aşağıdaki tartışmada, Internet üzerinde kullanılan IP sürüm 4 adres ailesi bir örnek olarak kullanılmaktadır.

IP sürüm 4 adresleri bir ağ adresi belirtmek için 32 bit kullanır. 255.255.255.0 ağ maskesini kullanan sınıf C adresleri için, bu bitler dört sekizlik ile ayrılır. Ondalık olarak ifade edildiğinde, dört sekizli, 192.168.100.2 gibi tanıdık noktalı dörtlü gösterimi oluşturur. İlk iki sekizli (Bu örnekteki 192,168) ağ numarasını, üçüncü sekizli (100) alt ağı tanımlar ve son sekizli (2) konak tanımlayıcısıdır.

Bir IP adresinin tüm bitlerini bir veya 255.255.255.255 olarak ayarlamak, sınırlı yayın adresini oluşturur. Bu adrese bir UDP veri birimi gönderilmesi, iletiyi yerel ağ kesimindeki herhangi bir konağa gönderir. Yönlendiriciler bu adrese gönderilen iletileri hiçbir şekilde iletmediği için, yalnızca ağ kesimindeki konaklar yayın iletisini alır.

Yayınlar, ana bilgisayar tanımlayıcısının tüm bitlerini ayarlayarak bir ağın belirli bölümlerine yönlendirilebilir. Örneğin, 192.168.1 ile başlayan IP adresleri tarafından tanımlanan ağdaki tüm konaklara bir yayın göndermek için 192.168.1.255 aralığındaki adresini kullanın.

Aşağıdaki kod örneği, <xref:System.Net.Sockets.UdpClient> bağlantı noktası 11.000 ' DEKI UDP datagramları dinlemek için bir kullanır. İstemci bir ileti dizesi alır ve iletiyi konsola yazar.

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

Aşağıdaki kod örneği, <xref:System.Net.Sockets.Socket> 11.000 numaralı bağlantı noktasını kullanarak 192.168.1.255 aralığındaki yönlendirilmiş yayın ADRESINE UDP veri birimleri göndermek için bir kullanır. İstemci, komut satırında belirtilen ileti dizesini gönderir.

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
