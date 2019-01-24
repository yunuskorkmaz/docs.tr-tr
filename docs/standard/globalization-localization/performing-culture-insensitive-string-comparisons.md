---
title: Kültüre Duyarsız Dize Karşılaştırmalarını Gerçekleştirme
ms.date: 08/22/2018
ms.technology: dotnet-standard
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d20ce0f09309c84dcbeb016e0f17c37fe338dd9c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54504099"
---
# <a name="performing-culture-insensitive-string-comparisons"></a>Kültüre Duyarsız Dize Karşılaştırmalarını Gerçekleştirme
Varsayılan olarak, <xref:System.String.Compare%2A?displayProperty=nameWithType> yöntemi kültüre duyarlı ve büyük küçük harfe duyarlı karşılaştırmalar yapar. Bu yöntem sağlayan çeşitli tekrar yüklemeler de içerir. bir `culture` kullanılacak kültürü belirtmenize olanak sağlar. parametre ve bir `comparisonType` parametre kullanılacak karşılaştırma kurallarını belirtmenizi sağlar. Varsayılan tekrar yükleme yerine bu yöntemleri çağırmak, belirli bir yöntem çağrısında kullanılan kurallarla ilgili tüm belirsizlikleri kaldırır ve belirli bir karşılaştırmanın kültüre duyarlı veya kültüre duyarsız olduğunu netleştirir.  
  
> [!NOTE]
>  Her iki aşırı yüklemeleri <xref:System.String.CompareTo%2A?displayProperty=nameWithType> yöntemi kültüre duyarlı ve büyük küçük harfe duyarlı karşılaştırmaları gerçekleştirir; kültüre duyarsız karşılaştırmalar yapmak için bu yöntemi kullanamazsınız. Kod netliği için biz kullanmanızı öneririz. <xref:System.String.Compare%2A?displayProperty=nameWithType> yöntemi yerine.  
  
 Kültüre duyarlı işlemler için belirtin <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType> veya <xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType> numaralandırma değeri olarak `comparisonType` parametresi. Geçerli kültür yerine belirlenmiş bir kültürü kullanarak kültüre duyarlı bir karşılaştırma gerçekleştirmek istiyorsanız belirtin <xref:System.Globalization.CultureInfo> , kültürü temsil eden bir nesne `culture` parametresi.  
  
 Tarafından desteklenen kültüre duyarsız dize karşılaştırmalarını <xref:System.String.Compare%2A?displayProperty=nameWithType> yöntemi dil (sabit kültürün sıralama kurallarına dayalı) veya dilsel olmayan (dizedeki karakterlerin sıralı değerlerine bağlı olarak). Kültüre duyarsız dize karşılaştırmalarının çoğu dilsel değildir. Bu karşılaştırmalar için belirtin <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> veya <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> numaralandırma değeri olarak `comparisonType` parametresi. Örneğin, bir güvenlik kararı (bir kullanıcı adı ve parola karşılaştırması gibi) bir dize karşılaştırmasının sonucuna dayalıysa, sonucun belirli bir kültürün veya dilin kurallarından etkilenmemesi için, işlemin kültüre duyarsız olması ve dilsel olmaması gerekir.  
  
 Birden çok kültürden alınan dilsel olarak gerekli dizeleri tutarlı bir şekilde işlemek isterseniz, kültüre duyarsız dile dize karşılaştırması kullanın. Örneğin, uygulamanız bir liste kutusunda birden çok karakter kümesi kullanan sözcükler görüntülerse, geçerli kültüre bakılmaksızın, sözcükleri aynı sırada görüntülemek istersiniz. Kültüre duyarsız dilsel karşılaştırmalar için, .NET Framework İngilizce dil kurallarına dayalı sabit bir kültür tanımlar. Kültüre duyarsız bir dilsel karşılaştırma için belirtin <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType> veya <xref:System.StringComparison.InvariantCultureIgnoreCase?displayProperty=nameWithType> olarak `comparisonType` parametresi.  
  
 Aşağıdaki örnek, iki kültüre duyarsız, dilsel olmayan dize karşılaştırması gerçekleştirir. Birincisi büyük/küçük harfe duyarlıdır, ancak ikinci değildir.  
  
 [!code-csharp[Conceptual.Strings.CultureInsensitiveComparison#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.cultureinsensitivecomparison/cs/cultureinsensitive1.cs#1)]
 [!code-vb[Conceptual.Strings.CultureInsensitiveComparison#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.cultureinsensitivecomparison/vb/cultureinsensitive1.vb#1)]  

İndirebileceğiniz [sıralama ağırlık tabloları](https://www.microsoft.com/en-us/download/details.aspx?id=10921), sıralama ve karşılaştırma işlemlerinde Windows işletim sistemleri için kullanılan karakter ağırlıkları hakkında bilgi içeren metin dosyalarını bir dizi ve [varsayılan Unicode Harmanlama öğesi tablosu](https://www.unicode.org/Public/UCA/latest/allkeys.txt), Linux ve macOS için sıralama ağırlık tablosu.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.String.Compare%2A?displayProperty=nameWithType>
- <xref:System.String.CompareTo%2A?displayProperty=nameWithType>
- [Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
- [Dizeleri Kullanmak için En İyi Uygulamalar](../../../docs/standard/base-types/best-practices-strings.md)
