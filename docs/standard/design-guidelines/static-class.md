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
ms.openlocfilehash: 35bcf1d403c78cdfcbb476b2eb5de2251a564b9a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709068"
---
# <a name="static-class-design"></a>Statik Sınıf Tasarımı
Statik bir sınıf, yalnızca statik Üyeler (<xref:System.Object?displayProperty=nameWithType> devralınan örnek üyelerinin yanı sıra özel bir Oluşturucu) içeren bir sınıf olarak tanımlanır. Bazı diller statik sınıflar için yerleşik destek sağlar. C# 2,0 ve sonraki sürümlerde, bir sınıf statik olarak bildirildiğinde, mühürlenmiş, soyut ve hiçbir örnek üye geçersiz kılınabilir veya bildirilemez.  
  
 Statik sınıflar saf nesne odaklı tasarım ve basitlik arasında bir uzlaşdır. Bunlar yaygın olarak diğer işlemlere (<xref:System.IO.File?displayProperty=nameWithType>), uzantı yöntemlerinin sahiplerine veya tam nesne odaklı bir sarmalayıcının izin verilmeyen bir sarmalayıcı (<xref:System.Environment?displayProperty=nameWithType>gibi) için kısayollar sağlamak üzere kullanılır.  
  
 **✓ DO** statik sınıflar tutumlu kullanın.  
  
 Statik sınıflar yalnızca çerçevenin nesne odaklı çekirdeği için destekleme sınıfları olarak kullanılmalıdır.  
  
 **X DO NOT** statik sınıflar çeşitli kova olarak ele alın.  
  
 **X DO NOT** bildirme veya statik sınıflarda örnek üyeleri geçersiz kılın.  
  
 **✓ DO** statik sınıflar bildirmeniz korumalı, soyut olarak ve programlama diliniz statik sınıflar için yerleşik destek yoksa özel örnek oluşturucu ekleyin.  
  
 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tür Tasarımı Yönergeleri](../../../docs/standard/design-guidelines/type.md)
- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
