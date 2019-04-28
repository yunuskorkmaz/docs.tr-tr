---
title: IPv6 ve Teredo kullanarak NAT Geçişi
ms.date: 03/30/2017
ms.assetid: 568cd245-3300-49ef-a995-d81bf845d961
ms.openlocfilehash: f617dc8912091576727b90da1e9efb9ebd5f9bda
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61642184"
---
# <a name="nat-traversal-using-ipv6-and-teredo"></a>IPv6 ve Teredo kullanarak NAT Geçişi
Geliştirmeler ağ adresi çevirisi (NAT) geçişi için destek sağlayan yapıldı. Bu değişiklikler, IPv6 ve Teredo ile kullanılmak üzere tasarlanmıştır ancak ayrıca diğer IP teknolojileri tünel için geçerlidir. Bu geliştirmeler sınıflarda etkileyen <xref:System.Net> ve ilgili ad alanları.  
  
 Bu değişiklikler, IP teknolojileri tünel kullanmayı planlıyorsanız istemci ve sunucu uygulamaları etkileyebilir.  
  
 NAT geçişini desteklemek için değişiklikler yalnızca .NET Framework sürüm 4 kullanan uygulamalar için kullanılabilir. Bu özellikler, .NET Framework'ün önceki sürümlerinde kullanılamaz.  
  
## <a name="overview"></a>Genel Bakış  
 Internet Protokolü sürüm 4 (IPv4), bir IPv4 adresi 32 bit uzunluğunda tanımlanır. Sonuç olarak, IPv4 yaklaşık 4 milyarı aşan benzersiz IP adreslerini destekler (2 ^ 32). Bilgisayarları ve ağ cihazları 1990'ların genişletilmiş Internet üzerindeki sayısı arttıkça, IPv4 adres alanı sınırları belirgin hale geldi.  
  
 Çok sayıda özel IP temsil etmek bir tek benzersiz genel IP adreslerine izin verecek şekilde NAT'ı dağıtmak için yapılmış IPv4 ömrünü genişletmek için kullanılan birkaç tekniklerden birini (özel Intranet) adresler. NAT cihazının arkasında özel IP adresleri, tek bir ortak IPv4 adresi paylaşın. NAT cihazının (bir ucuz kablosuz erişim noktası ve yönlendirici, örneğin) bir adanmış donanım cihazı veya NAT sağlamak için bir hizmeti çalıştıran bir bilgisayar olabilir. Bir cihaz veya hizmete bu genel IP adresi için genel Internet ile özel Intranet arasında IP ağ paketlerinin çevirir.  
  
 Bu düzeni de Internet üzerindeki diğer IP adreslerine (genellikle sunucuları) isteklerini göndermek özel Intranet üzerinde çalışan istemci uygulamalar için çalışır. Yanıtın gönderileceği bildiği bir yanıt döndürüldüğünde NAT cihazı veya sunucu, istemci istekleri bir eşleme bunu tutabilirsiniz. Ancak, sorunları istediğiniz hizmetleri sağlamak, paketler için dinleme ve yanıt, özel intranet NAT cihazının arkasında çalışan uygulamalar için bu düzeni doğurur. Bu özellikle eşler arası uygulamalar için geçerlidir.  
  
 IPv6 protokolü, bir IPv4 adresi 128 bit uzunluğunda tanımlanır. Sonuç olarak, bir çok büyük bir IP adres alanı 3.2 x 10 IPv6 destekleyen ^ 38 benzersiz adresler (2 ^ 128). Bu boyuttaki bir adres alanı ile her cihazın benzersiz adresi verilmesi için Internet'e bağlı mümkündür. Ancak, sorunları vardır. Dünya çoğunu, yine de yalnızca IPv4 kullanıyor. Özellikle, birçok küçük şirketler, kuruluşlar ve hanenin tarafından kullanılan kablosuz erişim noktaları ve mevcut yönlendiricilerin IPv6 desteklemez. Ayrıca bu müşterilere bazı Internet hizmet sağlayıcıları desteklemeyen ya da IPv6 desteğini yapılandırılmadı.  
  
 Birden fazla IPv6 geçiş teknolojileri IPv4 tüneli IPv6 adresleri için geliştirilmiştir. 6to4, ISATAP, bu teknolojiler şunları içerir ve IPv6 ana IP4 ağları diğer IPv6 ağları ulaşmak için geçmesi gereken, tek noktaya yayın IPv6 trafiği için adres ataması ve ana otomatik tünel sağlamak Teredo tünel oluşturur. IPv6 paketlerini IPv4 paketleri tünel gönderilir. IPv6 adresleri için NAT geçişi bir NAT cihazı üzerinden izin veren birkaç tünel teknikleri kullanılır.  
  
 Teredo IPv4 ağları için IPv6 bağlantısı getiren IPv6 geçiş teknolojileri biridir. Teredo RFC Internet Engineering Task Force (IETF) tarafından yayınlanan 4380 belgelenmiştir. Windows XP SP2 ve daha sonra genel IPv6 adresi de Aralık 2001:0 sağlayan sanal bir Teredo bağdaştırıcı için destek sağlayabilirsiniz:: / 32. Şu IPv6 adresi, Internet'ten gelen bağlantıları için dinlemek için kullanılan ve dinleme hizmete bağlanmak istediğiniz IPv6 etkin istemciler için sağlanabilir. Bu uygulama yalnızca Teredo IPv6 adresini kullanarak bağlanabilir olduğundan, bir bilgisayara bir NAT cihazının arkasında adres konusunda endişelenmenize gerek uygulamanın serbest bırakır.  
  
## <a name="enhancements-to-support-nat-traversal-and-teredo"></a>Destek NAT geçişi ve Teredo geliştirmeleri  
 Geliştirmeler eklenmiştir <xref:System.Net>, <xref:System.Net.NetworkInformation>, ve <xref:System.Net.Sockets> IPv6 ve Teredo kullanan NAT geçişini desteklemek için ad alanları.  
  
 Çeşitli yöntemler eklenen <xref:System.Net.NetworkInformation.IPGlobalProperties?displayProperty=nameWithType> listesi tek noktaya yayın IP adreslerini konakta almak için sınıf. <xref:System.Net.NetworkInformation.IPGlobalProperties.BeginGetUnicastAddresses%2A> Yöntemi, yerel bilgisayarda kararlı tek noktaya yayın IP adres tablosu almak için zaman uyumsuz isteği başlar. <xref:System.Net.NetworkInformation.IPGlobalProperties.EndGetUnicastAddresses%2A> Yöntemi, yerel bilgisayarda kararlı tek noktaya yayın IP adres tablosu almak için bekleyen bir zaman uyumsuz istek sona erer. <xref:System.Net.NetworkInformation.IPGlobalProperties.GetUnicastAddresses%2A> Yöntemdir gerekirse adres tablosu kararlı hale gelinceye kadar bekleyen yerel bilgisayarda kararlı tek noktaya yayın IP adres tablosu almak için zaman uyumlu bir istek.  
  
 <xref:System.Net.IPAddress.IsIPv6Teredo%2A?displayProperty=nameWithType> Özelliği belirlemek için kullanılabilir bir <xref:System.Net.IPAddress> Teredo IPv6 adresidir.  
  
 Bu yeni kullanarak <xref:System.Net.NetworkInformation.IPGlobalProperties> sınıfı yöntemleri ile birlikte <xref:System.Net.IPAddress.IsIPv6Teredo%2A> özelliği bir Teredo adresi kolayca bulmak bir uygulama sağlar. Uygulamanın normal olarak, yalnızca uzak uygulamalar bu bilgileri halindeyse yerel Teredo adresini bilmeniz gerekiyor. Örneğin, bir eşler arası uygulama eşleri doğrudan iletişim sağlamak için tüm kendi IPv6 adreslerini sonra bunları başkalarına iletmek bir matchmaking sunucuya gönderebilir.  
  
 Bir uygulama normalde dinleyecek şekilde kendi dinleme hizmeti ayarlamalısınız <xref:System.Net.IPAddress.IPv6Any?displayProperty=nameWithType> yerine yerel bir Teredo adresi. Bu nedenle doğrudan bir IPv6 yolunun hizmet ana bilgisayarı için bir uzak istemci veya eş varsa, istemci veya eş IPv6 kullanarak doğrudan bağlanabilir ve Teredo Tünel paketleri kullanmak zorunda kalmazsınız.  
  
 TCP uygulamalar için <xref:System.Net.Sockets.TcpListener?displayProperty=nameWithType> sınıfında bir <xref:System.Net.Sockets.TcpListener.AllowNatTraversal%2A> NAT geçişi etkinleştirmek için yöntemi. UDP uygulamaları için <xref:System.Net.Sockets.UdpClient?displayProperty=nameWithType> sınıfında bir <xref:System.Net.Sockets.UdpClient.AllowNatTraversal%2A> NAT geçişi etkinleştirmek için yöntemi.  
  
 Kullanan uygulamalar için <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> ve ilişkili sınıflarının <xref:System.Net.Sockets.Socket.GetSocketOption%2A> ve <xref:System.Net.Sockets.Socket.SetSocketOption%2A> yöntemleri ile kullanılabilir <xref:System.Net.Sockets.SocketOptionName.IPProtectionLevel?displayProperty=nameWithType> yuva sorgu, etkinleştirme veya NAT geçişi devre dışı bırakmak için seçeneği.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Net.IPAddress.IsIPv6Teredo%2A?displayProperty=nameWithType>
- <xref:System.Net.NetworkInformation.IPGlobalProperties.BeginGetUnicastAddresses%2A?displayProperty=nameWithType>
- <xref:System.Net.NetworkInformation.IPGlobalProperties.EndGetUnicastAddresses%2A?displayProperty=nameWithType>
- <xref:System.Net.NetworkInformation.IPGlobalProperties.GetUnicastAddresses%2A?displayProperty=nameWithType>
- <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType>
- <xref:System.Net.Sockets.Socket.SetIPProtectionLevel%2A?displayProperty=nameWithType>
- <xref:System.Net.Sockets.TcpListener.AllowNatTraversal%2A?displayProperty=nameWithType>
- <xref:System.Net.Sockets.UdpClient.AllowNatTraversal%2A?displayProperty=nameWithType>
