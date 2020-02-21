---
title: WCF geliştiricileri için arabirim tanımlama dili-gRPC
description: Protokol arabellekleri IDL ile tanışın.
ms.date: 09/02/2019
ms.openlocfilehash: 841f041ae350e76e648c71f9d6d113b9d39e0d3b
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543215"
---
# <a name="interface-definition-language"></a>Arabirim Tanımlama Dili

Windows Communication Foundation (WCF) ile, Hizmetler Web hizmeti tanım dili (WSDL) kullanarak açıklama meta verilerini kullanıma sunabilir. WSDL, çalışma zamanında .NET Reflection kullanılarak dinamik olarak oluşturulur. Geliştiriciler bu meta verileri, büyük olasılıkla HTTP üzerinden SOAP gibi platformdan bağımsız bir bağlama kullanıyorsa diğer dillerde Bu hizmetler için istemciler oluşturmak üzere kullanabilir.

gRPC, protokol arabelleklerinden arabirim tanım dilini (IDL) kullanır. Protokol arabellekleri IDL, açık bir belirtimle özel, platformdan bağımsız bir dildir. Geliştiriciler, hizmetleri ve çıkışları ile birlikte, hizmetleri anlatmak için `.proto` dosyaları yazar. Bu `.proto` dosyalar daha sonra istemciler ve sunucular için dile veya platforma özel saplamalar oluşturmak için kullanılabilir ve birden çok farklı platformun iletişim kurmasına olanak tanır. `.proto` dosyaları paylaşarak takımlar, bir kod bağımlılığı almak zorunda kalmadan, diğerlerinin her birinin hizmetlerini kullanmak için kod oluşturabilir.

Prototipsel IDL 'nin avantajlarından biri özel bir dil olarak, gRPC 'nin tamamen dil ve platform belirsiz olmasını sağlar, başka bir teknolojiyi de favoring etmez.

Prototiplik IDL Ayrıca insanlar için hem okuma hem de yazma için tasarlanmıştır, WSDL ise makine tarafından okunabilen/yazılabilir biçim olarak tasarlanmıştır. Bir WCF hizmetinin WSDL 'sini değiştirmek, genellikle hizmetin değiştirilmesini, hizmetin çalıştırılmasını ve WSDL dosyasını sunucudan yeniden üretmeyi gerektirir. Bunun aksine, bir `.proto` dosyası ile, değişiklikler basit bir metin Düzenleyicisi ile uygulanır ve oluşturulan kodla otomatik olarak akar. Visual Studio 2019, kaydedildiklerinde arka planda `.proto` dosyaları oluşturur. VS Code gibi diğer düzenleyicilerle, proje oluşturulduğunda değişiklikler uygulanır.

XML ile karşılaştırıldığında ve özellikle SOAP kullanılarak kodlanan iletiler birçok avantaj sağlar. Prototip iletiler SOAP XML ile serileştirilmiş aynı verilerden daha küçük olmaya eğilimlidir ve kodlama, kod çözme ve ağ üzerinden iletilmesi daha hızlı olabilir.

Prototiplinin SOAP ile karşılaştırıldığında potansiyel dezavantajı, iletiler insanların okunmadığı için ileti içeriğinin hata ayıklaması için ek araçlar gerektirir.

> [!TIP]
> gRPC *,* önceden derlenmiş saplamalar olmadan hizmetlere dinamik olarak erişmek için sunucu yansımasını destekler, ancak uygulamaya özgü istemcilerden daha fazla genel amaçlı araçlara yöneliktir. Daha fazla bilgi için GitHub 'da [GRPC sunucu yansıma Protokolü](https://github.com/grpc/grpc/blob/master/doc/server-reflection.md) ' ne bakın.

> [!NOTE]
> WCF 'nin NetTCP bağlamasıyla kullanılan ikili biçimi, compactness ve performans açısından prototipte çok daha yakın. Ancak NetTCP yalnızca .NET istemcileri ve sunucuları arasında kullanılabilir, Protoda platformlar arası bir çözümdür.

>[!div class="step-by-step"]
>[Önceki](approach.md)
>[İleri](network-protocols.md)
