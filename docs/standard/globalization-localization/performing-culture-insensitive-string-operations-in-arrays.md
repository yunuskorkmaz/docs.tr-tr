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
ms.openlocfilehash: f4d732d64eecff72403c455c14b68c3aec1b5407
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33572066"
---
# <a name="performing-culture-insensitive-string-operations-in-arrays"></a>Dizilerde Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme
Overloads <xref:System.Array.Sort%2A?displayProperty=nameWithType> ve <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> yöntemleri kullanarak varsayılan kültüre duyarlı sıralar gerçekleştirmek <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> özelliği. Bu yöntemler tarafından döndürülen kültüre duyarlı sonuçları sıralamalar farklılıkları nedeniyle kültür göre farklılık gösterebilir. Kültüre duyarlı davranışı ortadan kaldırmak için kabul bu yöntem aşırı birini kullanın bir `comparer` parametresi. `comparer` Parametresi belirtir <xref:System.Collections.IComparer> dizideki öğeler karşılaştırılırken kullanmak için uygulama. Kullanan bir özel değişmez karşılaştırıcı sınıfı parametresi için belirlediğiniz <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>. Özel sabit karşılaştırıcı sınıf örneği "SortedList sınıfı kullanarak" konu sağlanan [koleksiyonlarda kültüre duyarsız dize işlemlerini gerçekleştirme](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) konu.  
  
 **Not** geçirme **CultureInfo.InvariantCulture** karşılaştırma yöntemi kültüre duyarsız bir karşılaştırma işlemini gerçekleştirir. Ancak, bu dile ait olmayan bir karşılaştırma, örneğin, dosya yolları, kayıt defteri anahtarları ve ortam değişkenleri için neden olmaz. Güvenlik kararları karşılaştırma sonucuna desteklemiyor. Dil olmayan karşılaştırma veya sonuç tabanlı güvenlik kararları desteği için uygulama kabul eden bir karşılaştırma yöntemi kullanması gereken bir <xref:System.StringComparison> değeri. Uygulama sonra geçirmelisiniz <xref:System.StringComparison.Ordinal>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Array.Sort%2A?displayProperty=nameWithType>  
 <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType>  
 <xref:System.Collections.IComparer>  
 [Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
