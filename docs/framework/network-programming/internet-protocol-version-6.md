---
title: İnternet Protokolü Sürüm 6
ms.date: 03/30/2017
helpviewer_keywords:
- IPv6, improvements
- IPv4
- IPv6
- Internet Protocol version 6, improvements
- Internet Protocol version 6
ms.assetid: e6fa8ebd-010a-4c48-a5ec-a5102c53c06f
ms.openlocfilehash: 367db4fa4e585d6066009dbd1afacb154829319a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047871"
---
# <a name="internet-protocol-version-6"></a>İnternet Protokolü Sürüm 6
Internet Protokolü sürüm 6 (IPv6), Internet'in ağ katmanı için yeni bir standart protokol paketidir. IPv6, adres tükenmesi, güvenlik, otomatik yapılandırma, genişletilebilirlik vb. ile ilgili olarak Internet Protocol paketinin (IPv4 olarak da bilinir) geçerli sürümünün birçok sorununu çözmek için tasarlanmıştır. IPv6, eşler arası ve mobil uygulamalar da dahil olmak üzere yeni uygulama türlerini etkinleştirmek için Internet'in yeteneklerini genişletir. Geçerli IPv4 protokolünün ana konuları şunlardır:  
  
- Adres alanının hızla tükenmesi.  
  
     Bu, birden çok özel adresi tek bir genel IP adresiyle eşleyen Ağ Adresi Çevirmenlerinin (NAT' ler) kullanılmasına yol açmıştır. Bu mekanizma tarafından oluşturulan temel sorunlar, genel olarak işlenmek ve uçtan uca bağlantı eksikliğidir.  
  
- Hiyerarşi desteği eksikliği.  
  
     Doğası nda var olan önceden tanımlanmış sınıf organizasyonu nedeniyle, IPv4 gerçek hiyerarşik destekyoksundur. IP adreslerini ağ topolojisini gerçekten eşleyen bir şekilde yapılandırmak mümkün değildir. Bu önemli tasarım hatası, IPv4 paketlerini Internet'teki herhangi bir konuma teslim etmek için büyük yönlendirme tablolarına ihtiyaç yaratır.  
  
- Karmaşık ağ yapılandırması.  
  
     IPv4 ile adreslere statik olarak veya DHCP gibi bir yapılandırma protokolü kullanılarak atanmalıdır. İdeal bir durumda, ev sahipleri bir DHCP altyapısının yönetimine güvenmek zorunda kalmaz. Bunun yerine, bulundukları ağ kesimine göre kendilerini yapılandırabilirler.  
  
- Yerleşik kimlik doğrulama ve gizlilik eksikliği.  
  
     IPv4, değiştirilen verilerin kimlik doğrulamasını veya şifrelemesini sağlayan herhangi bir mekanizma için destek gerektirmez. Bu IPv6 ile değişir. Internet Protocol security (IPSec) bir IPv6 destek gereksinimidir.  
  
 Yeni bir protokol paketi aşağıdaki temel gereksinimleri karşılamalıdır:  
  
- Büyük ölçekli yönlendirme ve düşük yükü ile adresleme.  
  
- Çeşitli bağlantı durumları için otomatik yapılandırma.  
  
- Dahili kimlik doğrulama ve gizlilik.  
  
 Daha fazla bilgi için, [IPv6 Adresleme](ipv6-addressing.md), [IPv6 Yönlendirme](ipv6-routing.md), [IPv6 Otomatik Yapılandırma](ipv6-auto-configuration.md), [Etkinleştirme ve Devre Dışı Bırakma IPv6](enabling-and-disabling-ipv6.md), ve [Nasıl bakınız: IPv6 Desteği etkinleştirmek için Bilgisayar Yapılandırma Dosyasını değiştirin](how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).  
  
## <a name="references"></a>Başvurular  
 [İnternet Mühendisliği Görev Gücü (IETF)](https://www.ietf.org/) web sitesinde bulabileceğiniz seçilmiş RFC belgeleri aşağıda veda edilebilmelidir:  
  
- RFC 1287, Geleceğe Doğru İnternet Mimarisi.  
  
- RFC 1454, IP Sonraki Sürümü için Tekliflerin Karşılaştırılması.  
  
- RFC 2373, IP Sürüm 6 Adresleme Mimarisi.  
  
- RFC 2374, Bir IPv6 Toplayıcı Küresel Unicast Adres Biçimi.  
  
 [Ayrıca IP Sürüm 6 (IPv6)](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd379498%28v=ws.10%29)iPv6 ile ilgili bilgileri bulabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IPv6 Soketleri Örneği](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/ms180981%28v=vs.85%29)
- [Ağ Programlama Örnekleri](network-programming-samples.md)
- [Yuvalar](sockets.md)
