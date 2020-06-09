---
title: .NET 'teki dizeleri karşılaştırma
description: .NET 'teki dizeleri karşılaştırmak için yöntemler hakkında bilgi edinin. Compare, CompareOrdinal, CompareTo, StartsWith, EndsWith, eşittir, IndexOf, & LastIndexOf yöntemleri hakkında bilgi edinin.
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
ms.openlocfilehash: 5ed73d18341c3b9c6e61e12fdf322b9a67affd4a
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602199"
---
# <a name="comparing-strings-in-net"></a>.NET 'teki dizeleri karşılaştırma
.NET, dizelerin değerlerini karşılaştırmak için çeşitli yöntemler sağlar. Aşağıdaki tabloda değer karşılaştırma yöntemleri listelenmekte ve açıklanmaktadır.  
  
|Yöntem adı|Kullanım|  
|-----------------|---------|  
|<xref:System.String.Compare%2A?displayProperty=nameWithType>|İki dizenin değerlerini karşılaştırır. Bir tamsayı değeri döndürür.|  
|<xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType>|Yerel kültürle ilgili olmadan iki dizeyi karşılaştırır. Bir tamsayı değeri döndürür.|  
|<xref:System.String.CompareTo%2A?displayProperty=nameWithType>|Geçerli dize nesnesini başka bir dizeyle karşılaştırır. Bir tamsayı değeri döndürür.|  
|<xref:System.String.StartsWith%2A?displayProperty=nameWithType>|Bir dizenin geçilen dizeyle başlayıp başlamadığını belirler. Boole değeri döndürür.|  
|<xref:System.String.EndsWith%2A?displayProperty=nameWithType>|Bir dizenin geçtiğini dize ile bitip bitmeyeceğini belirler. Boole değeri döndürür.|  
|<xref:System.String.Equals%2A?displayProperty=nameWithType>|İki dizenin aynı olup olmadığını belirler. Boole değeri döndürür.|  
|<xref:System.String.IndexOf%2A?displayProperty=nameWithType>|İncelediğiniz dizenin başından başlayarak bir karakterin veya dizenin dizin konumunu döndürür. Bir tamsayı değeri döndürür.|  
|<xref:System.String.LastIndexOf%2A?displayProperty=nameWithType>|İncelediğiniz dizenin sonundan başlayarak bir karakterin veya dizenin dizin konumunu döndürür. Bir tamsayı değeri döndürür.|  
  
## <a name="compare"></a>Karşılaştır  
 Statik <xref:System.String.Compare%2A?displayProperty=nameWithType> Yöntem, iki dizeyi karşılaştıran kapsamlı bir yol sağlar. Bu yöntem, önemli ölçüde farkında değildir. Bu işlevi, iki dizenin iki dizesini veya alt dizelerini karşılaştırmak için kullanabilirsiniz. Ek olarak, büyük/küçük harf ve kültürel varyansı dikkate alan veya gözardı eden aşırı yüklemeler Aşağıdaki tabloda, bu yöntemin döndürebileceğini üç tamsayı değeri gösterilmektedir.  
  
|Döndürülen değer|Koşul|  
|------------------|---------------|  
|Negatif bir tamsayı|İlk dize sıralama düzeninde ikinci dizeden önce gelir.<br /><br /> -veya-<br /><br /> İlk dize `null` .|  
|0|İlk dize ve ikinci dize eşittir.<br /><br /> -veya-<br /><br /> Her iki dize de `null` .|  
|Pozitif bir tamsayı<br /><br /> -veya-<br /><br /> 1|İlk dize sıralama düzeninde ikinci dizeyi izler.<br /><br /> -veya-<br /><br /> İkinci dize `null` .|  
  
> [!IMPORTANT]
> <xref:System.String.Compare%2A?displayProperty=nameWithType>Yöntemi, birincil olarak dizeleri sıralama veya sıralama sırasında kullanılmak üzere tasarlanmıştır. <xref:System.String.Compare%2A?displayProperty=nameWithType>Eşitlik için test etmek için yöntemini kullanmamalısınız (yani, bir dizenin diğerine göre veya ondan daha büyük olup olmadığı konusunda hiçbir şekilde 0 dönüş değerini açıkça araması için). Bunun yerine, iki dizenin eşit olup olmadığını anlamak için yöntemini kullanın <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> .  
  
 Aşağıdaki örnek, <xref:System.String.Compare%2A?displayProperty=nameWithType> iki dizenin göreli değerlerini belirlemede yöntemini kullanır.  
  
 [!code-cpp[Conceptual.String.BasicOps#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#6)]
 [!code-csharp[Conceptual.String.BasicOps#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#6)]
 [!code-vb[Conceptual.String.BasicOps#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#6)]  
  
 Bu örnek `-1` konsola görüntülenir.  
  
 Yukarıdaki örnek, varsayılan olarak kültüre duyarlıdır. Kültüre duyarsız bir dize karşılaştırması gerçekleştirmek için, <xref:System.String.Compare%2A?displayProperty=nameWithType> bir *kültür* parametresi sağlayarak kullanılacak kültürü belirtmenize izin veren yönteminin bir aşırı yüklemesini kullanın. <xref:System.String.Compare%2A?displayProperty=nameWithType>Kültüre duyarsız bir karşılaştırma gerçekleştirmek için yönteminin nasıl kullanılacağını gösteren bir örnek için bkz. [kültüre duyarsız dize karşılaştırmaları gerçekleştirme](../globalization-localization/performing-culture-insensitive-string-comparisons.md).  
  
## <a name="compareordinal"></a>CompareOrdinal  
 <xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType>Yöntemi, yerel kültürü düşünmeksizin iki dize nesnesini karşılaştırır. Bu yöntemin dönüş değerleri, önceki tabloda **Compare** yöntemi tarafından döndürülen değerlerle aynıdır.  
  
> [!IMPORTANT]
> <xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType>Yöntemi, birincil olarak dizeleri sıralama veya sıralama sırasında kullanılmak üzere tasarlanmıştır. <xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType>Eşitlik için test etmek için yöntemini kullanmamalısınız (yani, bir dizenin diğerine göre veya ondan daha büyük olup olmadığı konusunda hiçbir şekilde 0 dönüş değerini açıkça araması için). Bunun yerine, iki dizenin eşit olup olmadığını anlamak için yöntemini kullanın <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> .  
  
 Aşağıdaki örnek, iki dizenin değerlerini karşılaştırmak için **CompareOrdinal** yöntemini kullanır.  
  
 [!code-cpp[Conceptual.String.BasicOps#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#7)]
 [!code-csharp[Conceptual.String.BasicOps#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#7)]
 [!code-vb[Conceptual.String.BasicOps#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#7)]  
  
 Bu örnek `-32` konsola görüntülenir.  
  
## <a name="compareto"></a>CompareTo  
 <xref:System.String.CompareTo%2A?displayProperty=nameWithType>Yöntemi, geçerli dize nesnesinin sarmaladığı dizeyi başka bir dize veya nesne ile karşılaştırır. Bu yöntemin dönüş değerleri, önceki tabloda yöntemi tarafından döndürülen değerlerle aynıdır <xref:System.String.Compare%2A?displayProperty=nameWithType> .  
  
> [!IMPORTANT]
> <xref:System.String.CompareTo%2A?displayProperty=nameWithType>Yöntemi, birincil olarak dizeleri sıralama veya sıralama sırasında kullanılmak üzere tasarlanmıştır. <xref:System.String.CompareTo%2A?displayProperty=nameWithType>Eşitlik için test etmek için yöntemini kullanmamalısınız (yani, bir dizenin diğerine göre veya ondan daha büyük olup olmadığı konusunda hiçbir şekilde 0 dönüş değerini açıkça araması için). Bunun yerine, iki dizenin eşit olup olmadığını anlamak için yöntemini kullanın <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> .  
  
 Aşağıdaki örnek, <xref:System.String.CompareTo%2A?displayProperty=nameWithType> nesnesini nesnesiyle karşılaştırmak için yöntemini kullanır `string1` `string2` .  
  
 [!code-cpp[Conceptual.String.BasicOps#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#8)]
 [!code-csharp[Conceptual.String.BasicOps#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#8)]
 [!code-vb[Conceptual.String.BasicOps#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#8)]  
  
 Bu örnek `-1` konsola görüntülenir.  
  
 Metodun tüm aşırı yüklemeleri <xref:System.String.CompareTo%2A?displayProperty=nameWithType> Varsayılan olarak kültüre duyarlı ve büyük/küçük harfe duyarlı karşılaştırmalar gerçekleştirir. Kültüre duyarsız bir karşılaştırma gerçekleştirmenize olanak tanıyan bu yöntemin hiçbir aşırı yüklemesi sağlanmaz. Kod netliği için, **String.Compare** <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> kültür duyarlı işlemler veya <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> kültüre duyarsız Işlemler için belirtmek yerine String. Compare yöntemini kullanmanızı öneririz. Her iki kültüre duyarlı ve kültüre duyarsız karşılaştırmalar gerçekleştirmek için **String. Compare** metodunu nasıl kullanacağınızı gösteren örnekler için bkz. [kültüre duyarsız dize karşılaştırmaları gerçekleştirme](../globalization-localization/performing-culture-insensitive-string-comparisons.md).  
  
## <a name="equals"></a>Eşittir  
 **String. Equals** yöntemi, iki dizenin aynı olup olmadığını kolayca belirleyebilir. Bu büyük/küçük harfe duyarlı Yöntem, **doğru** veya **yanlış** Boole değeri döndürür. Sonraki örnekte gösterildiği gibi mevcut bir sınıftan kullanılabilir. Aşağıdaki örnek, bir dize nesnesinin "Merhaba Dünya" ifadesini içerip içermediğini anlamak için **Equals** yöntemini kullanır.  
  
 [!code-cpp[Conceptual.String.BasicOps#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#9)]
 [!code-csharp[Conceptual.String.BasicOps#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#9)]
 [!code-vb[Conceptual.String.BasicOps#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#9)]  
  
 Bu örnek `True` konsola görüntülenir.  
  
 Bu yöntem, statik bir yöntem olarak da kullanılabilir. Aşağıdaki örnek, statik bir yöntem kullanarak iki dize nesnesini karşılaştırır.  
  
 [!code-cpp[Conceptual.String.BasicOps#10](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#10)]
 [!code-csharp[Conceptual.String.BasicOps#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#10)]
 [!code-vb[Conceptual.String.BasicOps#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#10)]  
  
 Bu örnek `True` konsola görüntülenir.  
  
## <a name="startswith-and-endswith"></a>StartsWith ve EndsWith  
 String **. StartsWith** metodunu kullanarak, bir dize nesnesinin başka bir dizeyi çevreleyen karakterlerle başlayıp başlamamadığını belirleyebilirsiniz. Bu büyük/küçük harf duyarlı Yöntem, geçerli dize nesnesi geçen dizeyle başlıyorsa **true** , değilse **false** döndürür. Aşağıdaki örnek, bir dize nesnesinin "Hello" ile başlayıp başlamadığını anlamak için bu yöntemi kullanır.  
  
 [!code-cpp[Conceptual.String.BasicOps#11](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#11)]
 [!code-csharp[Conceptual.String.BasicOps#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#11)]
 [!code-vb[Conceptual.String.BasicOps#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#11)]  
  
 Bu örnek `True` konsola görüntülenir.  
  
 **String. EndsWith** yöntemi, geçirilen bir dizeyi geçerli dize nesnesinin sonunda bulunan karakterlerle karşılaştırır. Ayrıca bir Boole değeri döndürür. Aşağıdaki örnek, **EndsWith** metodunu kullanarak bir dizenin sonunu denetler.  
  
 [!code-cpp[Conceptual.String.BasicOps#12](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#12)]
 [!code-csharp[Conceptual.String.BasicOps#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#12)]
 [!code-vb[Conceptual.String.BasicOps#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#12)]  
  
 Bu örnek `False` konsola görüntülenir.  
  
## <a name="indexof-and-lastindexof"></a>IndexOf ve LastIndexOf  
 Bir dize içindeki belirli bir karakterin ilk geçtiği konumu bulmak için **String. IndexOf** yöntemini kullanabilirsiniz. Bu büyük/küçük harf duyarlı Yöntem bir dizenin başından itibaren sayıma başlar ve sıfır tabanlı bir dizin kullanarak geçen karakterin konumunu döndürür. Karakter bulunamazsa – 1 değeri döndürülür.  
  
 Aşağıdaki örnek, bir dizedeki ' ' karakterinin ilk oluşumunu aramak için **IndexOf** metodunu kullanır `l` .  
  
 [!code-cpp[Conceptual.String.BasicOps#13](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#13)]
 [!code-csharp[Conceptual.String.BasicOps#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#13)]
 [!code-vb[Conceptual.String.BasicOps#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#13)]  
  
 Bu örnek `2` konsola görüntülenir.  
  
 String **. LastIndexOf** yöntemi String **. IndexOf** yöntemine benzer, ancak bir dize içindeki belirli bir karakterin son geçtiği konumu döndürür. Büyük/küçük harfe duyarlıdır ve sıfır tabanlı bir dizin kullanır.  
  
 Aşağıdaki örnek, bir dizedeki ' ' karakterinin son oluşumunu aramak için **LastIndexOf** metodunu kullanır `l` .  
  
 [!code-cpp[Conceptual.String.BasicOps#14](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#14)]
 [!code-csharp[Conceptual.String.BasicOps#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#14)]
 [!code-vb[Conceptual.String.BasicOps#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#14)]  
  
 Bu örnek `9` konsola görüntülenir.  
  
 Her iki yöntem de **String. Remove** yöntemiyle birlikte kullanıldığında yararlıdır. Bir karakterin konumunu almak için **IndexOf** veya **LastIndexOf** yöntemlerini kullanabilir ve sonra bu karakterle başlayan bir karakteri ya da kelimeyi kaldırmak için bu konumu **Remove** yöntemine sağlayabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Temel dize Işlemleri](basic-string-operations.md)
- [Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme](../globalization-localization/performing-culture-insensitive-string-operations.md)
- [Sıralama ağırlığı tabloları (Windows üzerinde .NET için)](https://www.microsoft.com/download/details.aspx?id=10921)
- [Varsayılan Unicode harmanlama öğesi tablosu (Linux ve macOS 'ta .NET Core için)](https://www.unicode.org/Public/UCA/latest/allkeys.txt)
