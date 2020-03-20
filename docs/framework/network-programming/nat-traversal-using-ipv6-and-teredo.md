---
title: IPv6 ve Teredo kullanarak NAT Geçişi
ms.date: 03/30/2017
ms.assetid: 568cd245-3300-49ef-a995-d81bf845d961
ms.openlocfilehash: f617dc8912091576727b90da1e9efb9ebd5f9bda
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "61642184"
---
# <a name="nat-traversal-using-ipv6-and-teredo"></a>IPv6 ve Teredo kullanarak NAT Geçişi
Ağ Adresi Çevirisi (NAT) geçişi için destek sağlayan geliştirmeler yapıldı. Bu değişiklikler IPv6 ve Teredo ile kullanılmak üzere tasarlanmıştır, ancak diğer IP tünel leme teknolojileri için de geçerlidir. Bu <xref:System.Net> geliştirmeler, ve ilgili ad alanlarındaki sınıfları etkiler.  
  
 Bu değişiklikler, IP tünelleme teknolojilerini kullanmayı planlayan istemci ve sunucu uygulamalarını etkileyebilir.  
  
 NAT geçişini destekleyen değişiklikler yalnızca .NET Framework sürüm 4'üni kullanan uygulamalar için kullanılabilir. Bu özellikler .NET Framework'ün önceki sürümlerinde kullanılamaz.  
  
## <a name="overview"></a>Genel Bakış  
 Internet Protokolü sürüm 4 (IPv4), Bir IPv4 adresini 32 bit uzunluğunda olarak tanımladı. Sonuç olarak, IPv4 yaklaşık 4 milyar benzersiz IP adresini destekler (2^32). 1990'larda Internet'teki bilgisayar ve ağ aygıtlarının sayısı arttıkça, IPv4 adres alanının sınırları belirginleşti.  
  
 IPv4'ün kullanım ömrünü uzatmak için kullanılan çeşitli tekniklerden biri, çok sayıda özel IP adresini (özel Intranet) temsil edecek tek bir benzersiz genel IP adresine izin vermek için NAT dağıtmak olmuştur. NAT aygıtının arkasındaki özel IP adresleri tek bir genel IPv4 adresini paylaşır. NAT aygıtı özel bir donanım aygıtı (örneğin ucuz bir Kablosuz Erişim Noktası ve yönlendirici) veya NAT sağlamak için bir hizmet çalıştıran bir bilgisayar olabilir. Bu genel IP adresiiçin bir aygıt veya hizmet, genel Internet ve özel Intranet arasındaki IP ağ paketlerini çevirir.  
  
 Bu şema, Internet'teki diğer IP adreslerine (genellikle sunuculara) istek gönderen özel Intranet'te çalışan istemci uygulamaları için iyi çalışır. NAT aygıtı veya sunucusu istemci isteklerinin eşlenesini tutabilir, böylece yanıt döndürüldüğünde yanıtı nereye göndereceğini bilir. Ancak bu şema, hizmet sağlamak, paketleri dinlemek ve yanıt vermek isteyen NAT aygıtının arkasındaki özel Intranet'te çalışan uygulamalar için sorun oluşturur. Bu, özellikle eşler arası uygulamalar için geçerlidir.  
  
 IPv6 protokolü bir IPv4 adresini 128 bit uzunluğunda olarak tanımlamıştır. Sonuç olarak, IPv6 3.2 x 10^38 benzersiz adresler (2 ^128) çok büyük bir IP adres alanı destekler. Bu boyuttaki bir adres alanı ile, Internet'e bağlı her cihaza benzersiz bir adres verilmesi mümkündür. Ama bazı sorunlar var. Dünyanın büyük bir kısmı hala sadece IPv4 kullanıyor. Özellikle, küçük şirketler, kuruluşlar ve haneler tarafından kullanılan mevcut yönlendiricilerin ve kablosuz erişim noktalarının çoğu IPv6'yı desteklemez. Ayrıca, bu müşterilere hizmet veren bazı Internet servis sağlayıcıları, IPv6 desteğini desteklemez veya yapılandırmamıştır.  
  
 IPv4 paketinde IPv6 adreslerini tünellemek için çeşitli IPv6 geçiş teknolojileri geliştirilmiştir. Bu teknolojiler arasında, IPv6 ana bilgisayarlarının diğer IPv6 ağlarına ulaşmak için IP4 ağlarından geçmesi gerektiğinde adres ataması ve tek döküm IPv6 trafiği için ana bilgisayarotomatik tünelleme sağlayan 6to4, ISATAP ve Teredo tünelleri yer almaktadır. IPv6 paketleri IPv4 paketleri olarak tünele gönderilir. Bir NAT aygıtı aracılığıyla IPv6 adresleri için NAT geçişine izin veren çeşitli tünel teknikleri kullanılmaktadır.  
  
 Teredo, IPv4 ağlarına IPv6 bağlantısı getiren IPv6 geçiş teknolojilerinden biridir. Teredo, Internet Engineering Task Force (IETF) tarafından yayınlanan RFC 4380 belgesine sahiptir. Windows XP SP2 ve daha sonra 2001:0:/32 aralığında genel bir IPv6 adresi sağlayabilir sanal bir Teredo bağdaştırıcı sı için destek sağlar. Bu IPv6 adresi, Internet'ten gelen bağlantıları dinlemek için kullanılabilir ve dinleme hizmetine bağlanmak isteyen IPv6 etkin istemcilere sağlanabilir. Bu, uygulama sadece IPv6 Teredo adresini kullanarak bağlanabildiği için, bir NAT aygıtının arkasındaki bilgisayara nasıl hitap edilebildiği konusunda endişelenmekten kurtarır.  
  
## <a name="enhancements-to-support-nat-traversal-and-teredo"></a>NAT Traversal ve Teredo'nun Desteklenmesine Yönelik Geliştirmeler  
 IPv6 ve <xref:System.Net> <xref:System.Net.NetworkInformation> <xref:System.Net.Sockets> Teredo kullanılarak NAT geçişini desteklemek için ,, ve ad alanlarına geliştirmeler eklenir.  
  
 Ana bilgisayardaki <xref:System.Net.NetworkInformation.IPGlobalProperties?displayProperty=nameWithType> tek döküm IP adreslerinin listesini almak için sınıfa çeşitli yöntemler eklenir. Yöntem, <xref:System.Net.NetworkInformation.IPGlobalProperties.BeginGetUnicastAddresses%2A> yerel bilgisayardaki kararlı tek döküm IP adres tablosunu almak için eşzamanlı bir istek başlatır. Yöntem, <xref:System.Net.NetworkInformation.IPGlobalProperties.EndGetUnicastAddresses%2A> yerel bilgisayardaki kararlı tek döküm IP adres tablosunu almak için bekleyen bir eşzamanlı isteği sona erdirir. Yöntem, <xref:System.Net.NetworkInformation.IPGlobalProperties.GetUnicastAddresses%2A> gerekirse adres tablosu stabilize olana kadar bekleyen, yerel bilgisayarda kararlı unicast IP adres tablosu almak için eşzamanlı bir istektir.  
  
 Özellik, <xref:System.Net.IPAddress.IsIPv6Teredo%2A?displayProperty=nameWithType> bir <xref:System.Net.IPAddress> IPv6 Teredo adresi olup olmadığını belirlemek için kullanılabilir.  
  
 Özelliği ile <xref:System.Net.NetworkInformation.IPGlobalProperties> birlikte bu yeni sınıf yöntemleri kullanarak kolayca Teredo adresi bulmak için bir uygulama sağlar. <xref:System.Net.IPAddress.IsIPv6Teredo%2A> Bir uygulama normalde sadece uzak uygulamalara bu bilgileri iletişim ise yerel Teredo adresini bilmek gerekir. Örneğin, eşler arası bir uygulama, tüm IPv6 adreslerini bir çöpçatanlık sunucusuna gönderebilir ve bu da doğrudan iletişimi etkinleştirmek için bunları diğer eş arkadaşlarıyla iletebilir.  
  
 Bir uygulama normalde yerel Teredo <xref:System.Net.IPAddress.IPv6Any?displayProperty=nameWithType> adresi yerine dinlemek için dinleme hizmeti ayarlamalıdır. Bu nedenle, uzak bir istemci veya eşin dinleme hizmetinin ana bilgisayara doğrudan IPv6 rotası varsa, istemci veya eş doğrudan IPv6 kullanarak bağlanabilir ve paketleri tünele almak için Teredo'yu kullanmak zorunda kalmaz.  
  
 TCP uygulamaları için <xref:System.Net.Sockets.TcpListener?displayProperty=nameWithType> sınıfın NAT geçişini etkinleştirmek için bir <xref:System.Net.Sockets.TcpListener.AllowNatTraversal%2A> yöntemi vardır. UDP uygulamaları için <xref:System.Net.Sockets.UdpClient?displayProperty=nameWithType> sınıfın NAT geçişini etkinleştirmek için bir <xref:System.Net.Sockets.UdpClient.AllowNatTraversal%2A> yöntemi vardır.  
  
 <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> Ve ilgili sınıfları kullanan uygulamalarda, NAT geçişini sorgulamak, <xref:System.Net.Sockets.Socket.GetSocketOption%2A> <xref:System.Net.Sockets.Socket.SetSocketOption%2A> etkinleştirmek veya devre dışı etmek için <xref:System.Net.Sockets.SocketOptionName.IPProtectionLevel?displayProperty=nameWithType> soket seçeneğiyle yöntemler kullanılabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Net.IPAddress.IsIPv6Teredo%2A?displayProperty=nameWithType>
- <xref:System.Net.NetworkInformation.IPGlobalProperties.BeginGetUnicastAddresses%2A?displayProperty=nameWithType>
- <xref:System.Net.NetworkInformation.IPGlobalProperties.EndGetUnicastAddresses%2A?displayProperty=nameWithType>
- <xref:System.Net.NetworkInformation.IPGlobalProperties.GetUnicastAddresses%2A?displayProperty=nameWithType>
- <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType>
- <xref:System.Net.Sockets.Socket.SetIPProtectionLevel%2A?displayProperty=nameWithType>
- <xref:System.Net.Sockets.TcpListener.AllowNatTraversal%2A?displayProperty=nameWithType>
- <xref:System.Net.Sockets.UdpClient.AllowNatTraversal%2A?displayProperty=nameWithType>
