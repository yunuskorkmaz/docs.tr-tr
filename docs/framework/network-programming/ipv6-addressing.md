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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047847"
---
# <a name="ipv6-addressing"></a>IPv6 Adresleme

Internet Protokolü sürüm 6'da (IPv6) adresler 128 bit uzunluğundadır. Bu kadar büyük bir adres alanının bir nedeni, kullanılabilir adresleri Internet'in topolojisini yansıtan yönlendirme etki alanları hiyerarşisine bölmektir. Başka bir neden, aygıtları ağa bağlayan ağ bağdaştırıcılarının (veya arabirimlerin) adreslerini eşlemektir. IPv6, adresleri ağ arabirimi düzeyinde olan ve aynı zamanda otomatik yapılandırma özelliklerine sahip en düşük düzeyde çözümlemek için doğal bir yeteneğe sahiptir.

## <a name="text-representation"></a>Metin Gösterimi

IPv6 adreslerini metin dizeleri olarak temsil etmek için kullanılan üç geleneksel form şunlardır:

- **Kolon-hexadecimal formu**. This is the preferred form n:n:n:n:n:n:n:n. Her n, adresin sekiz 16 bitlik öğesinden birinin hexadecimal değerini temsil eder. Örneğin: `3FFE:FFFF:7654:FEDA:1245:BA98:3210:4562`.

- **Sıkıştırılmış form**. Adres uzunluğu nedeniyle, uzun bir sıfır dizesi içeren adreslere sahip olmak yaygındır. Bu adresleri yazmayı kolaylaştırmak için, 0 bloktan oluşan tek bir bitişik sıranın çift sütunlu bir simgeyle temsil edildiği sıkıştırılmış formu kullanın (::). Bu sembol bir adreste yalnızca bir kez görünebilir. Örneğin, sıkıştırılmış biçimdeki çok noktaya `FFED::BA98:3210:4562`yayın adresi. `FFED:0:0:0:0:BA98:3210:4562` Sıkıştırılmış biçimde `3FFE:FFFF:0:0:8:800:20C4:0` unicast `3FFE:FFFF::8:800:20C4:0`adresi . Sıkıştırılmış biçimde geri dönüş adresi `0:0:0:0:0:0:0:1` 1'dir. `::` Sıkıştırılmış biçimde belirtilmeyen `0:0:0:0:0:0:0:0` `::`adres .

- **Karışık form**. Bu form, IPv4 ve IPv6 adreslerini birleştirir. In this case, the address format is n:n:n:n:n:n:d.d.d.d, where each n represents the hexadecimal values of the six IPv6 high-order 16-bit address elements, and each d represents the decimal value of an IPv4 address.

## <a name="address-types"></a>Adres Türleri

Adresteki satır aralığı bitleri belirli IPv6 adres türünü tanımlar. Bu satır baş bitlerini içeren değişken uzunluktaki alana Biçim Öneki (FP) adı verilir.

Bir IPv6 unicast adresi iki bölüme ayrılmıştır. İlk bölüm adres önekini, ikinci bölüm ise arabirim tanımlayıcısını içerir. IPv6 adresi/öneki birleşimini ifade etmenin kısa bir yolu aşağıdaki gibidir: ipv6-address/önek uzunluğu.

Aşağıda, 64 bit önek olan bir adres örneği verilmiştir.

`3FFE:FFFF:0:CD30:0:0:0:0/64`.

Bu örnekteki önek `3FFE:FFFF:0:CD30`. Adres de sıkıştırılmış bir biçimde yazılabilir, gibi `3FFE:FFFF:0:CD30::/64`.

IPv6 aşağıdaki adres türlerini tanımlar:

- **Unicast adresi**. Tek bir arabirim için tanımlayıcı. Bu adrese gönderilen bir paket tanımlanan arabirime teslim edilir. Tek noktaya yayın adresleri, çok noktaya yayın adreslerinden yüksek sıralı sekizlinin değeriyle ayırt edilir. Çok noktaya yayın adreslerinin yüksek sıralı sekizlisi FF'nin heksadesimal değerine sahiptir. Bu sekizliiçin başka bir değer tek dökümlü bir adresi tanımlar. Aşağıdaki tek tek adresler farklı türleri şunlardır:

  - **Bağlantı yerel adresleri**. Bu adresler tek bir bağlantıda kullanılır ve aşağıdaki biçime sahiptir: FE80::*InterfaceID*. Otomatik adres yapılandırması, komşu bulma veya yönlendirici olmadığında bağlantıdaki düğümler arasında bağlantı yerel adresleri kullanılır. Bir bağlantı yerel adres öncelikle başlangıç ve sistem henüz daha büyük kapsamda adresleri elde değil kullanılır.

  - **Site yerel adresleri.** Bu adresler tek bir sitede kullanılır ve aşağıdaki biçime sahiptir: FEC0::*SubnetID*:*InterfaceID*. Site yerel adresleri, genel bir önek gerek kalmadan bir site içinde adresleme için kullanılır.

  - **Global IPv6 unicast adresleri.** Bu adresler Internet'te kullanılabilir ve aşağıdaki biçime sahiptir: 010(FP, 3 bit) TLA ID (13 bit) Ayrılmış (8 bit) NLA ID (24 bit) SLA ID (16 bit) *InterfaceID* (64 bit).

- **Çok noktaya yayın adresi.** Arabirim kümesi (genellikle farklı düğümlere ait) için bir tanımlayıcı. Bu adrese gönderilen bir paket, adres tarafından tanımlanan tüm arabirimlere teslim edilir. Çok noktaya yayın adresi türleri IPv4 yayın adreslerinin yerini alar.

- **Anycast adresi**. Arabirim kümesi (genellikle farklı düğümlere ait) için bir tanımlayıcı. Bu adrese gönderilen bir paket, adres tarafından tanımlanan yalnızca bir arabirime teslim edilir. Bu, yönlendirme ölçümleri ile tanımlanan en yakın arabirimdir. Herhangi bir döküm adresleri unicast adres alanından alınır ve sözdizimsel olarak ayırt edilemez. Adresli arabirim, yapılandırmasının bir işlevi olarak unicast ve anycast adresleri arasındaki ayrımı gerçekleştirir.

Genel olarak, bir düğümün her zaman bir bağlantı yerel adresi vardır. Bir site yerel adresi ve bir veya daha fazla genel adres olabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [İnternet Protokolü Sürüm 6](internet-protocol-version-6.md)
- [Yuvalar](sockets.md)
