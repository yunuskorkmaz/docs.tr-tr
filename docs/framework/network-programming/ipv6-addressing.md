---
title: IPv6 adresi
ms.date: 03/30/2017
helpviewer_keywords:
- Internet Protocol version 6, addresses in
- Neighbor Discovery
- IPv6, enabling
- IPv6, mobility and
- Internet Protocol version 6, anycast addresses
- IPv6, Neighbor Discovery
- Internet Protocol version 6, auto-configuring
- Internet Protocol version 6, enabling
- IPv6, unicast addresses
- IPv6, auto-configuring
- Internet Protocol version 6, routing
- IPv6, RFC documents
- IPv6, routing
- Internet Protocol version 6, disabling
- Internet Protocol version 6, unicast addresses
- IPv6, multicast addresses
- Internet Protocol version 6, mobility and
- Internet Protocol version 6, RFC documents
- Internet Protocol version 6, Neighbor Discovery
- IPv6, anycast addresses
- Internet Protocol version 6, multicast addresses
- IPv6, addresses in
- IPv6, disabling
ms.assetid: 20a104ae-1649-4649-a005-531a5cf74c93
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 532928118df9784198eada6f6a2f1e7a1b808ee9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="ipv6-addressing"></a>IPv6 adresi
Internet Protokolü sürüm 6 (IPv6), 128 bit uzunluğunda adresleridir. Tek bir tür büyük adres alanı için kullanılabilir adresler bulunan Internet'in topoloji yansıtacak Yönlendirme etki alanları bölümlere için nedenidir. Başka bir ağ bağdaştırıcısı (veya arabirimleri) cihazları ağa bağlamak adreslerini eşlemek için nedenidir. IPv6 ağ arabirimi düzeyinde ve aynı zamanda otomatik yapılandırma özellikleri içeren kendi en düşük düzeyde adresleri çözümleyecek şekilde devralınmış bir özellik sunar.  
  
## <a name="text-representation"></a>Metin gösterimi  
 IPv6 adreslerini metin dizesi olarak göstermek için kullanılan üç geleneksel formlar şunlardır:  
  
-   **İki nokta üst üste onaltılık form**. Tercih edilen form n:n:n:n:n:n:n:n budur. Her n adresinin sekiz 16 bit öğelerden birini onaltılı değerini temsil eder. Örneğin: `3FFE:FFFF:7654:FEDA:1245:BA98:3210:4562`.  
  
-   **Sıkıştırılmış form**. Adresi uzunluğu nedeniyle sıfır uzunluğunda bir dize içeren adresleri yaygındır. Bu adresler yazma işlemini basitleştirmek için hangi 0 blokları tek bitişik bir dizi temsil edilen bir çift iki nokta üst üste (:) simge sıkıştırılmış biçimi kullanın. Bu simgeyi bir adresi yalnızca bir kez görünebilir. Örneğin, çok noktaya yayın adresi `FFED:0:0:0:0:BA98:3210:4562` sıkıştırılmış biçimindedir `FFED::BA98:3210:4562`. Tek noktaya yayın adresi `3FFE:FFFF:0:0:8:800:20C4:0` sıkıştırılmış biçimindedir `3FFE:FFFF::8:800:20C4:0`. Geri döngü adresine `0:0:0:0:0:0:0:1` sıkıştırılmış biçimindedir `::`1. Belirtilmemiş adres `0:0:0:0:0:0:0:0` sıkıştırılmış biçimindedir `::`.  
  
-   **Form karma**. Bu form IPv4 ve IPv6 adresleri birleştirir. Bu durumda, adresi burada her n altı IPv6 yüksek düzey 16 bit adres öğelerini onaltılı değerini temsil eder ve bir IPv4 adresi ondalık değeri her d gösterir n:n:n:n:n:n:d.d.d.d biçimidir.  
  
## <a name="address-types"></a>Adres türleri  
 Belirli bir IPv6 adresi türü bitlerin adresi tanımlayın. Bu bitlerin içeren değişken uzunlukta alan bir biçim öneki (FP) adı verilir.  
  
 Bir IPv6 tek noktaya yayın adresi iki bölüme ayrılmıştır. Adres ön eki ilk bölümü içerir ve arabirim tanımlayıcısı ikinci bölümü içerir. Bir IPv6 adresi/öneki bileşimi express için kısa bir yol şu şekildedir: IPv6 adresi/önek uzunluğu.  
  
 64 bitlik bir önek ile adresinin bir örnek verilmiştir.  
  
 `3FFE:FFFF:0:CD30:0:0:0:0/64`.  
  
 Bu örnekte öneki `3FFE:FFFF:0:CD30`. Adres de sıkıştırılmış biçimde, olarak yazılabilir `3FFE:FFFF:0:CD30::/64`.  
  
 IPv6 aşağıdaki adresi türlerini tanımlar:  
  
-   **Tek noktaya yayın adresi**. Tek bir arabirim için tanımlayıcı. Bu adrese gönderilen bir paket için tanımlanan arabirimi teslim edilir. Tek noktaya yayın adreslerini çok noktaya yayın adreslerini yüksek düzey sekizli değerini ayırt edilir. Çok noktaya yayın adreslerini yüksek düzey sekizli FF onaltılı değerini alır. Bu sekizli için başka bir değer tek noktaya yayın adresi tanımlar. Tek noktaya yayın adreslerini farklı türleri şunlardır:  
  
    -   **Bağlantı-yerel adresleri**. Bu adresler üzerinde tek bir bağlantıya kullanılır ve aşağıdaki biçime sahiptir: FE80::*InterfaceId*. Bağlantı-yerel adresleri hiçbir yönlendiricilerdir sunmak veya adres otomatik yapılandırması, komşu bulma için bir bağlantı üzerindeki düğümler arasında kullanılır. Bağlantı-yerel adresi başlangıç derecede ve sistemi henüz büyük kapsam adreslerini almadığında kullanılır.  
  
    -   **Site-yerel adresleri**. Bu adresler tek bir sitede kullanılan ve aşağıdaki biçime sahiptir: FEC0::*SubnetID*:*InterfaceId*. Site-yerel adresleri genel bir önek gerek kalmadan bir site içinde ele almak için kullanılır.  
  
    -   **Genel IPv6 tek noktaya yayın adreslerini**. Bu adresleri Internet üzerinden kullanılabilir ve aşağıdaki biçime sahiptir: 010 (FP, 3 BITS) TLA Kimliği (13 BITS) NLA Kimliği (24 bit) SLA kimliği (16 bit) (8 bit) ayrılmış *InterfaceId* (64 bit).  
  
-   **Çok noktaya yayın adresi**. (Genellikle farklı düğümlerine ait) arabirimleri kümesi için bir tanımlayıcı. Bu adrese gönderilen bir paket adres tarafından tanımlanan tüm arabirimler için teslim edilir. Çok noktaya yayın adresi türleri yayın IPv4 adresleri yerini alır.  
  
-   **Her noktaya yayın adresi**. (Genellikle farklı düğümlerine ait) arabirimleri kümesi için bir tanımlayıcı. Bu adrese gönderilen bir paket adres tarafından tanımlanan yalnızca bir arabirim için teslim edilir. Bu en yakın yönlendirme ölçümleri tarafından tanımlandığı gibi arabirimidir. Her noktaya yayın adreslerini tek noktaya yayın adres alanından alınır ve sözdizimsel olarak ayrılabilen değildir. Adresli arabirimi yapılandırmasına yönelik bir işlevi olarak tek noktaya yayın ve her noktaya yayın adreslerini arasında ayrım gerçekleştirir.  
  
 Genel olarak, bir düğüm her zaman bir bağlantı-yerel adresi vardır. Bir site-yerel adresi ve bir veya daha fazla genel adresleri olabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İnternet Protokolü Sürüm 6](../../../docs/framework/network-programming/internet-protocol-version-6.md)  
 [Yuvalar](../../../docs/framework/network-programming/sockets.md)
