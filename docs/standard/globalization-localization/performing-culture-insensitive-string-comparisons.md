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
ms.openlocfilehash: 85ba91b63ab0edbccc768e2d1ad4aaef31fd2f21
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73120826"
---
# <a name="performing-culture-insensitive-string-comparisons"></a>Kültüre Duyarsız Dize Karşılaştırmalarını Gerçekleştirme
Varsayılan olarak, <xref:System.String.Compare%2A?displayProperty=nameWithType> yöntem kültüre duyarlı ve büyük/küçük harf duyarlı karşılaştırmalar gerçekleştirir. Bu yöntem, kullanılacak kültürü belirtmenize olanak tanıyan bir `culture` parametre ve `comparisonType` kullanılacak karşılaştırma kurallarını belirtmenize olanak tanıyan bir parametre sağlayan birkaç aşırı yükleme de içerir. Varsayılan tekrar yükleme yerine bu yöntemleri çağırmak, belirli bir yöntem çağrısında kullanılan kurallarla ilgili tüm belirsizlikleri kaldırır ve belirli bir karşılaştırmanın kültüre duyarlı veya kültüre duyarsız olduğunu netleştirir.  
  
> [!NOTE]
> Yöntemin <xref:System.String.CompareTo%2A?displayProperty=nameWithType> her iki aşırı yükleri kültüre duyarlı ve büyük/küçük harf duyarlı karşılaştırmalar gerçekleştirir; kültüre duyarsız karşılaştırmalar yapmak için bu yöntemi kullanamazsınız. Kod netliği için, <xref:System.String.Compare%2A?displayProperty=nameWithType> bunun yerine yöntemi kullanmanızı öneririz.  
  
 Kültüre duyarlı işlemler için, parametre olarak <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType> veya `comparisonType` <xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType> numaralandırma değerini belirtin. Geçerli kültür dışında belirlenmiş bir kültür kullanarak kültüre duyarlı bir karşılaştırma <xref:System.Globalization.CultureInfo> yapmak istiyorsanız, bu `culture` kültürü parametre olarak temsil eden nesneyi belirtin.  
  
 <xref:System.String.Compare%2A?displayProperty=nameWithType> Yöntem tarafından desteklenen kültürduyarsız dize karşılaştırmaları ya dilsel (değişmez kültürün sıralama kurallarıdayalı) ya da non-linguistic (dize karakterlerin ordinal değerine dayalı). Kültüre duyarsız dize karşılaştırmalarının çoğu dilsel değildir. Bu karşılaştırmalar için, <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> parametre olarak veya `comparisonType` numaralandırma değerini belirtin. Örneğin, bir güvenlik kararı (bir kullanıcı adı ve parola karşılaştırması gibi) bir dize karşılaştırmasının sonucuna dayalıysa, sonucun belirli bir kültürün veya dilin kurallarından etkilenmemesi için, işlemin kültüre duyarsız olması ve dilsel olmaması gerekir.  
  
 Birden çok kültürden alınan dilsel olarak gerekli dizeleri tutarlı bir şekilde işlemek isterseniz, kültüre duyarsız dile dize karşılaştırması kullanın. Örneğin, uygulamanız bir liste kutusunda birden çok karakter kümesi kullanan sözcükler görüntülerse, geçerli kültüre bakılmaksızın, sözcükleri aynı sırada görüntülemek istersiniz. Kültüre duyarsız dilsel karşılaştırmalar için, .NET Framework İngilizce dil kurallarına dayalı sabit bir kültür tanımlar. Kültüre duyarsız dilsel karşılaştırma yapmak <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType> <xref:System.StringComparison.InvariantCultureIgnoreCase?displayProperty=nameWithType> için `comparisonType` parametre olarak belirtiniz veya belirtiniz.  
  
 Aşağıdaki örnek, iki kültüre duyarsız, dilsel olmayan dize karşılaştırması gerçekleştirir. Birincisi büyük/küçük harfe duyarlıdır, ancak ikinci değildir.  
  
 [!code-csharp[Conceptual.Strings.CultureInsensitiveComparison#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.cultureinsensitivecomparison/cs/cultureinsensitive1.cs#1)]
 [!code-vb[Conceptual.Strings.CultureInsensitiveComparison#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.cultureinsensitivecomparison/vb/cultureinsensitive1.vb#1)]  

Windows işletim sistemleri için sıralama ve karşılaştırma işlemlerinde kullanılan karakter ağırlıkları hakkında bilgi içeren bir metin dosyası kümesi olan [Sıralama Ağırlık Tabloları](https://www.microsoft.com/download/details.aspx?id=10921)ve Linux ve macOS için sıralama ağırlık tablosu olan Varsayılan [Unicode Collation Element Table'ı](https://www.unicode.org/Public/UCA/latest/allkeys.txt)indirebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.String.Compare%2A?displayProperty=nameWithType>
- <xref:System.String.CompareTo%2A?displayProperty=nameWithType>
- [Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
- [Dizeleri Kullanmak için En İyi Uygulamalar](../../../docs/standard/base-types/best-practices-strings.md)
