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
ms.openlocfilehash: 91996bc721db55b24521be97e4d9accd53ef7924
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288621"
---
# <a name="performing-culture-insensitive-string-comparisons"></a>Kültüre Duyarsız Dize Karşılaştırmalarını Gerçekleştirme
Varsayılan olarak, <xref:System.String.Compare%2A?displayProperty=nameWithType> Yöntem kültüre duyarlı ve büyük/küçük harfe duyarlı karşılaştırmalar gerçekleştirir. Bu yöntemde Ayrıca kullanılacak kültürü belirtmenize imkan tanıyan bir parametre sağlayan çeşitli aşırı yüklemeler `culture` ve `comparisonType` kullanılacak karşılaştırma kurallarını belirtmenizi sağlayan bir parametre bulunur. Varsayılan tekrar yükleme yerine bu yöntemleri çağırmak, belirli bir yöntem çağrısında kullanılan kurallarla ilgili tüm belirsizlikleri kaldırır ve belirli bir karşılaştırmanın kültüre duyarlı veya kültüre duyarsız olduğunu netleştirir.  
  
> [!NOTE]
> Metodun her iki aşırı yüklemesi de <xref:System.String.CompareTo%2A?displayProperty=nameWithType> kültüre duyarlı ve büyük/küçük harfe duyarlı karşılaştırmalar gerçekleştirir; kültüre duyarsız karşılaştırmalar gerçekleştirmek için bu yöntemi kullanamazsınız. Kod netliği için, <xref:System.String.Compare%2A?displayProperty=nameWithType> bunun yerine yöntemini kullanmanızı öneririz.  
  
 Kültüre duyarlı işlemler için <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType> <xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType> parametresi olarak veya numaralandırma değerini belirtin `comparisonType` . Geçerli kültür dışında belirlenmiş bir kültür kullanarak kültüre duyarlı bir karşılaştırma gerçekleştirmek istiyorsanız, <xref:System.Globalization.CultureInfo> Bu kültürü temsil eden nesneyi parametresi olarak belirtin `culture` .  
  
 Yöntemi tarafından desteklenen kültüre duyarsız dize karşılaştırmaları, <xref:System.String.Compare%2A?displayProperty=nameWithType> Dil (Sabit kültürün sıralama kurallarına göre) veya dil olmayan (dizedeki karakterlerin sıra değerine göre). Kültüre duyarsız dize karşılaştırmalarının çoğu dilsel değildir. Bu karşılaştırmalar için, <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> parametresi olarak veya numaralandırma değerini belirtin `comparisonType` . Örneğin, bir güvenlik kararı (bir kullanıcı adı ve parola karşılaştırması gibi) bir dize karşılaştırmasının sonucuna dayalıysa, sonucun belirli bir kültürün veya dilin kurallarından etkilenmemesi için, işlemin kültüre duyarsız olması ve dilsel olmaması gerekir.  
  
 Birden çok kültürden alınan dilsel olarak gerekli dizeleri tutarlı bir şekilde işlemek isterseniz, kültüre duyarsız dile dize karşılaştırması kullanın. Örneğin, uygulamanız bir liste kutusunda birden çok karakter kümesi kullanan sözcükler görüntülerse, geçerli kültüre bakılmaksızın, sözcükleri aynı sırada görüntülemek istersiniz. Kültüre duyarsız dilsel karşılaştırmalar için, .NET Framework İngilizce dil kurallarına dayalı sabit bir kültür tanımlar. Kültüre duyarsız bir dil karşılaştırması gerçekleştirmek için <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType> <xref:System.StringComparison.InvariantCultureIgnoreCase?displayProperty=nameWithType> parametresi olarak belirtin `comparisonType` .  
  
 Aşağıdaki örnek, iki kültüre duyarsız, dilsel olmayan dize karşılaştırması gerçekleştirir. Birincisi büyük/küçük harfe duyarlıdır, ancak ikinci değildir.  
  
 [!code-csharp[Conceptual.Strings.CultureInsensitiveComparison#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.cultureinsensitivecomparison/cs/cultureinsensitive1.cs#1)]
 [!code-vb[Conceptual.Strings.CultureInsensitiveComparison#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.cultureinsensitivecomparison/vb/cultureinsensitive1.vb#1)]  

[Sıralama ağırlığı tablolarını](https://www.microsoft.com/download/details.aspx?id=10921), Windows işletim sistemleri için sıralama ve karşılaştırma işlemlerinde kullanılan karakter ağırlıkları ve [varsayılan Unicode harmanlama öğesi tablosu](https://www.unicode.org/Public/UCA/latest/allkeys.txt), Linux ve MacOS için sıralama ağırlığı tablosu gibi bilgileri içeren bir metin dosyası kümesi indirebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.String.Compare%2A?displayProperty=nameWithType>
- <xref:System.String.CompareTo%2A?displayProperty=nameWithType>
- [Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme](performing-culture-insensitive-string-operations.md)
- [Dizeleri kullanmak için en iyi uygulamalar](../base-types/best-practices-strings.md)
