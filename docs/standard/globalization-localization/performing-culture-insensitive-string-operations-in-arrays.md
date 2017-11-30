---
title: "Dizilerde Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- culture-insensitive string operations, in arrays
- arrays [.NET Framework], culture-insensitive string operations
- comparer parameter
ms.assetid: f12922e1-6234-4165-8896-63f0653ab478
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1b4e040ed379cdbf43fbe8b2c4379fdd4dc781f2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="performing-culture-insensitive-string-operations-in-arrays"></a>Dizilerde Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme
Overloads <xref:System.Array.Sort%2A?displayProperty=nameWithType> ve <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> yöntemleri kullanarak varsayılan kültüre duyarlı sıralar gerçekleştirmek <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> özelliği. Bu yöntemler tarafından döndürülen kültüre duyarlı sonuçları sıralamalar farklılıkları nedeniyle kültür göre farklılık gösterebilir. Kültüre duyarlı davranışı ortadan kaldırmak için kabul bu yöntem aşırı birini kullanın bir `comparer` parametresi. `comparer` Parametresi belirtir <xref:System.Collections.IComparer> dizideki öğeler karşılaştırılırken kullanmak için uygulama. Kullanan bir özel değişmez karşılaştırıcı sınıfı parametresi için belirlediğiniz <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>. Özel sabit karşılaştırıcı sınıf örneği "SortedList sınıfı kullanarak" konu sağlanan [koleksiyonlarda kültüre duyarsız dize işlemlerini gerçekleştirme](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) konu.  
  
 **Not** geçirme **CultureInfo.InvariantCulture** karşılaştırma yöntemi kültüre duyarsız bir karşılaştırma işlemini gerçekleştirir. Ancak, bu dile ait olmayan bir karşılaştırma, örneğin, dosya yolları, kayıt defteri anahtarları ve ortam değişkenleri için neden olmaz. Güvenlik kararları karşılaştırma sonucuna desteklemiyor. Dil olmayan karşılaştırma veya sonuç tabanlı güvenlik kararları desteği için uygulama kabul eden bir karşılaştırma yöntemi kullanması gereken bir <xref:System.StringComparison> değeri. Uygulama sonra geçirmelisiniz <xref:System.StringComparison.Ordinal>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Array.Sort%2A?displayProperty=nameWithType>  
 <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType>  
 <xref:System.Collections.IComparer>  
 [Kültüre duyarsız dize işlemlerini gerçekleştirme](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
