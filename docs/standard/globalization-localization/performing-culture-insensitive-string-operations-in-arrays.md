---
title: Dizilerde Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- culture-insensitive string operations, in arrays
- arrays [.NET Framework], culture-insensitive string operations
- comparer parameter
ms.assetid: f12922e1-6234-4165-8896-63f0653ab478
ms.openlocfilehash: 051ee77ae5d6552e26e0216d58734d90188475f9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73120801"
---
# <a name="performing-culture-insensitive-string-operations-in-arrays"></a>Dizilerde Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme

Aşırı yükler <xref:System.Array.Sort%2A?displayProperty=nameWithType> ve <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> yöntemler <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> özelliği kullanarak varsayılan olarak kültüre duyarlı sıralamaları gerçekleştirir. Bu yöntemlerle döndürülen kültüre duyarlı sonuçlar, sıralama emirlerindeki farklılıklara bağlı olarak kültüre göre değişiklik gösterebilir. Kültüre duyarlı davranışı ortadan kaldırmak için, parametre `comparer` kabul eden bu yöntemin aşırı yüklerinden birini kullanın. Parametre, `comparer` dizideki <xref:System.Collections.IComparer> öğeleri karşılaştırırken kullanılacak uygulamayı belirtir. Parametre için, kullanan özel değişmez karşılayıcı <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>sınıf belirtin. Özel değişmez karşılaştırıcı sınıfın bir örneği, [Koleksiyonlarda Performans Kültürü-Duyarsız Dize İşlemleri](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) konusunun "Sıralamalı Liste Sınıfını Kullanma" alt başlığında verilmiştir.

> [!NOTE]
> **CultureInfo.InvariantCulture'ı** bir karşılaştırma yöntemine geçirmek kültüre duyarsız bir karşılaştırma yapar. Ancak, dosya yolları, kayıt defteri anahtarları ve ortam değişkenleri gibi dilsel olmayan bir karşılaştırmaya neden olmaz. Karşılaştırma sonucuna göre güvenlik kararlarını da desteklemez. Dilbilimsel olmayan bir karşılaştırma veya sonuç tabanlı güvenlik kararları desteği için, uygulama bir <xref:System.StringComparison> değer kabul eden bir karşılaştırma yöntemi kullanmalıdır. Uygulama daha sonra <xref:System.StringComparison.Ordinal>geçmelidir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Array.Sort%2A?displayProperty=nameWithType>
- <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType>
- <xref:System.Collections.IComparer>
- [Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
