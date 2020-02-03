---
title: Statik Sınıf Tasarımı
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines, static classes
- class library design guidelines [.NET Framework], classes
- classes [.NET Framework], static
- static classes [.NET Framework]
- classes [.NET Framework], design guidelines
- type design guidelines, classes
ms.assetid: d67c14d8-c4dd-443f-affb-4ccae677c9b6
ms.openlocfilehash: 104fa204a95ef31d34e224348068e3a6505aded5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743601"
---
# <a name="static-class-design"></a>Statik Sınıf Tasarımı
Statik bir sınıf, yalnızca statik Üyeler (<xref:System.Object?displayProperty=nameWithType> devralınan örnek üyelerinin yanı sıra özel bir Oluşturucu) içeren bir sınıf olarak tanımlanır. Bazı diller statik sınıflar için yerleşik destek sağlar. C# 2,0 ve sonraki sürümlerde, bir sınıf statik olarak bildirildiğinde, mühürlenmiş, soyut ve hiçbir örnek üye geçersiz kılınabilir veya bildirilemez.

 Statik sınıflar saf nesne odaklı tasarım ve basitlik arasında bir uzlaşdır. Bunlar yaygın olarak diğer işlemlere (<xref:System.IO.File?displayProperty=nameWithType>), uzantı yöntemlerinin sahiplerine veya tam nesne odaklı bir sarmalayıcının izin verilmeyen bir sarmalayıcı (<xref:System.Environment?displayProperty=nameWithType>gibi) için kısayollar sağlamak üzere kullanılır.

 ✔️ statik sınıfları gelişigüzel bir şekilde kullanın.

 Statik sınıflar yalnızca çerçevenin nesne odaklı çekirdeği için destekleme sınıfları olarak kullanılmalıdır.

 ❌ statik sınıfları çeşitli demet olarak kabul etmez.

 ❌ statik sınıflarda örnek üyelerini bildiremez veya geçersiz kılmaz.

 ✔️ statik sınıfları korumalı, soyut olarak bildirir ve programlama dilinizin statik sınıflar için yerleşik desteği yoksa özel bir örnek oluşturucu ekleyin.

 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*

 *, Microsoft Windows geliştirme serisinin bir parçası olarak, [.NET kitaplıkları için 2. sürüm](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vazysztof Cwalina ve atacan Abk2008 MS, 4. Adım: Addison-Wesley Professional tarafından yeniden yazdırılmıştır.*

## <a name="see-also"></a>Ayrıca bkz.

- [Tür Tasarımı Yönergeleri](../../../docs/standard/design-guidelines/type.md)
- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
