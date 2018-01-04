---
title: "Soyut sınıf tasarımı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- type design guidelines, abstract classes
- abstract classes, design guidelines
- class library design guidelines [.NET Framework], classes
- classes [.NET Framework], abstract
- classes [.NET Framework], design guidelines
- type design guidelines, classes
ms.assetid: d3646e6d-5c1f-4922-8fb0-ec5effb30d60
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 739f86acd534549bc997dc7a939cf43a0c6fc3cb
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="abstract-class-design"></a>Soyut sınıf tasarımı
**X yok** soyut türlerinde genel ya da korumalı iç oluşturucuları tanımlama.  
  
 Oluşturucular kullanıcılar türdeki örneklerin oluşturmanız gerekir, ortak olmalıdır. Soyut bir tür örneklerini oluşturamazsınız çünkü bir public oluşturucuya sahip soyut bir tür tasarlanmış ve kullanıcılara yanıltıcı yanlış.  
  
 **✓ YAPMAK** korumalı bir ya da bir iç Oluşturucusu soyut sınıflarda tanımlayın.  
  
 Korumalı Oluşturucu daha yaygın bir durumdur ve yalnızca alt oluşturulduğunda kendi başlatma yapmak temel sınıf sağlar.  
  
 Bir iç Oluşturucusu sınıfını tanımlama derleme Özet sınıf, somut uygulamalarını sınırlamak için kullanılabilir.  
  
 **✓ YAPMAK** sevk her soyut sınıfından devralan en az bir somut türü sağlayın.  
  
 Soyut sınıf tasarımını doğrulamak için bu yardımcı yapılıyor. Örneğin, <xref:System.IO.FileStream?displayProperty=nameWithType> uygulamasıdır <xref:System.IO.Stream?displayProperty=nameWithType> soyut sınıf.  
  
 *Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Tür Tasarımı Yönergeleri](../../../docs/standard/design-guidelines/type.md)  
 [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
