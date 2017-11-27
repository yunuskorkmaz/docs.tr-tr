---
title: "Kültüre Duyarsız Dize Karşılaştırmalarını Gerçekleştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- String.CompareTo method
- String.Compare method
- string comparison [.NET Framework], culture-insensitive
- strings [.NET Framework], comparing
- culture-insensitive string operations, comparisons
- culture parameter
ms.assetid: abae50ef-32f7-4a50-a540-fd256fd1aed0
caps.latest.revision: "23"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 980b4ac515deaaedb1ab7e240e8f110a5fd0d51c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="performing-culture-insensitive-string-comparisons"></a>Kültüre Duyarsız Dize Karşılaştırmalarını Gerçekleştirme
Varsayılan olarak, <xref:System.String.Compare%2A?displayProperty=nameWithType> yöntemi kültüre duyarlı ve büyük küçük harfe duyarlı karşılaştırmaları gerçekleştirir. Bu yöntem de sağlayan birçok aşırı yüklemeye içeren bir `culture` kullanmak için kültür belirtmenize olanak sağlar. parametre ve bir `comparisonType` kullanmak için karşılaştırma kuralları belirtmenize olanak sağlar. parametre. Varsayılan tekrar yükleme yerine bu yöntemleri çağırmak, belirli bir yöntem çağrısında kullanılan kurallarla ilgili tüm belirsizlikleri kaldırır ve belirli bir karşılaştırmanın kültüre duyarlı veya kültüre duyarsız olduğunu netleştirir.  
  
> [!NOTE]
>  Her iki aşırı <xref:System.String.CompareTo%2A?displayProperty=nameWithType> yöntemi kültüre duyarlı ve büyük küçük harfe duyarlı karşılaştırmalar gerçekleştirin; kültüre duyarsız karşılaştırmaları gerçekleştirmek için bu yöntemi kullanamazsınız. Kodu daha anlaşılır olması için kullanmanızı öneririz <xref:System.String.Compare%2A?displayProperty=nameWithType> yöntemi yerine.  
  
 Kültüre duyarlı işlemlerinde belirtin <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType> veya <xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType> numaralandırma değeri olarak `comparisonType` parametresi. Geçerli kültür dışında atanmış bir kültür kullanarak bir kültüre duyarlı karşılaştırma yapmak isterseniz belirtin <xref:System.Globalization.CultureInfo> kültüre olarak temsil eden nesnesi `culture` parametresi.  
  
 Tarafından desteklenen kültüre duyarsız dize karşılaştırmalarını <xref:System.String.Compare%2A?displayProperty=nameWithType> yöntemi olan ya da dil (sabit kültür sıralama kurallarına göre) veya dil olmayan (sıra sayısı değerini dizesindeki karakterlerin bağlı olarak). Kültüre duyarsız dize karşılaştırmalarının çoğu dilsel değildir. Bu Karşılaştırmaların belirtin <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> veya <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> numaralandırma değeri olarak `comparisonType` parametresi. Örneğin, bir güvenlik kararı (bir kullanıcı adı ve parola karşılaştırması gibi) bir dize karşılaştırmasının sonucuna dayalıysa, sonucun belirli bir kültürün veya dilin kurallarından etkilenmemesi için, işlemin kültüre duyarsız olması ve dilsel olmaması gerekir.  
  
 Birden çok kültürden alınan dilsel olarak gerekli dizeleri tutarlı bir şekilde işlemek isterseniz, kültüre duyarsız dile dize karşılaştırması kullanın. Örneğin, uygulamanız bir liste kutusunda birden çok karakter kümesi kullanan sözcükler görüntülerse, geçerli kültüre bakılmaksızın, sözcükleri aynı sırada görüntülemek istersiniz. Kültüre duyarsız dilsel karşılaştırmalar için, .NET Framework İngilizce dil kurallarına dayalı sabit bir kültür tanımlar. Kültüre duyarsız bir dil karşılaştırma yapabilmesi için belirtmek <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType> veya <xref:System.StringComparison.InvariantCultureIgnoreCase?displayProperty=nameWithType> olarak `comparisonType` parametresi.  
  
 Aşağıdaki örnek, iki kültüre duyarsız, dilsel olmayan dize karşılaştırması gerçekleştirir. Birincisi büyük/küçük harfe duyarlıdır, ancak ikinci değildir.  
  
 [!code-csharp[Conceptual.Strings.CultureInsensitiveComparison#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.cultureinsensitivecomparison/cs/cultureinsensitive1.cs#1)]
 [!code-vb[Conceptual.Strings.CultureInsensitiveComparison#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.cultureinsensitivecomparison/vb/cultureinsensitive1.vb#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.String.Compare%2A?displayProperty=nameWithType>  
 <xref:System.String.CompareTo%2A?displayProperty=nameWithType>  
 [Kültüre duyarsız dize işlemlerini gerçekleştirme](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)  
 [Dizeleri kullanmak için en iyi uygulamalar](../../../docs/standard/base-types/best-practices-strings.md)
