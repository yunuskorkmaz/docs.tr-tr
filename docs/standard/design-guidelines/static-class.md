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
author: KrzysztofCwalina
ms.openlocfilehash: d0a2f11b53f50f2ec2f301f7b88df65e1cd7b811
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61762052"
---
# <a name="static-class-design"></a>Statik Sınıf Tasarımı
Bir statik sınıf yalnızca statik üyeleri içeren bir sınıfı tanımlanır (kuşkusuz devralınan örnek üyeleri yanı sıra <xref:System.Object?displayProperty=nameWithType> ve büyük olasılıkla bir private Oluşturucu). Bazı diller, statik sınıflar için yerleşik destek sağlar. C# 2.0 ve sonraki sürümlerinde, bir sınıfın statik olarak bildirilmişse, korumalı, soyut olduğu ve hiç örnek üyeleri geçersiz kılınmış veya bildirildi.  
  
 Statik sınıflar, saf nesne yönelimli tasarım ve Basitlik arasında bir denge sınıflarıdır. Bunlar genellikle diğer işlemler için kısayollar sağlamak için kullanılır (gibi <xref:System.IO.File?displayProperty=nameWithType>), genişletme yöntemleri veya tam nesne yönelimli bir sarmalayıcı olan unwarranted işlevselliği sahipleri (gibi <xref:System.Environment?displayProperty=nameWithType>).  
  
 **✓ DO** statik sınıflar tutumlu kullanın.  
  
 Statik sınıflar yalnızca için nesne yönelimli core framework'ün destek sınıfları olarak kullanılmalıdır.  
  
 **X DO NOT** statik sınıflar çeşitli kova olarak ele alın.  
  
 **X DO NOT** bildirme veya statik sınıflarda örnek üyeleri geçersiz kılın.  
  
 **✓ DO** statik sınıflar bildirmeniz korumalı, soyut olarak ve programlama diliniz statik sınıflar için yerleşik destek yoksa özel örnek oluşturucu ekleyin.  
  
 *Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: Kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 Addison Wesley Professional ile Microsoft Windows geliştirme serisi bir parçası olarak yayımlandı.*  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tür Tasarımı Yönergeleri](../../../docs/standard/design-guidelines/type.md)
- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
