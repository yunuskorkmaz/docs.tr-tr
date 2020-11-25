---
title: İç içe Geçmiş Türler
ms.date: 10/22/2008
helpviewer_keywords:
- types, nested
- public nested types
- type design guidelines, nested types
- nested types
- members [.NET Framework], type
- class library design guidelines [.NET Framework], nested types
ms.assetid: 12feb7f0-b793-4d96-b090-42d6473bab8c
ms.openlocfilehash: bc0aee32b5cc1d40afdd9cce8260d5b5341a687d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706404"
---
# <a name="nested-types"></a>İç içe Geçmiş Türler

İç içe bir tür, kapsayan tür olarak adlandırılan başka bir türün kapsamı içinde tanımlanan bir türdür. İç içe bir tür, kapsayan türünün tüm üyelerine erişebilir. Örneğin, kapsayan tür ' de tanımlanan özel alanlara ve kapsayan türün tüm yokler ' de tanımlanan korumalı alanlara erişimi vardır.

 Genel olarak, iç içe türler gelişigüzel kullanılmalıdır. Bunun birçok nedeni vardır. Bazı geliştiriciler kavram ile tam olarak tanıdık değildir. Bu geliştiriciler Örneğin, iç içe geçmiş türlerin değişkenlerini bildirme söz dizimi ile ilgili sorunlarla karşılaşabilirsiniz. İç içe türler aynı zamanda kapsayan türleriyle çok sıkı bir şekilde bağlanmış ve bu nedenle genel amaçlı türler gibi uygun değildir.

 İç içe türler, kapsayan türlerin modelleme uygulama ayrıntıları için idealdir. Son Kullanıcı nadiren iç içe bir türün değişkenlerini bildirmeli ve neredeyse asla iç içe geçmiş türleri örneklemek gerekmez. Örneğin, bir koleksiyonun numaralandırıcısı, o koleksiyonun iç içe bir türü olabilir. Numaralandırıcılar genellikle kapsayan türlerine göre örneklenmiştir ve birçok dil foreach ifadesini destekledikleri için, Numaralandırıcı değişkenlerinin Son Kullanıcı tarafından bildirilmelidir.

 iç içe geçmiş türü ve onun dış türü arasındaki ilişki, üye erişilebilirlik semantiklerine göre istenmediğinde iç içe türler kullanın ✔️.

 ❌ Genel iç içe türler mantıksal gruplandırma yapısı olarak kullanmayın; Bu ad alanlarını kullanın.

 ❌ Genel kullanıma açık iç içe türler kullanmaktan kaçının. Bunun tek istisnası, iç içe türün değişkenlerinin yalnızca altsınıflama veya diğer gelişmiş özelleştirme senaryoları gibi nadir senaryolarda bildirilmesine ihtiyaç duymalıdır.

 ❌ Tür, kapsayan tür dışında başvuruluyorsa iç içe türler kullanmayın.

 Örneğin, bir sınıfta tanımlanan bir metoda geçirilen Enum, sınıfta iç içe geçmiş bir tür olarak tanımlanmamalıdır.

 ❌ İç içe türler, istemci kodu tarafından örneklenmeleri gerekiyorsa kullanmayın.  Bir türün ortak Oluşturucusu varsa, muhtemelen iç içe olmamalıdır.

 Bir tür örneği oluşturulabilir, bu, türün kendi çerçevesinde bir yerde yer aldığı anlamına gelir (bunu oluşturabilir, onunla çalışabilir ve dış türü kullanmadan yok edebilir) ve bu nedenle iç içe geçmemelidir. İç türler, dış tür herhangi bir ilişki olmadan dış türün dışında yaygın olarak yeniden kullanılmamalıdır.

 ❌ İç içe bir türü arabirimin üyesi olarak tanımlamayın. Birçok dil böyle bir yapıyı desteklemez.

 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*

 *Microsoft Windows geliştirme serisi 'nin bir parçası olarak, Addison-Wesley Professional tarafından, yeniden [kullanılabilir .NET kitaplıkları Için kurallar, deyimler ve desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vabzysztof Cwalina ve atacan Abkms, yayımlandı Ekim 22, 2008 tarafından yeniden yazdırılmıştır.*

## <a name="see-also"></a>Ayrıca bkz.

- [Tür tasarım yönergeleri](type.md)
- [Çerçeve tasarım yönergeleri](index.md)
