---
title: "Statik sınıf tasarımı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- type design guidelines, static classes
- class library design guidelines [.NET Framework], classes
- classes [.NET Framework], static
- static classes [.NET Framework]
- classes [.NET Framework], design guidelines
- type design guidelines, classes
ms.assetid: d67c14d8-c4dd-443f-affb-4ccae677c9b6
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 28fe3756a2881e8f746616f8275b505b1a01eada
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
  
 *Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Türü tasarım yönergeleri](../../../docs/standard/design-guidelines/type.md)  
 [Framework tasarım yönergeleri](../../../docs/standard/design-guidelines/index.md)
