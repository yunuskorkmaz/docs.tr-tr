---
title: İnternet Protokolü Sürüm 6
description: IPv6 protokolünü ve IPv4 'den farklı olduğunu öğrenin. .NET Framework uygulamalar IPv6 'yı destekler, ancak yapılandırma gerektirebilir.
ms.date: 03/30/2017
helpviewer_keywords:
- IPv6, improvements
- IPv4
- IPv6
- Internet Protocol version 6, improvements
- Internet Protocol version 6
ms.assetid: e6fa8ebd-010a-4c48-a5ec-a5102c53c06f
ms.openlocfilehash: c2b23705ae309436344513e54d6258e206d69da4
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90551471"
---
# <a name="internet-protocol-version-6"></a>İnternet Protokolü Sürüm 6
Internet Protokolü sürüm 6 (IPv6), Internet ağ katmanı için yeni bir standart protokoller paketidir. IPv6, Internet Protokolü paketi 'nin geçerli sürümünün (IPv4 olarak bilinir), aşalım, güvenlik, otomatik yapılandırma, genişletilebilirlik vb. gibi birçok sorununu çözmek için tasarlanmıştır. IPv6, eşler arası ve mobil uygulamalar da dahil olmak üzere yeni uygulama türlerini etkinleştirmek için Internet 'in yeteneklerini genişletir. Geçerli IPv4 protokolünün başlıca sorunları aşağıda verilmiştir:  
  
- Adres alanının hızlı bir şekilde çıkarılması.  
  
     Bu, birden çok özel adresi tek bir genel IP adresine eşleyen ağ adresi çeviricileri (NAT) kullanımına yol açmıştır. Bu mekanizma tarafından oluşturulan başlıca sorunlar, ek yükü ve uçtan uca bağlantının eksikliğinden oluşur.  
  
- Hiyerarşi desteğinin bulunmaması.  
  
     Devralınan önceden tanımlanmış sınıf kuruluşunda, IPv4 gerçek hiyerarşik desteğe sahip değildir. IP adreslerini gerçekten ağ topolojisini eşleyen bir şekilde yapılandırmak olanaksızdır. Bu önemli tasarım kusuru, Internet 'teki herhangi bir konuma IPv4 paketleri sunmaya yönelik büyük yönlendirme tablolarına yönelik ihtiyacı oluşturur.  
  
- Karmaşık ağ yapılandırması.  
  
     IPv4 ile adreslerin statik olarak atanması veya DHCP gibi bir yapılandırma Protokolü kullanılması gerekir. İdeal bir durumda, konaklar bir DHCP altyapısının yönetimine güvenmelidir. Bunun yerine kendilerini bulundukları ağ kesimine göre yapılandırabilirler.  
  
- Yerleşik kimlik doğrulaması ve gizlilik eksikliği yok.  
  
     IPv4, değiştirilen verilerin kimlik doğrulaması veya şifrelemesini sağlayan herhangi bir mekanizma için destek gerektirmez. Bu, IPv6 ile değiştirilir. Internet Protokolü güvenliği (IPSec) bir IPv6 destek gereksinimidir.  
  
 Yeni bir protokol paketinin aşağıdaki temel gereksinimleri karşılaması gerekir:  
  
- Düşük ek yüklerle büyük ölçekli yönlendirme ve adresleme.  
  
- Çeşitli bağlama durumları için otomatik yapılandırma.  
  
- Yerleşik kimlik doğrulaması ve gizlilik.  
  
 Daha fazla bilgi için bkz. [IPv6 adresleme](ipv6-addressing.md), [IPv6 yönlendirme](ipv6-routing.md), [IPv6 otomatik yapılandırma](ipv6-auto-configuration.md), [IPv6 'Yı etkinleştirme ve devre dışı bırakma](enabling-and-disabling-ipv6.md)ve [nasıl yapılır: IPv6 desteğini etkinleştirmek için bilgisayar yapılandırma dosyasını değiştirme](how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).  
  
## <a name="references"></a>Başvurular  
 Aşağıda, [Internet Mühendisliği görev gücü (IETF)](https://www.ietf.org/) Web SITESINDE bulabileceğiniz RFC belgelerinin seçildiği verilmiştir:  
  
- RFC 1287, gelecekteki Internet mimarisine doğru.  
  
- RFC 1454, IP 'nin sonraki sürümü için tekliflerin karşılaştırması.  
  
- RFC 2373, IP sürüm 6 Adresleme Mimarisi.  
  
- Bir IPv6 toplanabilir genel tek noktaya yayın adresi biçimi olan RFC 2374.  
  
 IPv6 ile ilgili bilgileri [IP sürüm 6 (IPv6)](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd379498(v=ws.10))üzerinde de bulabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IPv6 yuvaları örneği](/previous-versions/dotnet/netframework-3.0/ms180981(v=vs.85))
- [Ağ Programlama Örnekleri](network-programming-samples.md)
- [Yuvalar](sockets.md)
