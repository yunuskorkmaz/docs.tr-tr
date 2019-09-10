---
title: Dizilerde Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- culture-insensitive string operations, in arrays
- arrays [.NET Framework], culture-insensitive string operations
- comparer parameter
ms.assetid: f12922e1-6234-4165-8896-63f0653ab478
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b52ff8d72132c1076dfdece5e1ce47bbece37b81
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855999"
---
# <a name="performing-culture-insensitive-string-operations-in-arrays"></a>Dizilerde Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme

Ve <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> <xref:System.Array.Sort%2A?displayProperty=nameWithType> yöntemlerininaşırıyüklemeleri,özelliğinikullanarakvarsayılanolarakkültüreduyarlısıralargerçekleştirir.<xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> Bu yöntemler tarafından döndürülen kültüre duyarlı sonuçlar, sıralama emirlerindeki farklılıklar nedeniyle kültüre göre farklılık gösterebilir. Kültüre duyarlı davranışı ortadan kaldırmak için, bu yöntemin bir `comparer` parametreyi kabul eden aşırı yüklemelerinin birini kullanın. Parametresi dizideki öğeleri karşılaştırırken <xref:System.Collections.IComparer> kullanılacak uygulamayı belirtir. `comparer` Parametresi için, tarafından kullanılan <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>özel bir sabit karşılaştırıcı sınıfı belirtin. [Koleksiyonlarda kültüre duyarsız dize Işlemlerini gerçekleştirme](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) konusundaki "SortedList sınıfı kullanma" alt konusunun özel bir sabit karşılaştırıcı sınıfına bir örnek verilmiştir.

> [!NOTE]
> Bir karşılaştırma yöntemine **CultureInfo. InvariantCulture** geçirilmesi, kültüre duyarsız bir karşılaştırma gerçekleştirir. Ancak, dosya yolları, kayıt defteri anahtarları ve ortam değişkenleri gibi dil olmayan bir karşılaştırmaya neden olmaz. , Karşılaştırma sonucuna göre güvenlik kararlarını desteklemez. Dil olmayan bir karşılaştırma veya sonuç tabanlı güvenlik kararları için destek için, uygulamanın bir <xref:System.StringComparison> değeri kabul eden bir karşılaştırma yöntemi kullanması gerekir. Uygulama daha sonra geçmelidir <xref:System.StringComparison.Ordinal>.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Array.Sort%2A?displayProperty=nameWithType>
- <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType>
- <xref:System.Collections.IComparer>
- [Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
