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
ms.openlocfilehash: 22815b5ab993b36bc8bcb91f89f346cb6d812e19
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44068761"
---
# <a name="performing-culture-insensitive-string-operations-in-arrays"></a>Dizilerde Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme
Overloads biri <xref:System.Array.Sort%2A?displayProperty=nameWithType> ve <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> yöntemleri gerçekleştirmek varsayılan kullanarak kültüre duyarlı sıralamaları <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> özelliği. Bu yöntem tarafından döndürülen kültüre duyarlı sonuçlar sıralamalar farklılıkları nedeniyle kültüre göre değişebilir. Kültüre duyarlı davranışı ortadan kaldırmak için bu yöntemin kabul eden aşırı yüklemeler birini kullanın: bir `comparer` parametresi. `comparer` Parametresinin belirttiği <xref:System.Collections.IComparer> dizideki öğeleri karşılaştırırken kullanılacak uygulama. Parametresi, kullanan bir özel sabit karşılaştırıcısı sınıfı belirtin <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>. Sabit özel bir karşılaştırıcı sınıf örneği "SortedList sınıfı kullanarak" alt konu sağlanan [koleksiyonlarda kültüre duyarsız dize işlemlerini gerçekleştirme](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) konu.  
  
 **Not** geçirme **CultureInfo.InvariantCulture** karşılaştırma yöntemi kültüre duyarsız bir karşılaştırma gerçekleştirir. Ancak, bir dilsel karşılaştırma örneğin dosya yolları, kayıt defteri anahtarları ve ortam değişkenleri için neden olmaz. Karşılaştırma sonucuna dayalı güvenlik kararları diğerinden destekler. Uygulama, bir dilsel karşılaştırma veya sonuç dayalı güvenlik kararları desteği için kabul eden bir karşılaştırma yöntemi kullanmalıdır bir <xref:System.StringComparison> değeri. Uygulama ardından geçmelidir <xref:System.StringComparison.Ordinal>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Array.Sort%2A?displayProperty=nameWithType>  
- <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType>  
- <xref:System.Collections.IComparer>  
- [Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
