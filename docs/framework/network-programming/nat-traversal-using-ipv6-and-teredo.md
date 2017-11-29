---
title: "NAT IPv6 ve Teredo kullanarak geçişi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 568cd245-3300-49ef-a995-d81bf845d961
caps.latest.revision: "6"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 466e3faed9b2877671ca265afdb613607b12f0de
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="nat-traversal-using-ipv6-and-teredo"></a>NAT IPv6 ve Teredo kullanarak geçişi
Ağ adresi çevirisi (NAT) geçişi için destek sağlayan geliştirmeler yapıldı. Bu değişiklikler, IPv6 ve Teredo kullanmak için tasarlanmıştır ancak de teknolojileri tünel diğer IP uygulanabilir. Bu geliştirmeler sınıflarda etkileyen <xref:System.Net> ve ilgili ad alanları.  
  
 Bu değişiklikler IP teknolojileri tünel kullanmayı planlıyorsanız istemci ve sunucu uygulamaları etkileyebilir.  
  
 NAT geçişi desteklemek için değişiklikler yalnızca .NET Framework sürüm 4 kullanan uygulamalar için kullanılabilir. Bu özellikler, .NET Framework'ün önceki sürümlerinde kullanılamaz.  
  
## <a name="overview"></a>Genel Bakış  
 Internet Protokolü sürüm 4 (IPv4) bir IPv4 adresi 32 bit uzunluğunda tanımlanır. Sonuç olarak, IPv4 yaklaşık 4 milyar benzersiz IP adreslerini destekler (2 ^ 32). Bilgisayarları ve ağ aygıtları 1990'ların genişletilmiş Internet'te sayısı IPv4 adres alanı sınırları belirgin hale geldi.  
  
 Çok sayıda özel IP temsil etmek tek benzersiz bir ortak IP adresi izin vermek için NAT dağıtmak için açıldı IPv4 ömrü genişletmek için kullanılan birkaç teknikleri birini adresleri (özel Intranet). NAT cihazının arkasında özel IP adresleri tek genel IPv4 adresi paylaşır. NAT cihazının adanmış bir donanımsal cihaz (bir ucuz kablosuz erişim noktası ve yönlendirici, örneğin) ya da NAT sağlamak için bir hizmeti çalıştıran bir bilgisayar olabilir Bir aygıt veya hizmeti bu ortak IP adresi için ortak Internet ve özel Intranet arasında IP ağ paketlerinin çevirir.  
  
 Bu düzen de Internet üzerindeki diğer IP adresleri (genellikle sunucuları) istekleri göndermek özel Intranet üzerinde çalışan istemci uygulamalar için çalışır. Yanıtın gönderileceği yeri bildiği bir yanıt döndürdü NAT cihazı veya sunucu, istemci istekleri eşleme bunu tutabilirsiniz. Ancak bu düzeni istediğiniz hizmetleri sağlamak, paketlerini dinleme ve yanıt özel intranet NAT cihazının arkasında çalışan uygulamalar için sorunlar doğurur. Bu durum özellikle eşler arası uygulamaları için geçerlidir.  
  
 IPv6 protokolü, bir IPv4 adresi 128 bit uzunluğunda tanımlanır. Sonuç olarak, bir çok büyük IP adresi alanı 3.2 x 10 IPv6'yı destekleyen ^ 38 benzersiz adresler (2 ^ 128). Bu boyutta bir adres alanıyla benzersiz bir adresi verilecek Internet'e bağlı her bir aygıtı mümkündür. Ancak sorunları vardır. Büyük bir dünya hala yalnızca IPv4 kullanıyor. Özellikle, mevcut yönlendiriciler ve küçük şirketler, kuruluşlar ve ekleyebileceği tarafından kullanılan kablosuz erişim noktaları çoğu IPv6 desteklemez. Ayrıca bu müşterilerin hizmet bazı Internet hizmet sağlayıcıları desteklemiyor ya da IPv6 desteği yapılandırılmadı.  
  
 Birden fazla IPv6 geçiş teknolojileri, IPv4 paketinin tünel IPv6 adresleri için geliştirilmiştir. Teredo IPv6 ana IP4 ağları diğer IPv6 ağları ulaşmak için geçmesi gereken zaman, tek noktaya yayın IPv6 trafiği için adres ataması ve ana otomatik tünel sağlayan tünelleri ve 6to4, ISATAP, bu teknolojileri içerir. IPv6 paketlerini IPv4 paketleri tünel gönderilir. Bir NAT cihazı üzerinden IPv6 adresleri için NAT geçişi sağlayan birkaç tünel teknikleri kullanılır.  
  
 Teredo IPv4 ağları için IPv6 bağlantısı sunan IPv6 geçiş teknolojileri biridir. Teredo RFC Internet Engineering Task Force (IETF) tarafından yayımlanan 4380 belgelenmiştir. Windows XP SP2 ve daha sonra bir genel IPv6 adresi aralığı 2001:0 sağlayan sanal bir Teredo bağdaştırıcı için destek sağlayabilirsiniz:: / 32. Şu IPv6 adresi Internet'ten gelen bağlantıları dinlemek için kullanılan ve dinleme hizmetine bağlanmak istemezseniz IPv6 etkin istemciler için sağlanabilir. Bu uygulama yalnızca IPv6 Teredo adresini kullanarak bağlanabilmesi bu yana bir bilgisayarı bir NAT cihazının arkasında adres konusunda kaygı bir uygulamanın boşaltır.  
  
## <a name="enhancements-to-support-nat-traversal-and-teredo"></a>Destek NAT geçişi ve Teredo geliştirmeleri  
 Geliştirmeleri eklenmiştir <xref:System.Net>, <xref:System.Net.NetworkInformation>, ve <xref:System.Net.Sockets> IPv6 ve Teredo kullanarak NAT geçişi desteklemek için ad alanları.  
  
 Çeşitli yöntemler eklenir <xref:System.Net.NetworkInformation.IPGlobalProperties?displayProperty=nameWithType> tek noktaya yayın listesi konakta IP adreslerini almak için sınıf. <xref:System.Net.NetworkInformation.IPGlobalProperties.BeginGetUnicastAddresses%2A> Yöntemi yerel bilgisayarda kararlı tek noktaya yayın IP adresi tablosu almak için zaman uyumsuz isteği başlar. <xref:System.Net.NetworkInformation.IPGlobalProperties.EndGetUnicastAddresses%2A> Yöntemi yerel bilgisayarda kararlı tek noktaya yayın IP adresi tablosu almak için bekleyen bir zaman uyumsuz istek sona erer. <xref:System.Net.NetworkInformation.IPGlobalProperties.GetUnicastAddresses%2A> Yöntemdir adres tablosunu gerekirse kararlı hale gelinceye kadar bekleyen yerel bilgisayarda kararlı tek noktaya yayın IP adresi tablosu almak için zaman uyumlu bir istek.  
  
 <xref:System.Net.IPAddress.IsIPv6Teredo%2A?displayProperty=nameWithType> Özelliği, belirlemek için kullanılabilir bir <xref:System.Net.IPAddress> bir IPv6 Teredo adres.  
  
 Bu yeni kullanarak <xref:System.Net.NetworkInformation.IPGlobalProperties> sınıfı yöntemlerinin birlikte <xref:System.Net.IPAddress.IsIPv6Teredo%2A> özelliği, bir Teredo adresi kolayca bulmak uygulama izin verir. Uygulamanın normal olarak, yalnızca uzak uygulamalar için bu bilgileri halindeyse yerel Teredo adresini bilmeniz gerekiyor. Örneğin, bir eşler arası uygulaması tüm kendi IPv6 adreslerini, sonra bunları başkalarına iletmek bir matchmaking sunucusuna eşlere doğrudan iletişim sağlamak için gönderebilir.  
  
 Bir uygulama üzerinde dinleme onun dinleme hizmeti normal şekilde ayarlamanız gerekir <xref:System.Net.IPAddress.IPv6Any?displayProperty=nameWithType> yerine yerel Teredo adres. Bu nedenle bir uzak istemci veya eş için dinleme hizmeti konak doğrudan bir IPv6 yolunun varsa, istemci veya eş IPv6 kullanarak doğrudan bağlanabilir ve Teredo Tünel paketlerini kullanmak zorunda kalmazsınız.  
  
 TCP uygulamalar için <xref:System.Net.Sockets.TcpListener?displayProperty=nameWithType> sınıfına sahip bir <xref:System.Net.Sockets.TcpListener.AllowNatTraversal%2A> NAT geçişi etkinleştirmek için yöntemi. UDP uygulamalar için <xref:System.Net.Sockets.UdpClient?displayProperty=nameWithType> sınıfına sahip bir <xref:System.Net.Sockets.UdpClient.AllowNatTraversal%2A> NAT geçişi etkinleştirmek için yöntemi.  
  
 Kullanan uygulamalar için <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> ve ilgili sınıfların <xref:System.Net.Sockets.Socket.GetSocketOption%2A> ve <xref:System.Net.Sockets.Socket.SetSocketOption%2A> yöntemleri ile kullanılabilir <xref:System.Net.Sockets.SocketOptionName.IPProtectionLevel?displayProperty=nameWithType> yuva sorgu etkinleştirmek ya da NAT geçişi devre dışı bırakmak için seçeneği.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Net.IPAddress.IsIPv6Teredo%2A?displayProperty=nameWithType>  
 <xref:System.Net.NetworkInformation.IPGlobalProperties.BeginGetUnicastAddresses%2A?displayProperty=nameWithType>  
 <xref:System.Net.NetworkInformation.IPGlobalProperties.EndGetUnicastAddresses%2A?displayProperty=nameWithType>  
 <xref:System.Net.NetworkInformation.IPGlobalProperties.GetUnicastAddresses%2A?displayProperty=nameWithType>  
 <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType>  
 <xref:System.Net.Sockets.Socket.SetIPProtectionLevel%2A?displayProperty=nameWithType>  
 <xref:System.Net.Sockets.TcpListener.AllowNatTraversal%2A?displayProperty=nameWithType>  
 <xref:System.Net.Sockets.UdpClient.AllowNatTraversal%2A?displayProperty=nameWithType>
