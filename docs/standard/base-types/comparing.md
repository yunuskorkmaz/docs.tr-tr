---
title: .NET 'teki dizeleri karşılaştırma
description: .NET 'teki dizeleri karşılaştırmak için yöntemler hakkında bilgi edinin. Compare, CompareOrdinal, CompareTo, StartsWith, EndsWith, eşittir, IndexOf, & LastIndexOf yöntemleri hakkında bilgi edinin.
ms.date: 03/30/2017
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
- strings [.NET], comparing
- CompareOrdinal method
- EndsWith method
- Equals method
- StartsWith method
ms.assetid: 977dc094-fe19-4955-98ec-d2294d04a4ba
ms.openlocfilehash: 08a92e314ad0900679d46cc759c80db89b43f0f0
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94823153"
---
# <a name="compare-strings-in-net"></a>.NET 'teki dizeleri karşılaştırın

.NET, dizelerin değerlerini karşılaştırmak için çeşitli yöntemler sağlar. Aşağıdaki tabloda değer karşılaştırma yöntemleri listelenmekte ve açıklanmaktadır.

|Yöntem adı|Kullanın|
|-----------------|---------|
|<xref:System.String.Compare%2A?displayProperty=nameWithType>|İki dizenin değerlerini karşılaştırır. Bir tamsayı değeri döndürür.|
|<xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType>|Yerel kültürle ilgili olmadan iki dizeyi karşılaştırır. Bir tamsayı değeri döndürür.|
|<xref:System.String.CompareTo%2A?displayProperty=nameWithType>|Geçerli dize nesnesini başka bir dizeyle karşılaştırır. Bir tamsayı değeri döndürür.|
|<xref:System.String.StartsWith%2A?displayProperty=nameWithType>|Bir dizenin geçilen dizeyle başlayıp başlamadığını belirler. Boole değeri döndürür.|
|<xref:System.String.EndsWith%2A?displayProperty=nameWithType>|Bir dizenin geçtiğini dize ile bitip bitmeyeceğini belirler. Boole değeri döndürür.|
|<xref:System.String.Contains%2A?displayProperty=nameWithType>|Bir karakter veya dizenin başka bir dize içinde oluşup oluşmadığını belirler. Boole değeri döndürür.|
|<xref:System.String.Equals%2A?displayProperty=nameWithType>|İki dizenin aynı olup olmadığını belirler. Boole değeri döndürür.|
|<xref:System.String.IndexOf%2A?displayProperty=nameWithType>|İncelediğiniz dizenin başından başlayarak bir karakterin veya dizenin dizin konumunu döndürür. Bir tamsayı değeri döndürür.|
|<xref:System.String.LastIndexOf%2A?displayProperty=nameWithType>|İncelediğiniz dizenin sonundan başlayarak bir karakterin veya dizenin dizin konumunu döndürür. Bir tamsayı değeri döndürür.|

## <a name="compare-method"></a>Compare yöntemi

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

 Yukarıdaki örnek, varsayılan olarak kültüre duyarlıdır. Kültüre duyarsız bir dize karşılaştırması gerçekleştirmek için, <xref:System.String.Compare%2A?displayProperty=nameWithType> bir *kültür* parametresi sağlayarak kullanılacak kültürü belirtmenize izin veren yönteminin bir aşırı yüklemesini kullanın. <xref:System.String.Compare%2A?displayProperty=nameWithType>Kültüre duyarsız bir karşılaştırma gerçekleştirmek için yönteminin nasıl kullanılacağını gösteren bir örnek için bkz. [kültüre duyarsız dize karşılaştırmaları](../globalization-localization/performing-culture-insensitive-string-comparisons.md).

## <a name="compareordinal-method"></a>CompareOrdinal yöntemi

<xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType>Yöntemi, yerel kültürü düşünmeksizin iki dize nesnesini karşılaştırır. Bu yöntemin dönüş değerleri, önceki tabloda yöntemi tarafından döndürülen değerlerle aynıdır `Compare` .

> [!IMPORTANT]
> <xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType>Yöntemi, birincil olarak dizeleri sıralama veya sıralama sırasında kullanılmak üzere tasarlanmıştır. <xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType>Eşitlik için test etmek için yöntemini kullanmamalısınız (yani, bir dizenin diğerine göre veya ondan daha büyük olup olmadığı konusunda hiçbir şekilde 0 dönüş değerini açıkça araması için). Bunun yerine, iki dizenin eşit olup olmadığını anlamak için yöntemini kullanın <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> .

 Aşağıdaki örnek, `CompareOrdinal` iki dizenin değerlerini karşılaştırmak için yöntemini kullanır.

 [!code-cpp[Conceptual.String.BasicOps#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#7)]
 [!code-csharp[Conceptual.String.BasicOps#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#7)]
 [!code-vb[Conceptual.String.BasicOps#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#7)]

 Bu örnek `-32` konsola görüntülenir.

## <a name="compareto-method"></a>CompareTo yöntemi

<xref:System.String.CompareTo%2A?displayProperty=nameWithType>Yöntemi, geçerli dize nesnesinin sarmaladığı dizeyi başka bir dize veya nesne ile karşılaştırır. Bu yöntemin dönüş değerleri, önceki tabloda yöntemi tarafından döndürülen değerlerle aynıdır <xref:System.String.Compare%2A?displayProperty=nameWithType> .

> [!IMPORTANT]
> <xref:System.String.CompareTo%2A?displayProperty=nameWithType>Yöntemi, birincil olarak dizeleri sıralama veya sıralama sırasında kullanılmak üzere tasarlanmıştır. <xref:System.String.CompareTo%2A?displayProperty=nameWithType>Eşitlik için test etmek için yöntemini kullanmamalısınız (yani, bir dizenin diğerine göre veya ondan daha büyük olup olmadığı konusunda hiçbir şekilde 0 dönüş değerini açıkça araması için). Bunun yerine, iki dizenin eşit olup olmadığını anlamak için yöntemini kullanın <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> .

 Aşağıdaki örnek, <xref:System.String.CompareTo%2A?displayProperty=nameWithType> nesnesini nesnesiyle karşılaştırmak için yöntemini kullanır `string1` `string2` .

 [!code-cpp[Conceptual.String.BasicOps#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#8)]
 [!code-csharp[Conceptual.String.BasicOps#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#8)]
 [!code-vb[Conceptual.String.BasicOps#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#8)]

 Bu örnek `-1` konsola görüntülenir.

 Metodun tüm aşırı yüklemeleri <xref:System.String.CompareTo%2A?displayProperty=nameWithType> Varsayılan olarak kültüre duyarlı ve büyük/küçük harfe duyarlı karşılaştırmalar gerçekleştirir. Kültüre duyarsız bir karşılaştırma gerçekleştirmenize olanak tanıyan bu yöntemin hiçbir aşırı yüklemesi sağlanmaz. Kod netliği için, `String.Compare` <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> kültüre duyarlı işlemler veya kültüre duyarsız işlemler için belirterek metodunu kullanmanızı öneririz <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> . `String.Compare`Kültüre duyarlı ve kültüre duyarsız karşılaştırmalar yapmak için yönteminin nasıl kullanılacağını gösteren örnekler için bkz. [Culture-Insensitive dize karşılaştırmaları gerçekleştirme](../globalization-localization/performing-culture-insensitive-string-comparisons.md).

## <a name="equals-method"></a>Equals yöntemi

<xref:System.String.Equals%2A?displayProperty=nameWithType>Yöntemi, iki dizenin aynı olup olmadığını kolayca belirleyebilir. Bu büyük/küçük harfe duyarlı Yöntem bir `true` veya `false` Boole değeri döndürür. Sonraki örnekte gösterildiği gibi mevcut bir sınıftan kullanılabilir. Aşağıdaki örnek, `Equals` bir dize nesnesinin "Merhaba Dünya" ifadesini içerip içermediğini anlamak için yöntemini kullanır.

 [!code-cpp[Conceptual.String.BasicOps#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#9)]
 [!code-csharp[Conceptual.String.BasicOps#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#9)]
 [!code-vb[Conceptual.String.BasicOps#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#9)]

 Bu örnek `True` konsola görüntülenir.

 Bu yöntem, statik bir yöntem olarak da kullanılabilir. Aşağıdaki örnek, statik bir yöntem kullanarak iki dize nesnesini karşılaştırır.

 [!code-cpp[Conceptual.String.BasicOps#10](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#10)]
 [!code-csharp[Conceptual.String.BasicOps#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#10)]
 [!code-vb[Conceptual.String.BasicOps#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#10)]

 Bu örnek `True` konsola görüntülenir.

## <a name="startswith-and-endswith-methods"></a>StartsWith ve EndsWith yöntemleri

Bir <xref:System.String.StartsWith%2A?displayProperty=nameWithType> dize nesnesinin, başka bir dizeyi çevreleyen karakterlerle başlayıp başlamamadığını anlamak için yöntemini kullanabilirsiniz. Bu büyük/küçük harfe duyarlı Yöntem `true` , geçerli dize nesnesi geçen dize ile başlıyorsa ve yoksa ' i döndürür `false` . Aşağıdaki örnek, bir dize nesnesinin "Hello" ile başlayıp başlamadığını anlamak için bu yöntemi kullanır.

 [!code-cpp[Conceptual.String.BasicOps#11](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#11)]
 [!code-csharp[Conceptual.String.BasicOps#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#11)]
 [!code-vb[Conceptual.String.BasicOps#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#11)]

 Bu örnek `True` konsola görüntülenir.

 <xref:System.String.EndsWith%2A?displayProperty=nameWithType>Yöntemi, geçirilen bir dizeyi geçerli dize nesnesinin sonunda bulunan karakterlerle karşılaştırır. Ayrıca bir Boole değeri döndürür. Aşağıdaki örnek, yöntemini kullanarak bir dizenin sonunu denetler `EndsWith` .

 [!code-cpp[Conceptual.String.BasicOps#12](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#12)]
 [!code-csharp[Conceptual.String.BasicOps#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#12)]
 [!code-vb[Conceptual.String.BasicOps#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#12)]

 Bu örnek `False` konsola görüntülenir.

## <a name="indexof-and-lastindexof-methods"></a>IndexOf ve LastIndexOf yöntemleri

<xref:System.String.IndexOf%2A?displayProperty=nameWithType>Bir dize içindeki belirli bir karakterin ilk geçtiği konumu bulmak için yöntemini kullanabilirsiniz. Bu büyük/küçük harf duyarlı Yöntem bir dizenin başından itibaren sayıma başlar ve sıfır tabanlı bir dizin kullanarak geçen karakterin konumunu döndürür. Karakter bulunamazsa – 1 değeri döndürülür.

Aşağıdaki örnek, `IndexOf` bir dizedeki ' ' karakterinin ilk oluşumunu aramak için yöntemini kullanır `l` .

 [!code-cpp[Conceptual.String.BasicOps#13](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#13)]
 [!code-csharp[Conceptual.String.BasicOps#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#13)]
 [!code-vb[Conceptual.String.BasicOps#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#13)]

 Bu örnek `2` konsola görüntülenir.

 <xref:System.String.LastIndexOf%2A?displayProperty=nameWithType>Yöntemi, `String.IndexOf` bir dize içinde belirli bir karakterin son oluşum konumunu döndürdüğünden yöntemi ile benzerdir. Büyük/küçük harfe duyarlıdır ve sıfır tabanlı bir dizin kullanır.

 Aşağıdaki örnek, `LastIndexOf` bir dizedeki ' ' karakterinin son oluşumunu aramak için yöntemini kullanır `l` .

 [!code-cpp[Conceptual.String.BasicOps#14](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#14)]
 [!code-csharp[Conceptual.String.BasicOps#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#14)]
 [!code-vb[Conceptual.String.BasicOps#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#14)]

 Bu örnek `9` konsola görüntülenir.

 Her iki yöntem de yöntemiyle birlikte kullanıldığında yararlıdır <xref:System.String.Remove%2A?displayProperty=nameWithType> . `IndexOf` `LastIndexOf` Bir karakterin konumunu almak için ya da yöntemlerini kullanabilir ve sonra bu `Remove` karakterle başlayan bir karakteri veya kelimeyi kaldırmak için bu konumu yöntemine sağlayabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET 'teki dizeleri kullanmak için en iyi uygulamalar](best-practices-strings.md)
- [Temel dize Işlemleri](basic-string-operations.md)
- [Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme](../globalization-localization/performing-culture-insensitive-string-operations.md)
- [Sıralama ağırlığı tabloları](https://www.microsoft.com/download/details.aspx?id=10921) -Windows üzerinde .NET Framework ve .NET Core 1.0-3.1 tarafından kullanılır
- [Varsayılan Unicode harmanlama öğesi tablosu](https://www.unicode.org/Public/UCA/latest/allkeys.txt) -.NET 5 tarafından tüm platformlarda ve Linux ve MacOS 'Ta .NET Core tarafından kullanılır
