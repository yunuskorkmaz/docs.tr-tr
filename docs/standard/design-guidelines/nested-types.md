---
title: İç içe Geçmiş Türler
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- types, nested
- public nested types
- type design guidelines, nested types
- nested types
- members [.NET Framework], type
- class library design guidelines [.NET Framework], nested types
ms.assetid: 12feb7f0-b793-4d96-b090-42d6473bab8c
ms.openlocfilehash: 3467851aa767efcd0557e8a412cd36316a48b9b0
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709159"
---
# <a name="nested-types"></a>İç içe Geçmiş Türler
İç içe bir tür, kapsayan tür olarak adlandırılan başka bir türün kapsamı içinde tanımlanan bir türdür. İç içe bir tür, kapsayan türünün tüm üyelerine erişebilir. Örneğin, kapsayan tür ' de tanımlanan özel alanlara ve kapsayan türün tüm yokler ' de tanımlanan korumalı alanlara erişimi vardır.  
  
 Genel olarak, iç içe türler gelişigüzel kullanılmalıdır. Bunun birçok nedeni vardır. Bazı geliştiriciler kavram ile tam olarak tanıdık değildir. Bu geliştiriciler Örneğin, iç içe geçmiş türlerin değişkenlerini bildirme söz dizimi ile ilgili sorunlarla karşılaşabilirsiniz. İç içe türler aynı zamanda kapsayan türleriyle çok sıkı bir şekilde bağlanmış ve bu nedenle genel amaçlı türler gibi uygun değildir.  
  
 İç içe türler, kapsayan türlerin modelleme uygulama ayrıntıları için idealdir. Son Kullanıcı nadiren iç içe bir türün değişkenlerini bildirmeli ve neredeyse asla iç içe geçmiş türleri örneklemek gerekmez. Örneğin, bir koleksiyonun numaralandırıcısı, o koleksiyonun iç içe bir türü olabilir. Numaralandırıcılar genellikle kapsayan türlerine göre örneklenmiştir ve birçok dil foreach ifadesini destekledikleri için, Numaralandırıcı değişkenlerinin Son Kullanıcı tarafından bildirilmelidir.  
  
 **✓ DO** üye erişilebilirlik semantiği istenen şekilde iç içe geçmiş tür ve dış türü arasındaki ilişkiyi olduğunda iç içe geçmiş türler kullanın.  
  
 **X DO NOT** kullanım ortak iç içe geçmiş türler, mantıksal bir gruplandırma olarak oluşturun; ad alanları için bunu kullanın.  
  
 **X AVOID** herkese açık şekilde iç içe geçmiş türler açık. Bunun tek istisnası, iç içe türün değişkenlerinin yalnızca altsınıflama veya diğer gelişmiş özelleştirme senaryoları gibi nadir senaryolarda bildirilmesine ihtiyaç duymalıdır.  
  
 **X DO NOT** türü içeren türde dışında başvurulacak olasılığı olan iç içe geçmiş türler kullanın.  
  
 Örneğin, bir sınıfta tanımlanan bir metoda geçirilen Enum, sınıfta iç içe geçmiş bir tür olarak tanımlanmamalıdır.  
  
 **X DO NOT** istemci kodu tarafından örneğinin oluşturulması gerekirse iç içe geçmiş türler kullanın.  Bir türün ortak Oluşturucusu varsa, muhtemelen iç içe olmamalıdır.  
  
 Bir tür örneği oluşturulabilir, bu, türün kendi çerçevesinde bir yerde yer aldığı anlamına gelir (bunu oluşturabilir, onunla çalışabilir ve dış türü kullanmadan yok edebilir) ve bu nedenle iç içe geçmemelidir. İç türler, dış tür herhangi bir ilişki olmadan dış türün dışında yaygın olarak yeniden kullanılmamalıdır.  
  
 **X DO NOT** iç içe geçmiş tür bir arabirim üye olarak tanımlayın. Birçok dil böyle bir yapıyı desteklemez.  
  
 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tür Tasarımı Yönergeleri](../../../docs/standard/design-guidelines/type.md)
- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
