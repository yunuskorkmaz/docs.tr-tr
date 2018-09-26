---
title: IPv6 adresleme
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
ms.openlocfilehash: 8c992a96f2fa8d55d1fe16c03922cc8dbb39451c
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47090006"
---
# <a name="ipv6-addressing"></a>IPv6 adresleme
Internet Protokolü sürüm 6 (IPv6), 128 bit uzunluğunda adresleridir. Kullanılabilir adresler Internet'in topolojisini yansıtmak Yönlendirme etki alanları bir hiyerarşiye alt bölümlere ayırmak için bu tür bir geniş adres alanı bir neden olmasıdır. Başka bir nedeni, cihazları ağa bağlanan adreslerini ağ bağdaştırıcıları (veya arabirimleri) eşlemektir. IPv6 adresleri ağ arabirimi düzeyinde olduğunu ve ayrıca otomatik yapılandırma özellikleri, düşük düzeyinde gidermek için doğal bir özellik sunar.  
  
## <a name="text-representation"></a>Metin gösterimi  
 Metin dizesi olarak IPv6 adresleri temsil etmek için kullanılan üç geleneksel forms şunlardır:  
  
-   **İki nokta üst üste onaltılık form**. Tercih edilen form n:n:n:n:n:n:n:n budur. Her n adresinin sekiz 16-bit öğelerden biri onaltılık değerini temsil eder. Örneğin: `3FFE:FFFF:7654:FEDA:1245:BA98:3210:4562`.  
  
-   **Sıkıştırılmış form**. Adresi uzunluğu nedeniyle sıfır uzunluğunda bir dize içeren adresler çok yaygındır. Bu adresler yazma basitleştirmek için 0 blokları tek bitişik bir dizi bir çift iki nokta üst üste (:) sembolü gösterilir, sıkıştırılmış biçimi kullanın. Bu simge, bir adres olarak yalnızca bir kez görünebilir. Örneğin, çok noktaya yayın adresi `FFED:0:0:0:0:BA98:3210:4562` sıkıştırılmış biçimindedir `FFED::BA98:3210:4562`. Tek noktaya yayın adresi `3FFE:FFFF:0:0:8:800:20C4:0` sıkıştırılmış biçimindedir `3FFE:FFFF::8:800:20C4:0`. Geri döngü adresine `0:0:0:0:0:0:0:1` sıkıştırılmış biçimindedir `::`1. Belirtilmemiş adres `0:0:0:0:0:0:0:0` sıkıştırılmış biçimindedir `::`.  
  
-   **Form karma**. Bu form, IPv4 ve IPv6 adresleri birleştirir. Bu durumda adresi burada her n altı IPv6 yüksek düzeyli 16-bit adresi öğe onaltılık değerlerini temsil eder ve her d bir IPv4 adresi ondalık değeri temsil eden n:n:n:n:n:n:d.d.d.d biçimidir.  
  
## <a name="address-types"></a>Adres türü  
 Önde gelen adresteki bit belirli bir IPv6 adresi türü tanımlar. Değişken uzunluklu alanın başındaki bu bitlerin içeren bir biçim öneki (FP) adı verilir.  
  
 IPv6 tek noktaya yayın adresi iki bölüme ayrılmıştır. İlk bölümü adres ön eki, ve ikinci bölümüyle arabirim tanımlayıcısını içerir. Bir IPv6 adresi/ön ekinin birleşimini ifade etmek için kısa bir yol şu şekildedir: IPv6 adresi/ön ek uzunluğu.  
  
 Bir 64-bit ön ekine sahip bir adres örneği verilmiştir.  
  
 `3FFE:FFFF:0:CD30:0:0:0:0/64`.  
  
 Bu örnekte ön ekidir `3FFE:FFFF:0:CD30`. Adresi de sıkıştırılmış bir biçimde olarak yazılabilir `3FFE:FFFF:0:CD30::/64`.  
  
 IPv6 aşağıdaki adresi türleri tanımlar:  
  
-   **Tek noktaya yayın adresi**. Tek bir arabirim için bir tanımlayıcı. Bu adrese gönderilen bir paket için tanımlanan arabirimi teslim edilir. Tek noktaya yayın adresi çok noktaya yayın adreslerini yüksek düzeyli sekizli değerini ayırt edilir. Çok noktaya yayın adreslerini yüksek düzeyli sekizli FF onaltılı değerine sahiptir. Bir tek noktaya yayın adresi bu sekizli için başka bir değer tanımlar. Tek noktaya yayın adreslerini farklı türleri şunlardır:  
  
    -   **Bağlantı-yerel adresleri**. Bu adresler üzerinde tek bir bağlantı kullanılır ve aşağıdaki biçime sahiptir: FE80::*InterfaceId*. Bağlantı-yerel adresleri hiçbir yönlendiricilerdir sunmak veya adres otomatik yapılandırması, komşu bulma için bir bağlantı üzerindeki düğümler arasında kullanılır. Bağlantı-yerel adresi, başlangıç derecede ve sistem henüz adresleri, geniş kapsam almadığında kullanılır.  
  
    -   **Site-yerel adresleri**. Bu adresler, tek bir sitede kullanılan ve aşağıdaki biçime sahiptir: FEC0::*Subnetıd*:*InterfaceId*. Site-yerel adresleri, genel bir önek gerek kalmadan bir site içinde ele almak için kullanılır.  
  
    -   **Genel IPv6 tek noktaya yayın adreslerini**. Bu adresler Internet üzerinden kullanılabilir ve aşağıdaki biçime sahiptir: 010 (FP, 3 BITS) TLA Kimliği (13 BITS) NLA Kimliği (24 bit) SLA kimliği (16 bit) (8 bit) ayrılmış *InterfaceId* (64 bit).  
  
-   **Çok noktaya yayın adresi**. Arabirimler (genellikle farklı düğümlere ait) kümesi için bir tanımlayıcı. Bu adrese gönderilen bir paket adres tarafından tanımlanan tüm arabirimleri gönderilir. Çok noktaya yayın adresi türleri yayın IPv4 adresleri yerini alır.  
  
-   **Her noktaya yayın adresi**. Arabirimler (genellikle farklı düğümlere ait) kümesi için bir tanımlayıcı. Bu adrese gönderilen bir paket, yalnızca bir arabirime adres tarafından tanımlanan teslim edilir. Bu en yakın yönlendirme ölçümleri tarafından tanımlandığı gibi arabirimidir. Anycast adreslerine tek noktaya yayın adres alanından alınır ve sözdizimsel olarak ayrılabilen değildir. Adresli arabirimi yapılandırmasını işlevi olarak tek noktaya yayın ve anycast adresleri arasında ayrım gerçekleştirir.  
  
 Genel olarak, bir düğüm her zaman bir bağlantı-yerel adresi vardır. Site-yerel adresi ve bir veya daha fazla genel adresi olabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İnternet Protokolü Sürüm 6](../../../docs/framework/network-programming/internet-protocol-version-6.md)  
 [Yuvalar](../../../docs/framework/network-programming/sockets.md)
