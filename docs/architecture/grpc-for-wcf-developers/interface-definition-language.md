---
title: WCF geliştiricileri için arabirim tanımlama dili-gRPC
description: Protokol arabellekleri IDL ile tanışın.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 71bdf8bf488e0a5bed177817343051bcd7847d25
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184430"
---
# <a name="interface-definition-language"></a>Arabirim tanımı dili

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

WCF ile hizmetler, çalışma zamanında .NET Reflection kullanılarak dinamik olarak oluşturulan Web hizmeti tanım dili 'ni (WSDL) kullanarak açıklama meta verilerini kullanıma sunabilir. Geliştiriciler, HTTP üzerinden SOAP gibi bir platformdan bağımsız bağlamanın kullanılması durumunda bu hizmetler için istemcileri oluşturmak üzere bu meta verileri kullanabilir.

gRPC, protokol arabelleklerinden arabirim tanım dilini (IDL) kullanır. Protokol arabellekleri IDL, açık bir belirtimle özel, platformdan bağımsız bir dildir. Geliştiricilere, giriş ve `.proto` çıkışlarıyla birlikte hizmetleri anlatmak için kod dosyaları. Bu `.proto` dosyalar daha sonra istemciler ve sunucular için dile veya platforma özel saplamalar oluşturmak için kullanılabilir ve birden çok farklı platformun iletişim kurmasına olanak tanır. Ekipler, `.proto` dosyaları paylaşarak, bir kod bağımlılığı almak zorunda kalmadan diğerlerinin her birinin hizmetlerini kullanmak için kod oluşturabilir.

Prototipsel IDL 'nin avantajlarından biri, özel bir dil olarak, gRPC 'nin tamamen dil ve platform belirsiz olmasını sağladığından, başka bir teknolojinin favoring sağlamaz.

Prototiplik IDL Ayrıca insanlar için hem okuma hem de yazma için tasarlanmıştır, WSDL ise makine tarafından okunabilen/yazılabilir biçim olarak tasarlanmıştır. Bir WCF hizmetinin WSDL 'sini değiştirmek, genellikle hizmet kodu üzerinde değişiklik yapılmasını, hizmetin çalıştırılmasını ve WSDL dosyasını sunucudan yeniden üretmeyi gerektirir. Bunun aksine, bir `.proto` dosyayla birlikte, değişiklikler bir metin Düzenleyicisi ile uygulanır ve oluşturulan kodla otomatik olarak akar. Visual Studio 2019, `.proto` kaydedildiklerinde arka planda dosyaları oluşturur; vs Code gibi diğer düzenleyiciler kullanılırken, proje oluşturulduğunda değişiklikler uygulanır.

XML ile karşılaştırıldığında ve özellikle SOAP kullanılarak kodlanan iletiler birçok avantaj sağlar. Prototip iletiler SOAP XML ile serileştirilmiş aynı verilerden daha küçük olmaya eğilimlidir ve kodlama, kod çözme ve ağ üzerinden iletme daha hızlı olabilir.

Prototiplendirme 'nin SOAP ile karşılaştırıldığında potansiyel dezavantajı, iletilerin okunabilir olmaması nedeniyle ileti içeriğinin hata ayıklaması için ek araçlar gereklidir.

> [!TIP]
> gRPC *,* önceden derlenmiş saplamalar olmadan hizmetlere dinamik olarak erişmek için sunucu yansımasını destekler, ancak uygulamaya özgü istemcilerden daha fazla genel amaçlı araçlara yönelik olarak tasarlanmıştır. GRPC Server Reflection hakkında daha fazla bilgi için bkz. GitHub 'da [GRPC/GRPC](https://github.com/grpc/grpc/blob/master/doc/server-reflection.md) deposu.

> [!NOTE]
> WCF 'nin NetTCP bağlamasıyla birlikte kullanılan ikili biçimi, compactness ve performans açısından prototiplik 'e çok daha yakın, ancak NetTCP yalnızca .NET istemcileri ve sunucuları arasında kullanılabilir, bu arada bir platformlar arası çözümdür.

>[!div class="step-by-step"]
>[Önceki](approach.md)
>[İleri](network-protocols.md)
