---
title: .NET 'teki dizeleri karşılaştırma
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- value comparisons of strings
- LastIndexOf method
- CompareTo method
- IndexOf method
- Compare method
- strings [.NET Framework], comparing
- CompareOrdinal method
- EndsWith method
- Equals method
- StartsWith method
ms.assetid: 977dc094-fe19-4955-98ec-d2294d04a4ba
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dd5ec18147c074400457581618bacba11d9ee40a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963415"
---
# <a name="comparing-strings-in-net"></a>.NET 'teki dizeleri karşılaştırma
.NET, dizelerin değerlerini karşılaştırmak için çeşitli yöntemler sağlar. Aşağıdaki tabloda değer karşılaştırma yöntemleri listelenmekte ve açıklanmaktadır.  
  
|Yöntem adı|Bir yönetim grubuna bağlanmak veya bağlı bir yönetim grubunun özelliklerini düzenlemek için Yönetim çalışma alanında|  
|-----------------|---------|  
|<xref:System.String.Compare%2A?displayProperty=nameWithType>|İki dizenin değerlerini karşılaştırır. Bir tamsayı değeri döndürür.|  
|<xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType>|Yerel kültürle ilgili olmadan iki dizeyi karşılaştırır. Bir tamsayı değeri döndürür.|  
|<xref:System.String.CompareTo%2A?displayProperty=nameWithType>|Geçerli dize nesnesini başka bir dizeyle karşılaştırır. Bir tamsayı değeri döndürür.|  
|<xref:System.String.StartsWith%2A?displayProperty=nameWithType>|Bir dizenin geçilen dizeyle başlayıp başlamadığını belirler. Bir Boolean değer döndürür.|  
|<xref:System.String.EndsWith%2A?displayProperty=nameWithType>|Bir dizenin geçtiğini dize ile bitip bitmeyeceğini belirler. Bir Boolean değer döndürür.|  
|<xref:System.String.Equals%2A?displayProperty=nameWithType>|İki dizenin aynı olup olmadığını belirler. Bir Boolean değer döndürür.|  
|<xref:System.String.IndexOf%2A?displayProperty=nameWithType>|İncelediğiniz dizenin başından başlayarak bir karakterin veya dizenin dizin konumunu döndürür. Bir tamsayı değeri döndürür.|  
|<xref:System.String.LastIndexOf%2A?displayProperty=nameWithType>|İncelediğiniz dizenin sonundan başlayarak bir karakterin veya dizenin dizin konumunu döndürür. Bir tamsayı değeri döndürür.|  
  
## <a name="compare"></a>{1&gt;Karşılaştır&lt;1}  
 Statik <xref:System.String.Compare%2A?displayProperty=nameWithType> Yöntem, iki dizeyi karşılaştıran kapsamlı bir yol sağlar. Bu yöntem, önemli ölçüde farkında değildir. Bu işlevi, iki dizenin iki dizesini veya alt dizelerini karşılaştırmak için kullanabilirsiniz. Ek olarak, büyük/küçük harf ve kültürel varyansı dikkate alan veya gözardı eden aşırı yüklemeler Aşağıdaki tabloda, bu yöntemin döndürebileceğini üç tamsayı değeri gösterilmektedir.  
  
|Dönüş değeri|Koşul|  
|------------------|---------------|  
|Negatif bir tamsayı|İlk dize sıralama düzeninde ikinci dizeden önce gelir.<br /><br /> -veya-<br /><br /> İlk dize `null`.|  
|0|İlk dize ve ikinci dize eşittir.<br /><br /> -veya-<br /><br /> Her iki dize `null`de.|  
|Pozitif bir tamsayı<br /><br /> -veya-<br /><br /> 1\.|İlk dize sıralama düzeninde ikinci dizeyi izler.<br /><br /> -veya-<br /><br /> İkinci dize `null`.|  
  
> [!IMPORTANT]
> Yöntemi <xref:System.String.Compare%2A?displayProperty=nameWithType> , birincil olarak dizeleri sıralama veya sıralama sırasında kullanılmak üzere tasarlanmıştır. Eşitlik için test etmek için <xref:System.String.Compare%2A?displayProperty=nameWithType> yöntemini kullanmamalısınız (yani, bir dizenin diğerine göre veya ondan daha büyük olup olmadığı konusunda hiçbir şekilde 0 dönüş değerini açıkça araması için). Bunun yerine, iki dizenin eşit olup olmadığını anlamak için <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> yöntemini kullanın.  
  
 Aşağıdaki örnek, iki dizenin <xref:System.String.Compare%2A?displayProperty=nameWithType> göreli değerlerini belirlemede yöntemini kullanır.  
  
 [!code-cpp[Conceptual.String.BasicOps#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#6)]
 [!code-csharp[Conceptual.String.BasicOps#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#6)]
 [!code-vb[Conceptual.String.BasicOps#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#6)]  
  
 Bu örnek konsola `-1` görüntülenir.  
  
 Yukarıdaki örnek, varsayılan olarak kültüre duyarlıdır. Kültüre duyarsız bir dize karşılaştırması gerçekleştirmek için, bir *kültür* parametresi sağlayarak kullanılacak kültürü <xref:System.String.Compare%2A?displayProperty=nameWithType> belirtmenize izin veren yönteminin bir aşırı yüklemesini kullanın. Kültüre duyarsız bir karşılaştırma gerçekleştirmek için <xref:System.String.Compare%2A?displayProperty=nameWithType> yönteminin nasıl kullanılacağını gösteren bir örnek için bkz. [kültüre duyarsız dize karşılaştırmaları gerçekleştirme](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-comparisons.md).  
  
## <a name="compareordinal"></a>CompareOrdinal  
 Yöntemi <xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType> , yerel kültürü düşünmeksizin iki dize nesnesini karşılaştırır. Bu yöntemin dönüş değerleri, önceki tabloda **Compare** yöntemi tarafından döndürülen değerlerle aynıdır.  
  
> [!IMPORTANT]
> Yöntemi <xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType> , birincil olarak dizeleri sıralama veya sıralama sırasında kullanılmak üzere tasarlanmıştır. Eşitlik için test etmek için <xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType> yöntemini kullanmamalısınız (yani, bir dizenin diğerine göre veya ondan daha büyük olup olmadığı konusunda hiçbir şekilde 0 dönüş değerini açıkça araması için). Bunun yerine, iki dizenin eşit olup olmadığını anlamak için <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> yöntemini kullanın.  
  
 Aşağıdaki örnek, iki dizenin değerlerini karşılaştırmak için **CompareOrdinal** yöntemini kullanır.  
  
 [!code-cpp[Conceptual.String.BasicOps#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#7)]
 [!code-csharp[Conceptual.String.BasicOps#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#7)]
 [!code-vb[Conceptual.String.BasicOps#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#7)]  
  
 Bu örnek konsola `-32` görüntülenir.  
  
## <a name="compareto"></a>CompareTo  
 <xref:System.String.CompareTo%2A?displayProperty=nameWithType> Yöntemi, geçerli dize nesnesinin sarmaladığı dizeyi başka bir dize veya nesne ile karşılaştırır. Bu yöntemin dönüş değerleri, önceki tabloda <xref:System.String.Compare%2A?displayProperty=nameWithType> yöntemi tarafından döndürülen değerlerle aynıdır.  
  
> [!IMPORTANT]
> Yöntemi <xref:System.String.CompareTo%2A?displayProperty=nameWithType> , birincil olarak dizeleri sıralama veya sıralama sırasında kullanılmak üzere tasarlanmıştır. Eşitlik için test etmek için <xref:System.String.CompareTo%2A?displayProperty=nameWithType> yöntemini kullanmamalısınız (yani, bir dizenin diğerine göre veya ondan daha büyük olup olmadığı konusunda hiçbir şekilde 0 dönüş değerini açıkça araması için). Bunun yerine, iki dizenin eşit olup olmadığını anlamak için <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> yöntemini kullanın.  
  
 Aşağıdaki örnek, <xref:System.String.CompareTo%2A?displayProperty=nameWithType> `string1` nesnesini `string2` nesnesiyle karşılaştırmak için yöntemini kullanır.  
  
 [!code-cpp[Conceptual.String.BasicOps#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#8)]
 [!code-csharp[Conceptual.String.BasicOps#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#8)]
 [!code-vb[Conceptual.String.BasicOps#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#8)]  
  
 Bu örnek konsola `-1` görüntülenir.  
  
 <xref:System.String.CompareTo%2A?displayProperty=nameWithType> Metodun tüm aşırı yüklemeleri varsayılan olarak kültüre duyarlı ve büyük/küçük harfe duyarlı karşılaştırmalar gerçekleştirir. Kültüre duyarsız bir karşılaştırma gerçekleştirmenize olanak tanıyan bu yöntemin hiçbir aşırı yüklemesi sağlanmaz. Kod netliği için, kültür duyarlı işlemler veya <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> kültüre duyarsız işlemler için belirtmek <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> yerine **String. Compare** yöntemini kullanmanızı öneririz. Her iki kültüre duyarlı ve kültüre duyarsız karşılaştırmalar gerçekleştirmek için **String. Compare** metodunu nasıl kullanacağınızı gösteren örnekler için bkz. [kültüre duyarsız dize karşılaştırmaları gerçekleştirme](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-comparisons.md).  
  
## <a name="equals"></a>Eşittir  
 **String. Equals** yöntemi, iki dizenin aynı olup olmadığını kolayca belirleyebilir. Bu büyük/küçük harfe duyarlı Yöntem, **doğru** veya **yanlış** Boole değeri döndürür. Sonraki örnekte gösterildiği gibi mevcut bir sınıftan kullanılabilir. Aşağıdaki örnek, bir dize nesnesinin "Merhaba Dünya" ifadesini içerip içermediğini anlamak için **Equals** yöntemini kullanır.  
  
 [!code-cpp[Conceptual.String.BasicOps#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#9)]
 [!code-csharp[Conceptual.String.BasicOps#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#9)]
 [!code-vb[Conceptual.String.BasicOps#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#9)]  
  
 Bu örnek konsola `True` görüntülenir.  
  
 Bu yöntem, statik bir yöntem olarak da kullanılabilir. Aşağıdaki örnek, statik bir yöntem kullanarak iki dize nesnesini karşılaştırır.  
  
 [!code-cpp[Conceptual.String.BasicOps#10](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#10)]
 [!code-csharp[Conceptual.String.BasicOps#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#10)]
 [!code-vb[Conceptual.String.BasicOps#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#10)]  
  
 Bu örnek konsola `True` görüntülenir.  
  
## <a name="startswith-and-endswith"></a>StartsWith ve EndsWith  
 String **. StartsWith** metodunu kullanarak, bir dize nesnesinin başka bir dizeyi çevreleyen karakterlerle başlayıp başlamamadığını belirleyebilirsiniz. Bu büyük/küçük harf duyarlı Yöntem, geçerli dize nesnesi geçen dizeyle başlıyorsa **true** , değilse **false** döndürür. Aşağıdaki örnek, bir dize nesnesinin "Hello" ile başlayıp başlamadığını anlamak için bu yöntemi kullanır.  
  
 [!code-cpp[Conceptual.String.BasicOps#11](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#11)]
 [!code-csharp[Conceptual.String.BasicOps#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#11)]
 [!code-vb[Conceptual.String.BasicOps#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#11)]  
  
 Bu örnek konsola `True` görüntülenir.  
  
 **String. EndsWith** yöntemi, geçirilen bir dizeyi geçerli dize nesnesinin sonunda bulunan karakterlerle karşılaştırır. Ayrıca bir Boole değeri döndürür. Aşağıdaki örnek, **EndsWith** metodunu kullanarak bir dizenin sonunu denetler.  
  
 [!code-cpp[Conceptual.String.BasicOps#12](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#12)]
 [!code-csharp[Conceptual.String.BasicOps#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#12)]
 [!code-vb[Conceptual.String.BasicOps#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#12)]  
  
 Bu örnek konsola `False` görüntülenir.  
  
## <a name="indexof-and-lastindexof"></a>IndexOf ve LastIndexOf  
 Bir dize içindeki belirli bir karakterin ilk geçtiği konumu bulmak için **String. IndexOf** yöntemini kullanabilirsiniz. Bu büyük/küçük harf duyarlı Yöntem bir dizenin başından itibaren sayıma başlar ve sıfır tabanlı bir dizin kullanarak geçen karakterin konumunu döndürür. Karakter bulunamazsa – 1 değeri döndürülür.  
  
 Aşağıdaki örnek, bir dizedeki '`l`' karakterinin ilk oluşumunu aramak için IndexOf metodunu kullanır.  
  
 [!code-cpp[Conceptual.String.BasicOps#13](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#13)]
 [!code-csharp[Conceptual.String.BasicOps#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#13)]
 [!code-vb[Conceptual.String.BasicOps#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#13)]  
  
 Bu örnek konsola `2` görüntülenir.  
  
 String **. LastIndexOf** yöntemi String **. IndexOf** yöntemine benzer, ancak bir dize içindeki belirli bir karakterin son geçtiği konumu döndürür. Büyük/küçük harfe duyarlıdır ve sıfır tabanlı bir dizin kullanır.  
  
 Aşağıdaki örnek, bir dizedeki '`l`' karakterinin son oluşumunu aramak için **LastIndexOf** metodunu kullanır.  
  
 [!code-cpp[Conceptual.String.BasicOps#14](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#14)]
 [!code-csharp[Conceptual.String.BasicOps#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#14)]
 [!code-vb[Conceptual.String.BasicOps#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#14)]  
  
 Bu örnek konsola `9` görüntülenir.  
  
 Her iki yöntem de **String. Remove** yöntemiyle birlikte kullanıldığında yararlıdır. Bir karakterin konumunu almak için **IndexOf** veya **LastIndexOf** yöntemlerini kullanabilir ve sonra bu karakterle başlayan bir karakteri ya da kelimeyi kaldırmak için bu konumu **Remove** yöntemine sağlayabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Temel Dize İşlemleri](../../../docs/standard/base-types/basic-string-operations.md)
- [Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
- [Sıralama ağırlığı tabloları (Windows üzerinde .NET için)](https://www.microsoft.com/download/details.aspx?id=10921)
- [Varsayılan Unicode harmanlama öğesi tablosu (Linux ve macOS 'ta .NET Core için)](https://www.unicode.org/Public/UCA/latest/allkeys.txt)
