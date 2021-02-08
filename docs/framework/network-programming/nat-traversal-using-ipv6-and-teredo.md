---
description: 'Hakkında daha fazla bilgi edinin: IPv6 ve Teredo kullanarak NAT geçişi'
title: IPv6 ve Teredo kullanarak NAT Geçişi
ms.date: 03/30/2017
ms.assetid: 568cd245-3300-49ef-a995-d81bf845d961
ms.openlocfilehash: 4ff7f273c01ef52f4d307cbd3e0698c5cc2ead4d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785750"
---
# <a name="nat-traversal-using-ipv6-and-teredo"></a>IPv6 ve Teredo kullanarak NAT Geçişi

Ağ adresi çevirisi (NAT) geçişi için destek sağlayan geliştirmeler yapılmıştır. Bu değişiklikler IPv6 ve Teredo ile kullanılmak üzere tasarlanmıştır, ancak diğer IP tünelleme teknolojileri için de geçerlidir. Bu geliştirmeler <xref:System.Net> ve ilgili ad alanlarındaki sınıfları etkiler.  
  
 Bu değişiklikler, IP tünel teknolojilerini kullanmayı planlayasağlayan istemci ve sunucu uygulamalarını etkileyebilir.  
  
 NAT geçişini desteklemeye yönelik değişiklikler yalnızca .NET Framework sürüm 4 kullanan uygulamalar için kullanılabilir. Bu özellikler .NET Framework önceki sürümlerinde kullanılamaz.  
  
## <a name="overview"></a>Genel Bakış  

 Internet Protokolü sürüm 4 (IPv4), bir IPv4 adresini 32 bit uzunluğunda olarak tanımladı. Sonuç olarak, IPv4 yaklaşık 4.000.000.000 benzersiz IP adresini (2 ^ 32) destekler. Internet üzerindeki bilgisayar ve ağ cihazlarının sayısı 1990s içinde genişletilir, IPv4 adres alanının sınırları görünür hale geldi.  
  
 IPv4 ömrünü uzatmak için kullanılan birkaç teknikten biri, tek bir benzersiz genel IP adresinin çok sayıda özel IP adresini (özel Intranet) göstermesini sağlamak için NAT dağıtmaktır. NAT cihazının arkasındaki özel IP adresleri tek genel IPv4 adresini paylaşır. NAT cihazı ayrılmış bir donanım cihazı (örneğin, pahalı bir kablosuz erişim noktası ve yönlendirici) veya NAT sağlamak üzere bir hizmet çalıştıran bir bilgisayar olabilir. Bu genel IP adresi için bir cihaz veya hizmet, IP ağ paketlerini genel Internet ile özel Intranet arasında çevirir.  
  
 Bu düzen, Internet üzerindeki diğer IP adreslerine (genellikle sunucular) istek gönderen özel Intranette çalışan istemci uygulamaları için iyi çalışır. NAT cihazı veya sunucusu, bir yanıt döndürüldüğünde yanıtı nereden göndereceğini öğrendiğinde, istemci istekleri eşlemesini tutabilir. Ancak bu şema, hizmet sağlamak, paketleri dinlemek ve yanıt vermek istediğiniz NAT cihazının arkasında özel Intranette çalışan uygulamalar için sorunlar doğurur. Bu durum özellikle eşler arası uygulamalar için de kullanılır.  
  
 IPv6 protokolü, 128 bit uzunluğunda bir IPv4 adresi tanımladı. Sonuç olarak, IPv6, 3,2 x 10 ^ 38 benzersiz adresi (2 ^ 128) olan büyük bir IP adresi alanını destekler. Bu boyuttaki bir adres alanı ile, Internet 'e bağlı her cihaza benzersiz bir adres verilme olasılığı vardır. Ancak sorunlar oluştu. Dünyanın çoğu hala yalnızca IPv4 kullanıyor. Özellikle, küçük şirketler, kuruluşlar ve birlikte tutma tarafından kullanılan mevcut yönlendiricilerin ve kablosuz erişim noktalarının çoğu IPv6 'Yı desteklemez. Ayrıca, bu müşterilere hizmet veren bazı Internet hizmet sağlayıcıları IPv6 için destek yapılandırmamakta veya yapılandırılmamış olabilir.  
  
 IPv4 paketindeki IPv6 adreslerini tünel için birkaç IPv6 geçiş teknolojisi geliştirilmiştir. Bu teknolojiler, IPv6 ana bilgisayarlarının diğer IPv6 ağlarına ulaşmak için ıP4 ağlarını çapraz bir şekilde geçmesi gerektiğinde, tek noktaya yayın IPv6 trafiği için adres atamasını ve konak-konak otomatik tünelini sağlayan 6to4, ıSATAP ve Teredo tünellerini içerir. IPv6 paketleri IPv4 paketleri olarak tünel gönderilir. Bir NAT cihazı aracılığıyla IPv6 adresleri için NAT çapraz geçişine izin veren çeşitli tünel oluşturma teknikleri kullanılmaktadır.  
  
 Teredo, IPv4 ağlarına IPv6 bağlantısı getiren IPv6 geçiş teknolojilerinden biridir. Teredo, Internet Mühendisliği görev gücü (IETF) tarafından yayımlanan RFC 4380 ' de belgelenmiştir. Windows XP SP2 ve üzeri, 2001:0::/32 aralığında ortak bir IPv6 adresi sağlayabilen bir sanal Teredo bağdaştırıcısı desteği sağlar. Bu IPv6 adresi Internet 'ten gelen bağlantıları dinlemek için kullanılabilir ve dinleme hizmetine bağlanmak isteyen IPv6 etkin istemcilerine temin edilebilir. Bu, uygulama bir NAT cihazının arkasında bir bilgisayarın nasıl ele alınacağını öğrenmeden bir uygulamayı serbest bırakır ve bu, uygulama yalnızca kendi IPv6 Teredo adresini kullanarak bağlanabilir.  
  
## <a name="enhancements-to-support-nat-traversal-and-teredo"></a>NAT geçişi ve Teredo desteği için geliştirmeler  

 <xref:System.Net> <xref:System.Net.NetworkInformation> <xref:System.Net.Sockets> IPv6 ve Teredo kullanılarak NAT çapraz geçişini desteklemek için, ve ad alanlarına geliştirmeler eklenir.  
  
 <xref:System.Net.NetworkInformation.IPGlobalProperties?displayProperty=nameWithType>Konaktaki tek noktaya yayın IP adreslerinin listesini almak için sınıfa çeşitli yöntemler eklenmiştir. <xref:System.Net.NetworkInformation.IPGlobalProperties.BeginGetUnicastAddresses%2A>Yöntemi, yerel bilgisayardaki kararlı tek noktaya yayın IP adresi tablosunu almak için zaman uyumsuz bir istek başlatır. <xref:System.Net.NetworkInformation.IPGlobalProperties.EndGetUnicastAddresses%2A>Yöntemi, yerel bilgisayardaki kararlı tek noktaya yayın IP adresi tablosunu almak için bekleyen bir zaman uyumsuz isteği sonlandırır. <xref:System.Net.NetworkInformation.IPGlobalProperties.GetUnicastAddresses%2A>Yöntemi, yerel bilgisayardaki kararlı tek noktaya yayın IP adresi tablosunu almak için zaman uyumlu bir istek olup, gerekirse adres tablosu sabitlene kadar bekler.  
  
 <xref:System.Net.IPAddress.IsIPv6Teredo%2A?displayProperty=nameWithType>Özelliği, bir IPv6 Teredo adresi olup olmadığını anlamak için kullanılabilir <xref:System.Net.IPAddress> .  
  
 Bu yeni <xref:System.Net.NetworkInformation.IPGlobalProperties> Sınıf yöntemlerinin özelliği ile birlikte kullanılması, <xref:System.Net.IPAddress.IsIPv6Teredo%2A> bir uygulamanın Teredo adresini kolayca bulmasına olanak tanır. Genellikle bir uygulamanın bu bilgileri uzak uygulamalarla haberleşmiş olması durumunda yalnızca yerel Teredo adresini bilmeleri gerekir. Örneğin, eşler arası bir uygulama, tüm IPv6 adreslerini, daha sonra doğrudan iletişimi etkinleştirmek için bunları başka bir eşe iletebilen bir eşleşme sunucusuna gönderebilir.  
  
 Bir uygulamanın normalde dinleme hizmetini <xref:System.Net.IPAddress.IPv6Any?displayProperty=nameWithType> Yerel Teredo adresi yerine dinlemesi için ayarlaması gerekir. Bu nedenle, uzak bir istemci veya eşin dinleme hizmetinin ana bilgisayarına doğrudan bir IPv6 yolu varsa, istemci veya eş IPv6 kullanarak doğrudan bağlanabilir ve paketleri tünel oluşturmak için Teredo kullanmak zorunda değildir.  
  
 TCP uygulamalarında, <xref:System.Net.Sockets.TcpListener?displayProperty=nameWithType> SıNıFıNıN <xref:System.Net.Sockets.TcpListener.AllowNatTraversal%2A> NAT çapraz geçişini etkinleştirme yöntemi vardır. UDP uygulamalarında, <xref:System.Net.Sockets.UdpClient?displayProperty=nameWithType> SıNıFıNıN <xref:System.Net.Sockets.UdpClient.AllowNatTraversal%2A> NAT çapraz geçişini etkinleştirme yöntemi vardır.  
  
 Ve ilgili sınıfları kullanan uygulamalar için, <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> <xref:System.Net.Sockets.Socket.GetSocketOption%2A> ve <xref:System.Net.Sockets.Socket.SetSocketOption%2A> yöntemleri, <xref:System.Net.Sockets.SocketOptionName.IPProtectionLevel?displayProperty=nameWithType> NAT geçişini sorgulamak, etkinleştirmek veya devre dışı bırakmak için yuva seçeneğiyle birlikte kullanılabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Net.IPAddress.IsIPv6Teredo%2A?displayProperty=nameWithType>
- <xref:System.Net.NetworkInformation.IPGlobalProperties.BeginGetUnicastAddresses%2A?displayProperty=nameWithType>
- <xref:System.Net.NetworkInformation.IPGlobalProperties.EndGetUnicastAddresses%2A?displayProperty=nameWithType>
- <xref:System.Net.NetworkInformation.IPGlobalProperties.GetUnicastAddresses%2A?displayProperty=nameWithType>
- <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType>
- <xref:System.Net.Sockets.Socket.SetIPProtectionLevel%2A?displayProperty=nameWithType>
- <xref:System.Net.Sockets.TcpListener.AllowNatTraversal%2A?displayProperty=nameWithType>
- <xref:System.Net.Sockets.UdpClient.AllowNatTraversal%2A?displayProperty=nameWithType>
