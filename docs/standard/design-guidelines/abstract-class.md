---
title: Soyut sınıf tasarımı
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines, abstract classes
- abstract classes, design guidelines
- class library design guidelines [.NET Framework], classes
- classes [.NET Framework], abstract
- classes [.NET Framework], design guidelines
- type design guidelines, classes
ms.assetid: d3646e6d-5c1f-4922-8fb0-ec5effb30d60
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c5b9dacc4995a126e1ee3f6062dca796194d4882
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/20/2018
ms.locfileid: "46493496"
---
# <a name="abstract-class-design"></a>Soyut sınıf tasarımı
**X DO NOT** soyut türlerinde genel ya da korumalı iç oluşturucuları tanımlama.  
  
 Oluşturucular, yalnızca kullanıcıların türünün örneğini oluşturmak gerekir, ortak olmalıdır. Bir soyut türün örneklerini oluşturamayacağınızdan bir public Oluşturucu ile soyut bir tür yanlış ve yanıltıcı kullanıcılar için tasarlanmıştır.  
  
 **✓ DO** korumalı bir ya da bir iç Oluşturucusu soyut sınıflarda tanımlayın.  
  
 Korumalı Oluşturucu daha yaygın olarak görülür ve yalnızca subtypes oluştururken kendi başlangıç yapmak temel sınıf sağlar.  
  
 Bir iç Oluşturucu somut uygulamalarını derlemesine olan sınıfı tanımlayan soyut sınıfın sınırlamak için kullanılabilir.  
  
 **✓ DO** sevk her soyut sınıfından devralan en az bir somut türü sağlayın.  
  
 Soyut sınıf tasarımı doğrulamak için bu yardımcı yapılıyor. Örneğin, <xref:System.IO.FileStream?displayProperty=nameWithType> uygulamasıdır <xref:System.IO.Stream?displayProperty=nameWithType> soyut sınıf.  
  
 *Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tür Tasarımı Yönergeleri](../../../docs/standard/design-guidelines/type.md)  
- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
