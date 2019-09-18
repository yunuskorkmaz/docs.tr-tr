---
title: IPv6 Adresleme
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
ms.openlocfilehash: 1bad43b96fc6f66724e5e40cdf0ae6d76b46d867
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71047847"
---
# <a name="ipv6-addressing"></a>IPv6 Adresleme

Internet Protokolü sürüm 6 ' da (IPv6), adresler 128 bit uzunluğundadır. Bu tür büyük bir adres alanının bir nedeni, kullanılabilir adreslerin Internet 'in topolojisini yansıtan bir yönlendirme etki alanı hiyerarşisine alt kümesini oluşturma. Diğer bir neden, cihazları ağa bağlayan ağ bağdaştırıcılarının (veya arabirimlerinin) adreslerini eşlemenize yöneliktir. IPv6, adresleri, ağ arabirimi düzeyinde olan ve ayrıca otomatik yapılandırma özelliklerine sahip olan en düşük düzeyde çözümlemek için devralınmış bir özellik sunar.

## <a name="text-representation"></a>Metin gösterimi

IPv6 adreslerini metin dizeleri olarak temsil etmek için kullanılan üç geleneksel form aşağıda verilmiştir:

- **Iki nokta üst üste onaltılık form**. Bu değer, n:n: n:n: n:n: n:n. Her n, adresin 8 16 bitlik öğelerinden birinin onaltılık değerini temsil eder. Örneğin: `3FFE:FFFF:7654:FEDA:1245:BA98:3210:4562`

- **Sıkıştırılmış form**. Adres uzunluğu nedeniyle, uzun bir sıfır dizesi içeren adresler olması yaygındır. Bu adresleri yazmayı basitleştirmek için, tek bir bitişik dizi 0 blobunun çift iki nokta simgesiyle temsil edildiği sıkıştırılmış formu kullanın (::). Bu simge, adreste yalnızca bir kez görünebilir. Örneğin, sıkıştırılmış `FFED::BA98:3210:4562`biçimdeki çok noktaya `FFED:0:0:0:0:BA98:3210:4562` yayın adresi. `3FFE:FFFF:0:0:8:800:20C4:0` Sıkıştırılmış`3FFE:FFFF::8:800:20C4:0`biçimdeki tek noktaya yayın adresi. Sıkıştırılmış biçimdeki geri `0:0:0:0:0:0:0:1` döngü adresi 1 ' `::`dir. `0:0:0:0:0:0:0:0` Sıkıştırılmış`::`biçimdeki belirtilmemiş adres.

- **Karışık form**. Bu form IPv4 ve IPv6 adreslerini birleştirir. Bu durumda, adres biçimi n:n: n:n: n:n: d. d. d. d olur, burada her n altı IPv6 yüksek sıralı 16 bit adres öğesinin onaltılı değerlerini temsil eder ve her d bir IPv4 adresinin ondalık değerini temsil eder.

## <a name="address-types"></a>Adres türleri

Adresteki önde gelen bit, belirli bir IPv6 adresi türünü tanımlar. Bu önde gelen bitleri içeren değişken uzunluklu alan, biçim öneki (FP) olarak adlandırılır.

IPv6 tek noktaya yayın adresi iki parçaya ayrılmıştır. İlk bölüm, adres önekini içerir ve ikinci bölüm arabirim tanımlayıcısını içerir. IPv6 adresi/ön ek bileşimini hızlı bir şekilde ifade etmenin kısa bir yolu şunlardır: IPv6 adresi/ön ek uzunluğu.

Aşağıda, 64 bit ön ekine sahip bir adres örneği verilmiştir.

`3FFE:FFFF:0:CD30:0:0:0:0/64`.

Bu örnekteki `3FFE:FFFF:0:CD30`ön ek. Adres Ayrıca, olarak `3FFE:FFFF:0:CD30::/64`sıkıştırılmış bir biçimde yazılabilir.

IPv6 aşağıdaki adres türlerini tanımlar:

- **Tek noktaya yayın adresi**. Tek bir arabirim için tanımlayıcı. Bu adrese gönderilen bir paket, tanımlanan arabirime teslim edilir. Tek noktaya yayın adresleri, çok noktaya yayın adreslerinden yüksek sıralı sekizli değerine göre ayırt edilir. Çok noktaya yayın adreslerinin yüksek sıralı sekizli, FF onaltılık değerine sahiptir. Bu sekizli için herhangi bir diğer değer bir tek noktaya yayın adresini tanımlar. Aşağıdakiler farklı tek noktaya yayın adresi türleridir:

  - **Bağlantı yerel adresleri**. Bu adresler tek bir bağlantıda kullanılır ve aşağıdaki biçime sahiptir: FE80::*InterfaceID*. Bağlantı yerel adresleri, bir bağlantı üzerindeki düğümler arasında otomatik adres yapılandırması, komşu bulma veya yönlendirici olmadığında kullanılır. Bir bağlantı yerel adresi birincil olarak başlangıçta ve sistem daha büyük kapsamın adreslerini henüz almış olmadığında kullanılır.

  - **Site-yerel adresler**. Bu adresler tek bir sitede kullanılır ve aşağıdaki biçime sahiptir: FEC0::*SubnetID*:*InterfaceID*. Site yerel adresleri, genel ön ek gereksinimi olmadan bir site içinde adresleme için kullanılır.

  - **Genel IPv6 tek noktaya yayın adresleri**. Bu adresler Internet üzerinden kullanılabilir ve aşağıdaki biçime sahiptir: 010 (FP, 3 bit) TLA KIMLIĞI (13 bit) ayrılmış (8 bit) NLA Kimliği (24 bit) SLA kimliği (16 bit) *InterfaceID* (64 bit).

- **Çok noktaya yayın adresi**. Bir arabirim kümesi için tanımlayıcı (genellikle farklı düğümlere ait). Bu adrese gönderilen bir paket, adres tarafından tanımlanan tüm arabirimlere dağıtılır. Çok noktaya yayın adres türleri IPv4 yayın adreslerinin yerini alır.

- **Her noktaya yayın adresi**. Bir arabirim kümesi için tanımlayıcı (genellikle farklı düğümlere ait). Bu adrese gönderilen bir paket, yalnızca adres tarafından tanımlanan bir arabirime dağıtılır. Bu, yönlendirme ölçümleri tarafından tanımlanan en yakın arabirimdir. Tek noktaya yayın adresleri tek noktaya yayın adres alanından alınır ve sözdizimsel olarak ayırt edilemez. Adreslenen arabirim, tek noktaya yayın ve tek noktaya yayın adresleri arasındaki ayrımı kendi yapılandırmasının bir işlevi olarak gerçekleştirir.

Genel olarak, bir düğümün her zaman bir bağlantı yerel adresi vardır. Bu, bir site yerel adresine ve bir veya daha fazla genel adrese sahip olabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [İnternet Protokolü Sürüm 6](internet-protocol-version-6.md)
- [Yuvalar](sockets.md)
