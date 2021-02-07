---
description: 'Hakkında daha fazla bilgi edinin: diziler içinde Culture-Insensitive dize Işlemleri gerçekleştirme'
title: Dizilerde Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme
ms.date: 03/30/2017
helpviewer_keywords:
- culture-insensitive string operations, in arrays
- arrays [.NET], culture-insensitive string operations
- comparer parameter
ms.assetid: f12922e1-6234-4165-8896-63f0653ab478
ms.openlocfilehash: 35c9ceea3c8de45cc37ff14cf14704268c848a5f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99675734"
---
# <a name="performing-culture-insensitive-string-operations-in-arrays"></a>Dizilerde Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme

Ve yöntemlerinin aşırı yüklemeleri, <xref:System.Array.Sort%2A?displayProperty=nameWithType> <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> özelliğini kullanarak varsayılan olarak kültüre duyarlı sıralar gerçekleştirir <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> . Bu yöntemler tarafından döndürülen kültüre duyarlı sonuçlar, sıralama emirlerindeki farklılıklar nedeniyle kültüre göre farklılık gösterebilir. Kültüre duyarlı davranışı ortadan kaldırmak için, bu yöntemin bir parametreyi kabul eden aşırı yüklemelerinin birini kullanın `comparer` . `comparer`Parametresi <xref:System.Collections.IComparer> dizideki öğeleri karşılaştırırken kullanılacak uygulamayı belirtir. Parametresi için, tarafından kullanılan özel bir sabit karşılaştırıcı sınıfı belirtin <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> . [Koleksiyonlarda Culture-Insensitive dize Işlemleri gerçekleştirme](performing-culture-insensitive-string-operations-in-collections.md) konusunun "SortedList sınıfını kullanma" alt konusunun özel bir sabit karşılaştırıcı sınıfına bir örnek verilmiştir.

> [!NOTE]
> Bir karşılaştırma yöntemine **CultureInfo. InvariantCulture** geçirilmesi, kültüre duyarsız bir karşılaştırma gerçekleştirir. Ancak, dosya yolları, kayıt defteri anahtarları ve ortam değişkenleri gibi dil olmayan bir karşılaştırmaya neden olmaz. , Karşılaştırma sonucuna göre güvenlik kararlarını desteklemez. Dil olmayan bir karşılaştırma veya sonuç tabanlı güvenlik kararları için destek için, uygulamanın bir değeri kabul eden bir karşılaştırma yöntemi kullanması gerekir <xref:System.StringComparison> . Uygulama daha sonra geçmelidir <xref:System.StringComparison.Ordinal> .

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Array.Sort%2A?displayProperty=nameWithType>
- <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType>
- <xref:System.Collections.IComparer>
- [Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme](performing-culture-insensitive-string-operations.md)
