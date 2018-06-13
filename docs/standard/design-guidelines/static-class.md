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
ms.openlocfilehash: 92152600d317c04e3fef26400b11e94a549fde4c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33571065"
---
# <a name="static-class-design"></a>Statik sınıf tasarımı
Statik sınıf yalnızca statik üyeleri içeren bir sınıf olarak tanımlanır (elbette devralınan örnek üyelerin yanı sıra <xref:System.Object?displayProperty=nameWithType> ve büyük olasılıkla özel Oluşturucu). Bazı diller statik sınıflar için yerleşik destek sağlar. C# 2.0 ve daha sonra bir sınıf statik olarak bildirilmişse, korumalı, soyut ve hiçbir örnek üyesinin geçersiz ya bildirilir.  
  
 Saf nesne odaklı tasarım ve Basitlik arasında bir seçim statik sınıflarıdır. Bunlar genellikle diğer işlemleri kısayollar sağlamak için kullanılır (gibi <xref:System.IO.File?displayProperty=nameWithType>), uzantı yöntemleri ya da tam nesne yönelimli bir sarmalayıcı olduğu unwarranted işlevselliği sahiplerini (gibi <xref:System.Environment?displayProperty=nameWithType>).  
  
 **✓ YAPMAK** statik sınıflar tutumlu kullanın.  
  
 Statik sınıflar yalnızca framework nesne yönelimli çekirdek için destekleyici sınıflar olarak kullanılmalıdır.  
  
 **X yok** statik sınıflar çeşitli kova olarak ele alın.  
  
 **X yok** bildirme veya statik sınıflarda örnek üyeleri geçersiz kılın.  
  
 **✓ YAPMAK** statik sınıflar bildirmeniz korumalı, soyut olarak ve programlama diliniz statik sınıflar için yerleşik destek yoksa özel örnek oluşturucu ekleyin.  
  
 *Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Tür Tasarımı Yönergeleri](../../../docs/standard/design-guidelines/type.md)  
 [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
