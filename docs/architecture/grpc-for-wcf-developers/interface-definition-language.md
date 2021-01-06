---
title: WCF geliştiricileri için arabirim tanımlama dili-gRPC
description: Protokol arabellekleri IDL ile tanışın.
ms.date: 12/15/2020
ms.openlocfilehash: 60cedd9b7c29bf54165b15f512c0b2159cb5dda9
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938084"
---
# <a name="interface-definition-language"></a>Arabirim Tanımlama Dili

Windows Communication Foundation (WCF) ile, Hizmetler Web hizmeti tanım dili (WSDL) kullanarak açıklama meta verilerini kullanıma sunabilir. WSDL, çalışma zamanında .NET Reflection kullanılarak dinamik olarak oluşturulur. Geliştiriciler bu meta verileri, büyük olasılıkla HTTP üzerinden SOAP gibi platformdan bağımsız bir bağlama kullanıyorsa diğer dillerde Bu hizmetler için istemciler oluşturmak üzere kullanabilir.

gRPC, protokol arabelleklerinden arabirim tanım dilini (IDL) kullanır. Protokol arabellekleri IDL, açık bir belirtimle özel, platformdan bağımsız bir dildir. Geliştiriciler `.proto` , kendi giriş ve çıkışlarıyla birlikte Hizmetleri tanımlayacak dosyaları yazar. Bu `.proto` dosyalar daha sonra istemciler ve sunucular için dile veya platforma özel saplamalar oluşturmak için kullanılabilir ve birden çok farklı platformun iletişim kurmasına olanak tanır. `.proto`Ekipler, dosyaları paylaşarak, bir kod bağımlılığı almak zorunda kalmadan diğerlerinin her birinin hizmetlerini kullanmak için kod oluşturabilir.

Prototipsel IDL 'nin avantajlarından biri özel bir dil olarak, gRPC 'nin tamamen dil ve platform belirsiz olmasını sağlar, başka bir teknolojiyi de favoring etmez.

Prototiplik IDL Ayrıca insanlar için hem okuma hem de yazma için tasarlanmıştır, WSDL ise makine tarafından okunabilen/yazılabilir biçim olarak tasarlanmıştır. Bir WCF hizmetinin WSDL 'sini değiştirmek, genellikle hizmetin değiştirilmesini, hizmetin çalıştırılmasını ve WSDL dosyasını sunucudan yeniden üretmeyi gerektirir. Bunun aksine, bir `.proto` dosyayla birlikte, değişiklikler bir metin Düzenleyicisi ile uygulanır ve oluşturulan kodla otomatik olarak akar. Visual Studio 2019 `.proto` , kaydedildiklerinde arka planda dosyaları oluşturur. VS Code gibi diğer düzenleyicilerle, proje oluşturulduğunda değişiklikler uygulanır.

XML ile karşılaştırıldığında ve özellikle SOAP kullanılarak kodlanan iletiler birçok avantaj sağlar. Prototip iletiler SOAP XML ile serileştirilmiş aynı verilerden daha küçük olmaya eğilimlidir ve kodlama, kod çözme ve ağ üzerinden iletilmesi daha hızlı olabilir.

Prototiplinin SOAP ile karşılaştırıldığında potansiyel dezavantajı, iletiler insanların okunmadığı için ileti içeriğinin hata ayıklaması için ek araçlar gerektirir.

> [!TIP]
> gRPC *,* önceden derlenmiş saplamalar olmadan hizmetlere dinamik olarak erişmek için sunucu yansımasını destekler, ancak uygulamaya özgü istemcilerden daha fazla genel amaçlı araçlara yöneliktir. Daha fazla bilgi için GitHub 'da [GRPC sunucu yansıma Protokolü](https://github.com/grpc/grpc/blob/master/doc/server-reflection.md) ' ne bakın.

> [!NOTE]
> WCF 'nin NetTCP bağlamasıyla kullanılan ikili biçimi, compactness ve performans açısından prototipte çok daha yakın. Ancak NetTCP yalnızca .NET istemcileri ve sunucuları arasında kullanılabilir, Protoda platformlar arası bir çözümdür.

>[!div class="step-by-step"]
>[Önceki](approach.md) 
> [Sonraki](network-protocols.md)
