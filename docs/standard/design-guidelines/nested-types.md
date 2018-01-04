---
title: "İç içe Geçmiş Türler"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- types, nested
- public nested types
- type design guidelines, nested types
- nested types
- members [.NET Framework], type
- class library design guidelines [.NET Framework], nested types
ms.assetid: 12feb7f0-b793-4d96-b090-42d6473bab8c
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 389ba73c4509f41f6c2cf86363e59ea720eb3c9f
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="nested-types"></a>İç içe Geçmiş Türler
İç içe geçmiş tür, kendilerini kapsayan türle adlı başka bir tür kapsam içinde tanımlanan bir türüdür. İç içe geçmiş tür kapsayan türü tüm üyeleri erişebilir. Örneğin, kendilerini kapsayan türle ve korumalı alanlarına kendilerini kapsayan türle tüm üst öğelerinden içinde tanımlanan tanımlı özel alanlara erişimi vardır.  
  
 Genel olarak, iç içe geçmiş türler kullanılmamalıdır. Bunun birkaç nedeni vardır. Bazı geliştiriciler kavramına tam olarak aşina değildir. Örneğin, bu geliştiriciler iç içe geçmiş türler değişkenleri bildirme sözdizimi ile ilgili sorun yaşayabilir. İç içe geçmiş türler kapsayan kendi türleriyle aynı zamanda çok sıkı şekilde bağlı ve bu nedenle genel amaçlı türleri için uygundur değil.  
  
 İç içe geçmiş türler kapsayan türlerini uygulama ayrıntılarını modelleme için uygundur. Son kullanıcı nadiren iç içe geçmiş tür değişkenler bildirmek olmalıdır ve açıkça iç içe geçmiş türler örneği oluşturmak neredeyse hiçbir zaman sahip olmalıdır. Örneğin, bir koleksiyon öğesinin numaralandırıcısını o koleksiyonun iç içe geçmiş tür olabilir. Numaralandırıcılar genellikle kendilerini kapsayan türle tarafından oluşturulur ve birçok dilde foreach deyimi desteklediğinden, numaralandırıcı değişkenleri nadiren son kullanıcı tarafından bildirilmesi gerekir.  
  
 **✓ YAPMAK** üye erişilebilirlik semantiği istenen şekilde iç içe geçmiş tür ve dış türü arasındaki ilişkiyi olduğunda iç içe geçmiş türler kullanın.  
  
 **X yok** kullanım ortak iç içe geçmiş türler, mantıksal bir gruplandırma olarak oluşturun; ad alanları için bunu kullanın.  
  
 **KAÇININ x** herkese açık şekilde iç içe geçmiş türler açık. Bunun tek istisnası, iç içe geçmiş tür değişkenler yalnızca senaryolarda nadir sınıflara veya diğer gelişmiş özelleştirme senaryoları gibi bildirilmesi gerekip gerekmediğini ' dir.  
  
 **X yok** türü içeren türde dışında başvurulacak olasılığı olan iç içe geçmiş türler kullanın.  
  
 Örneğin, bir sınıf üzerinde tanımlı bir yönteme geçirilen enum iç içe bir sınıf türü olarak tanımlanmamalıdır.  
  
 **X yok** istemci kodu tarafından örneğinin oluşturulması gerekirse iç içe geçmiş türler kullanın.  Bir türü bir public oluşturucuya varsa, iç içe olmayabilir.  
  
 Bir türü örneği varsa, görünüyor türünde framework kendi başına bir yerde belirtmek için (Bu oluşturabilir, iş ile ve dış türü kullanmadan yok) ve bu nedenle iç içe değil. İç türleri değil yaygın olarak yeniden kullanılabilir herhangi bir ilişki olmadan dış türü dışında dış türü yoktur.  
  
 **X yok** iç içe geçmiş tür bir arabirim üye olarak tanımlayın. Birçok dilde bu tür bir yapı desteklemez.  
  
 *Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Tür Tasarımı Yönergeleri](../../../docs/standard/design-guidelines/type.md)  
 [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
