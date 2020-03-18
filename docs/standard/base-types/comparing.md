---
title: .NET'te Dizeleri Karşılaştırma
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
ms.openlocfilehash: e63b2a8ac44d6171f9c48990882780ea420f8c76
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73101665"
---
# <a name="comparing-strings-in-net"></a>.NET'te Dizeleri Karşılaştırma
.NET dizeleri değerlerini karşılaştırmak için çeşitli yöntemler sağlar. Aşağıdaki tablo listeler ve değer karşılaştırma yöntemleri açıklanır.  
  
|Yöntem adı|Kullanım|  
|-----------------|---------|  
|<xref:System.String.Compare%2A?displayProperty=nameWithType>|İki dizenin değerlerini karşılaştırır. Bir sonda değeri verir.|  
|<xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType>|Yerel kültüre bakılmaksızın iki dizeyi karşılaştırır. Bir sonda değeri verir.|  
|<xref:System.String.CompareTo%2A?displayProperty=nameWithType>|Geçerli dize nesnesini başka bir dizeyle karşılaştırır. Bir sonda değeri verir.|  
|<xref:System.String.StartsWith%2A?displayProperty=nameWithType>|Bir dize geçirilen dize ile başlar olup olmadığını belirler. Boolean değerini döndürür.|  
|<xref:System.String.EndsWith%2A?displayProperty=nameWithType>|Bir dize dize geçti ile sona erer olup olmadığını belirler. Boolean değerini döndürür.|  
|<xref:System.String.Equals%2A?displayProperty=nameWithType>|İki dize aynı olup olmadığını belirler. Boolean değerini döndürür.|  
|<xref:System.String.IndexOf%2A?displayProperty=nameWithType>|İncelediğiniz dizenin başından başlayarak bir karakterin veya dizenin dizin konumunu döndürür. Bir sonda değeri verir.|  
|<xref:System.String.LastIndexOf%2A?displayProperty=nameWithType>|İncelediğiniz dizenin sonundan başlayarak bir karakterin veya dizenin dizin konumunu döndürür. Bir sonda değeri verir.|  
  
## <a name="compare"></a>Karşılaştır  
 Statik <xref:System.String.Compare%2A?displayProperty=nameWithType> yöntem, iki dizeleri karşılaştırmanın tam bir yolunu sağlar. Bu yöntem kültürel olarak farkındadır. Bu işlevi, iki dizeden iki dize veya alt dizeleri karşılaştırmak için kullanabilirsiniz. Ayrıca, aşırı yükler dikkate alma veya durum ve kültürel varyans göz ardı sağlanır. Aşağıdaki tablo, bu yöntemin dönebileceği üç tamsayı değerini gösterir.  
  
|Döndürülen değer|Koşul|  
|------------------|---------------|  
|Negatif bir tamsayı|İlk dize sıralama sırasına göre ikinci dizeden önce gelir.<br /><br /> -veya-<br /><br /> İlk dize. `null`|  
|0|Birinci dize ve ikinci dize eşittir.<br /><br /> -veya-<br /><br /> Her iki `null`dize de.|  
|Pozitif bir tamsayı<br /><br /> -veya-<br /><br /> 1|İlk dize sıralama sırasına göre ikinci dize izler.<br /><br /> -veya-<br /><br /> İkinci dize. `null`|  
  
> [!IMPORTANT]
> Yöntem, <xref:System.String.Compare%2A?displayProperty=nameWithType> öncelikle dizeleri sıralarken veya sıralarken kullanılmak üzere tasarlanmıştır. Eşitliği sınamak <xref:System.String.Compare%2A?displayProperty=nameWithType> için yöntemi kullanmamalısınız (diğer bir deyişle, bir dize diğerinden daha az veya daha büyük olup olmadığına bakılmaksızın açıkça 0'ın geri dönüş değerini aramak için). Bunun yerine, iki dize eşit olup <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> olmadığını belirlemek için yöntemi kullanın.  
  
 Aşağıdaki örnek, <xref:System.String.Compare%2A?displayProperty=nameWithType> iki dize göreli değerlerini belirlemek için yöntemi kullanır.  
  
 [!code-cpp[Conceptual.String.BasicOps#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#6)]
 [!code-csharp[Conceptual.String.BasicOps#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#6)]
 [!code-vb[Conceptual.String.BasicOps#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#6)]  
  
 Bu örnek `-1` konsola görüntülenir.  
  
 Önceki örnek varsayılan olarak kültüre duyarlıdır. Kültüre duyarlı bir dize karşılaştırması yapmak için, bir <xref:System.String.Compare%2A?displayProperty=nameWithType> *kültür* parametresi sağlayarak kullanılacak kültürü belirtmenize olanak tanıyan yöntemin aşırı yüklenmesini kullanın. Kültüre duyarsız bir karşılaştırma yapmak <xref:System.String.Compare%2A?displayProperty=nameWithType> için yöntemin nasıl kullanılacağını gösteren bir örnek [için](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-comparisons.md)bkz.  
  
## <a name="compareordinal"></a>KarşılaştırmaOrdinal  
 Yöntem, <xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType> yerel kültürü düşünmeden iki dize nesnesini karşılaştırır. Bu yöntemin dönüş değerleri, önceki tablodaki **Karşılaştırma** yöntemi yle döndürülen değerlerle aynıdır.  
  
> [!IMPORTANT]
> Yöntem, <xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType> öncelikle dizeleri sıralarken veya sıralarken kullanılmak üzere tasarlanmıştır. Eşitliği sınamak <xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType> için yöntemi kullanmamalısınız (diğer bir deyişle, bir dize diğerinden daha az veya daha büyük olup olmadığına bakılmaksızın açıkça 0'ın geri dönüş değerini aramak için). Bunun yerine, iki dize eşit olup <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> olmadığını belirlemek için yöntemi kullanın.  
  
 Aşağıdaki örnekte, iki dizenin değerlerini karşılaştırmak için **CompareOrdinal** yöntemi ni kullanır.  
  
 [!code-cpp[Conceptual.String.BasicOps#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#7)]
 [!code-csharp[Conceptual.String.BasicOps#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#7)]
 [!code-vb[Conceptual.String.BasicOps#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#7)]  
  
 Bu örnek `-32` konsola görüntülenir.  
  
## <a name="compareto"></a>karşılaştırmak  
 Yöntem, <xref:System.String.CompareTo%2A?displayProperty=nameWithType> geçerli dize nesnesinin kapsülletiyi başka bir dize veya nesneyle karşılaştırır. Bu yöntemin dönüş değerleri, önceki tabloda <xref:System.String.Compare%2A?displayProperty=nameWithType> yöntem tarafından döndürülen değerlerle aynıdır.  
  
> [!IMPORTANT]
> Yöntem, <xref:System.String.CompareTo%2A?displayProperty=nameWithType> öncelikle dizeleri sıralarken veya sıralarken kullanılmak üzere tasarlanmıştır. Eşitliği sınamak <xref:System.String.CompareTo%2A?displayProperty=nameWithType> için yöntemi kullanmamalısınız (diğer bir deyişle, bir dize diğerinden daha az veya daha büyük olup olmadığına bakılmaksızın açıkça 0'ın geri dönüş değerini aramak için). Bunun yerine, iki dize eşit olup <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> olmadığını belirlemek için yöntemi kullanın.  
  
 Aşağıdaki örnek, <xref:System.String.CompareTo%2A?displayProperty=nameWithType> nesneyi `string1` `string2` nesneyle karşılaştırmak için yöntemi kullanır.  
  
 [!code-cpp[Conceptual.String.BasicOps#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#8)]
 [!code-csharp[Conceptual.String.BasicOps#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#8)]
 [!code-vb[Conceptual.String.BasicOps#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#8)]  
  
 Bu örnek `-1` konsola görüntülenir.  
  
 Yöntemin <xref:System.String.CompareTo%2A?displayProperty=nameWithType> tüm aşırı varsayılan olarak kültüre duyarlı ve büyük/küçük harf duyarlı karşılaştırmalar gerçekleştirir. Kültüre duyarsız bir karşılaştırma gerçekleştirmenize olanak tanıyan bu yöntemin aşırı yüklemesi sağlanmaz. Kod netliği için, kültüre duyarlı işlemler veya <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> kültüre <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> duyarlı işlemler için belirterek **String.Compare** yöntemini kullanmanızı öneririz. Hem kültüre duyarlı hem de kültüre duyarlı olmayan karşılaştırmalar gerçekleştirmek için **String.Compare** yönteminin nasıl kullanılacağını gösteren örnekler [için](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-comparisons.md)bkz.  
  
## <a name="equals"></a>Eşittir  
 **String.Equals** yöntemi, iki dize aynı olup olmadığını kolayca belirleyebilir. Bu büyük/küçük harf duyarlı yöntem **gerçek** veya **yanlış** Boolean değeri döndürür. Bir sonraki örnekte gösterildiği gibi, varolan bir sınıftan kullanılabilir. Aşağıdaki **örnekte,** bir dize nesnesinin "Merhaba Dünya" ifadesini bulunup içermediğini belirlemek için Eşittir yöntemini kullanır.  
  
 [!code-cpp[Conceptual.String.BasicOps#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#9)]
 [!code-csharp[Conceptual.String.BasicOps#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#9)]
 [!code-vb[Conceptual.String.BasicOps#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#9)]  
  
 Bu örnek `True` konsola görüntülenir.  
  
 Bu yöntem statik bir yöntem olarak da kullanılabilir. Aşağıdaki örnek, statik bir yöntem kullanarak iki dize nesnesi karşılaştırır.  
  
 [!code-cpp[Conceptual.String.BasicOps#10](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#10)]
 [!code-csharp[Conceptual.String.BasicOps#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#10)]
 [!code-vb[Conceptual.String.BasicOps#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#10)]  
  
 Bu örnek `True` konsola görüntülenir.  
  
## <a name="startswith-and-endswith"></a>StartsWith ve EndsWith  
 **String.StartsWith** yöntemini kullanarak bir dize nesnesinin başka bir dizeyi kapsayan aynı karakterlerle başlayıp başlamadığını belirleyebilirsiniz. Geçerli dize nesnesi geçirilen dize ile başlar ve değilse **yanlış** bu büyük/küçük harf duyarlı yöntem **doğru** döndürür. Aşağıdaki örnek, bir dize nesnesinin "Merhaba" ile başedip başlamayamasını belirlemek için bu yöntemi kullanır.  
  
 [!code-cpp[Conceptual.String.BasicOps#11](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#11)]
 [!code-csharp[Conceptual.String.BasicOps#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#11)]
 [!code-vb[Conceptual.String.BasicOps#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#11)]  
  
 Bu örnek `True` konsola görüntülenir.  
  
 **String.EndsWith** yöntemi, geçirilen bir dizeyi geçerli dize nesnesinin sonunda bulunan karakterlerle karşılaştırır. Ayrıca bir Boolean değeri döndürür. Aşağıdaki örnek, **EndsWith** yöntemini kullanarak bir dize sonunu denetler.  
  
 [!code-cpp[Conceptual.String.BasicOps#12](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#12)]
 [!code-csharp[Conceptual.String.BasicOps#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#12)]
 [!code-vb[Conceptual.String.BasicOps#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#12)]  
  
 Bu örnek `False` konsola görüntülenir.  
  
## <a name="indexof-and-lastindexof"></a>IndexOf ve LastIndexOf  
 **String.IndexOf** yöntemini, bir dize içinde belirli bir karakterin ilk oluşumunun konumunu belirlemek için kullanabilirsiniz. Bu büyük/küçük harf duyarlı yöntem bir dizenin başından saymaya başlar ve sıfır tabanlı dizin kullanarak geçen bir karakterin konumunu döndürür. Karakter bulunamazsa, -1 değeri döndürülür.  
  
 Aşağıdaki örnek, bir dizedeki ' '`l`karakterinilk oluşumunu aramak için **IndexOf** yöntemini kullanır.  
  
 [!code-cpp[Conceptual.String.BasicOps#13](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#13)]
 [!code-csharp[Conceptual.String.BasicOps#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#13)]
 [!code-vb[Conceptual.String.BasicOps#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#13)]  
  
 Bu örnek `2` konsola görüntülenir.  
  
 **String.LastIndexOf** yöntemi **string.IndexOf** yöntemine benzer, ancak bir dize içinde belirli bir karakterin son oluşumunun konumunu döndürür. Büyük/küçük harf duyarlıdır ve sıfır tabanlı bir dizin kullanır.  
  
 Aşağıdaki örnekte **LastIndexOf** yöntemibir dizedeki '`l`' karakterin son oluşumunu aramak için kullanır.  
  
 [!code-cpp[Conceptual.String.BasicOps#14](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#14)]
 [!code-csharp[Conceptual.String.BasicOps#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#14)]
 [!code-vb[Conceptual.String.BasicOps#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#14)]  
  
 Bu örnek `9` konsola görüntülenir.  
  
 **String.Remove** yöntemi ile birlikte kullanıldığında her iki yöntem de yararlıdır. Bir karakterin konumunu almak için **IndexOf** veya **LastIndexOf** yöntemlerini kullanabilir ve ardından bu karakteri veya bu karakterle başlayan bir sözcüğü kaldırmak için bu konumu **Kaldır** metoduna sağlayabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Temel Dize İşlemleri](../../../docs/standard/base-types/basic-string-operations.md)
- [Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
- [Ağırlık Tablolarını Sıralama (Windows'ta .NET için)](https://www.microsoft.com/download/details.aspx?id=10921)
- [Varsayılan Unicode Collation Element Table (Linux ve macOS'ta .NET Core için)](https://www.unicode.org/Public/UCA/latest/allkeys.txt)
