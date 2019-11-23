---
title: WCF geliştiricileri için arabirim tanımlama dili-gRPC
description: Protokol arabellekleri IDL ile tanışın.
ms.date: 09/02/2019
ms.openlocfilehash: 1f304502bd0091f753a3d2f7854298f4bbf983f1
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73967636"
---
# <a name="interface-definition-language"></a>Arabirim Tanımlama Dili

WCF ile hizmetler, çalışma zamanında .NET Reflection kullanılarak dinamik olarak oluşturulan Web hizmeti tanım dili 'ni (WSDL) kullanarak açıklama meta verilerini kullanıma sunabilir. Geliştiriciler, HTTP üzerinden SOAP gibi bir platformdan bağımsız bağlamanın kullanılması durumunda bu hizmetler için istemcileri oluşturmak üzere bu meta verileri kullanabilir.

gRPC, protokol arabelleklerinden arabirim tanım dilini (IDL) kullanır. Protokol arabellekleri IDL, açık bir belirtimle özel, platformdan bağımsız bir dildir. Geliştiriciler, kendi giriş ve çıkışlarıyla birlikte hizmetleri anlatmak için `.proto` dosyaları. Bu `.proto` dosyalar daha sonra istemciler ve sunucular için dile veya platforma özel saplamalar oluşturmak için kullanılabilir ve birden çok farklı platformun iletişim kurmasına olanak tanır. `.proto` dosyaları paylaşarak takımlar, bir kod bağımlılığı almak zorunda kalmadan diğerlerinin her birinin hizmetlerini kullanmak için kod oluşturabilir.

Prototipsel IDL 'nin avantajlarından biri, özel bir dil olarak, gRPC 'nin tamamen dil ve platform belirsiz olmasını sağladığından, başka bir teknolojinin favoring sağlamaz.

Prototiplik IDL Ayrıca insanlar için hem okuma hem de yazma için tasarlanmıştır, WSDL ise makine tarafından okunabilen/yazılabilir biçim olarak tasarlanmıştır. Bir WCF hizmetinin WSDL 'sini değiştirmek, genellikle hizmet kodu üzerinde değişiklik yapılmasını, hizmetin çalıştırılmasını ve WSDL dosyasını sunucudan yeniden üretmeyi gerektirir. Bunun aksine, bir `.proto` dosyası ile, değişiklikler basit bir metin Düzenleyicisi ile uygulanır ve oluşturulan kodla otomatik olarak akar. Visual Studio 2019, kaydedildiklerinde arka planda `.proto` dosyaları oluşturur; VS Code gibi diğer düzenleyiciler kullanılırken, proje oluşturulduğunda değişiklikler uygulanır.

XML ile karşılaştırıldığında ve özellikle SOAP kullanılarak kodlanan iletiler birçok avantaj sağlar. Prototip iletiler SOAP XML ile serileştirilmiş aynı verilerden daha küçük olmaya eğilimlidir ve kodlama, kod çözme ve ağ üzerinden iletme daha hızlı olabilir.

Prototiplendirme 'nin SOAP ile karşılaştırıldığında potansiyel dezavantajı, iletilerin okunabilir olmaması nedeniyle ileti içeriğinin hata ayıklaması için ek araçlar gereklidir.

> [!TIP]
> gRPC *,* önceden derlenmiş saplamalar olmadan hizmetlere dinamik olarak erişmek için sunucu yansımasını destekler, ancak uygulamaya özgü istemcilerden daha fazla genel amaçlı araçlara yönelik olarak tasarlanmıştır. GRPC Server Reflection hakkında daha fazla bilgi için bkz. GitHub 'da [GRPC/GRPC](https://github.com/grpc/grpc/blob/master/doc/server-reflection.md) deposu.

> [!NOTE]
> WCF 'nin NetTCP bağlamasıyla birlikte kullanılan ikili biçimi, compactness ve performans açısından prototiplik 'e çok daha yakın, ancak NetTCP yalnızca .NET istemcileri ve sunucuları arasında kullanılabilir, bu arada bir platformlar arası çözümdür.

>[!div class="step-by-step"]
>[Önceki](approach.md)
>[İleri](network-protocols.md)
