---
title: Statik sınıf tasarımı
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines, static classes
- class library design guidelines [.NET Framework], classes
- classes [.NET Framework], static
- static classes [.NET Framework]
- classes [.NET Framework], design guidelines
- type design guidelines, classes
ms.assetid: d67c14d8-c4dd-443f-affb-4ccae677c9b6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c3a0a51fc6055190f9a0189de2e17d98f88036ea
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2018
ms.locfileid: "44249574"
---
# <a name="static-class-design"></a>Statik sınıf tasarımı
Bir statik sınıf yalnızca statik üyeleri içeren bir sınıfı tanımlanır (kuşkusuz devralınan örnek üyeleri yanı sıra <xref:System.Object?displayProperty=nameWithType> ve büyük olasılıkla bir private Oluşturucu). Bazı diller, statik sınıflar için yerleşik destek sağlar. C# 2.0 ve sonraki sürümlerinde, bir sınıfın statik olarak bildirilmişse, korumalı, soyut olduğu ve hiç örnek üyeleri geçersiz kılınmış veya bildirildi.  
  
 Statik sınıflar, saf nesne yönelimli tasarım ve Basitlik arasında bir denge sınıflarıdır. Bunlar genellikle diğer işlemler için kısayollar sağlamak için kullanılır (gibi <xref:System.IO.File?displayProperty=nameWithType>), genişletme yöntemleri veya tam nesne yönelimli bir sarmalayıcı olan unwarranted işlevselliği sahipleri (gibi <xref:System.Environment?displayProperty=nameWithType>).  
  
 **✓ DO** statik sınıflar tutumlu kullanın.  
  
 Statik sınıflar yalnızca için nesne yönelimli core framework'ün destek sınıfları olarak kullanılmalıdır.  
  
 **X DO NOT** statik sınıflar çeşitli kova olarak ele alın.  
  
 **X DO NOT** bildirme veya statik sınıflarda örnek üyeleri geçersiz kılın.  
  
 **✓ DO** statik sınıflar bildirmeniz korumalı, soyut olarak ve programlama diliniz statik sınıflar için yerleşik destek yoksa özel örnek oluşturucu ekleyin.  
  
 *Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tür Tasarımı Yönergeleri](../../../docs/standard/design-guidelines/type.md)  
- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
