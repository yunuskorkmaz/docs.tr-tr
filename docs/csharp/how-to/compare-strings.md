---
title: Dizeleri karşılaştırmak için nasıl - C# Kılavuzu
description: Örnek olarak, kültüre özel sıralamayla veya olmadan dize değerlerini nasıl karşılaştırıp sipariş edebilirsiniz öğrenin
ms.date: 10/03/2018
helpviewer_keywords:
- strings [C#], comparison
- comparing strings [C#]
ms.openlocfilehash: dda3ec8cb6a0131867e6ea3bb0cf7199d86058ff
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73973327"
---
# <a name="how-to-compare-strings-in-c"></a>C'deki dizeleri karşılaştırma\#

İki sorudan birini yanıtlamak için dizeleri karşılaştırın: "Bu iki dize eşit mi?" veya "Bu dizeleri sıralanırken hangi sırada yerleştirilmelidir?"

Bu iki soru dize karşılaştırmalarını etkileyen etkenler tarafından karmaşıkhale getirilir:

- Bir ordinal veya dilsel karşılaştırma seçebilirsiniz.
- Davanın önemli olup olmadığını seçebilirsiniz.
- Kültüre özel karşılaştırmalar seçebilirsiniz.
- Dilsel karşılaştırmalar kültüre ve platforma bağlıdır.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Dizeleri karşılaştırdığınızda, aralarında bir sıra tanımlarsınız. Karşılaştırmalar dizeleri bir dizi sıralamak için kullanılır. Dizi bilinen bir sırada olduğunda, hem yazılım hem de insanlar için arama yapmak daha kolaydır. Diğer karşılaştırmalar dizeleri aynı olup olmadığını kontrol edebilirsiniz. Bu aynılık denetimleri eşitliğe benzer, ancak büyük/küçük harf farklılıkları gibi bazı farklılıklar göz ardı edilebilir.

## <a name="default-ordinal-comparisons"></a>Varsayılan ordinal karşılaştırmalar

Varsayılan olarak, en yaygın işlemler:

- <xref:System.String.CompareTo%2A?displayProperty=nameWithType>
- <xref:System.String.Equals%2A?displayProperty=nameWithType>
- <xref:System.String.op_Equality%2A?displayProperty=nameWithType>ve <xref:System.String.op_Inequality%2A?displayProperty=nameWithType>, yani [eşitlik `==` operatörleri `!=`ve ](../language-reference/operators/equality-operators.md#string-equality), sırasıyla

büyük/küçük harf duyarlı bir madde karşılaştırması yapın ve gerekirse geçerli kültürü kullanın. Aşağıdaki örnek gösteriyor ki:

[!code-csharp-interactive[Comparing strings using an ordinal comparison](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#1)]

Varsayılan ordinal karşılaştırma dizeleri karşılaştırırken dilsel kuralları dikkate almaz. Her <xref:System.Char> nesnenin ikili değerini iki dizede karşılaştırır. Sonuç olarak, varsayılan ordinal karşılaştırma da büyük/küçük harf duyarlıdır.

<xref:System.String.Equals%2A?displayProperty=nameWithType> Eşitlik testi ve `==` ve `!=` işleçleri ile <xref:System.String.CompareTo%2A?displayProperty=nameWithType> ve <xref:System.String.Compare(System.String,System.String)?displayProperty=nameWithType)> işleçleri kullanarak dize karşılaştırma sından farklı olduğunu unutmayın. Eşitlik testleri büyük/küçük harf duyarlı bir ordinal karşılaştırma gerçekleştirirken, karşılaştırma yöntemleri geçerli kültürü kullanarak büyük/küçük harf duyarlı, kültüre duyarlı bir karşılaştırma gerçekleştirir. Varsayılan karşılaştırma yöntemleri genellikle farklı karşılaştırma türleri gerçekleştirdiğinden, gerçekleştirecek karşılaştırma türünü açıkça belirten bir aşırı yükleme çağırarak kodamacınızı her zaman net yapmanızı öneririz.

## <a name="case-insensitive-ordinal-comparisons"></a>Büyük/küçük harf duyarsız ordinal karşılaştırmalar

Yöntem, <xref:System.String.Equals(System.String,System.StringComparison)?displayProperty=nameWithType> bir <xref:System.StringComparison> değer belirtmenizi sağlar<xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType>
büyük/küçük harf duyarsız ordinal karşılaştırma için. Bağımsız değişken için <xref:System.String.Compare(System.String,System.String,System.StringComparison)?displayProperty=nameWithType> <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> bir değer belirtirseniz, büyük/küçük harf duyarsız ordinal karşılaştırma sı gerçekleştiren statik bir yöntem de vardır. <xref:System.StringComparison> Bunlar aşağıdaki kodda gösterilmiştir:

[!code-csharp-interactive[Comparing strings ignoring case](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#2)]

Bir büyük/küçük harf duyarsız ordinal karşılaştırma gerçekleştirirken, bu yöntemler [değişmez kültürün](xref:System.Globalization.CultureInfo.InvariantCulture)kasa kuralları nı kullanır.

## <a name="linguistic-comparisons"></a>Dilsel karşılaştırmalar

Dizeleri de geçerli kültür için dilkuralları kullanılarak sıralanabilir.
Bu bazen "sözcük sıralama sırası" olarak adlandırılır. Dilsel bir karşılaştırma yaptığınızda, bazı alfanümerik Olmayan Unicode karakterleri özel ağırlıklar atanmış olabilir. Örneğin, tire "-" çok küçük bir ağırlık böylece "co-op" ve "kümes" sırayla yan yana görünür atanmış olabilir. Buna ek olarak, bazı Unicode karakterleri bir <xref:System.Char> dizi örnekle eşdeğer olabilir. Aşağıdaki örnekte "Sokakta dans ediyorlar" ifadesi yer almaktadır. Almanca'da "ss" (U+0073 U+0073) bir dizede, "ß" (U+00DF) diğerinde. Dilsel olarak (Windows'da), "ss" Alman Esszet eşittir: "en-US" ve "de-DE" kültürleri hem de 'ß' karakteri.

[!code-csharp-interactive[Comparing strings using linguistic rules](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#3)]

Bu örnek, dilsel karşılaştırmaların işletim sistemine bağımlı doğasını göstermektedir. Etkileşimli pencerenin ana bilgisayarı bir Linux ana bilgisayardır. Dilsel ve ordinal karşılaştırmalar aynı sonuçları üretir. Aynı örneği bir Windows ana bilgisayarda çalıştırdıysanız, aşağıdaki çıktıyı görürsünüz:

```console
<coop> is less than <co-op> using invariant culture
<coop> is greater than <co-op> using ordinal comparison
<coop> is less than <cop> using invariant culture
<coop> is less than <cop> using ordinal comparison
<co-op> is less than <cop> using invariant culture
<co-op> is less than <cop> using ordinal comparison
```

Windows'da, dilbilimsel bir karşılaştırmadan bir ordinal karşılaştırmaya geçiş yaptığınızda "polis", "kümes" ve "co-op" tür sırası değişir. İki Almanca cümle de farklı karşılaştırma türlerini kullanarak farklı karşılaştırın.

## <a name="comparisons-using-specific-cultures"></a>Belirli kültürleri kullanarak karşılaştırmalar

Bu örnek, en-US ve de-DE kültürleri için nesneleri depolar. <xref:System.Globalization.CultureInfo>
Karşılaştırmalar, kültüre <xref:System.Globalization.CultureInfo> özgü bir karşılaştırma sağlamak için bir nesne kullanılarak gerçekleştirilir.

Kullanılan kültür dilsel karşılaştırmaları etkiler. Aşağıdaki örnekte, "en-US" kültürü ve "de-DE" kültürünü kullanarak iki Almanca cümleyi karşılaştırmanın sonuçları gösterilmektedir:

[!code-csharp-interactive[Comparing strings across cultures](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#4)]

Kültüre duyarlı karşılaştırmalar genellikle, kullanıcılar tarafından diğer dizeleri girişi ile kullanıcılar tarafından dizeleri karşılaştırmak ve sıralamak için kullanılır. Bu dizelerin karakterleri ve sıralama kuralları kullanıcının bilgisayarının yerel durumuna bağlı olarak değişebilir. Aynı karakterleri içeren dizeleri bile geçerli iş parçacığının kültürüne bağlı olarak farklı sıralanabilir. Buna ek olarak, bu örnek kodu bir Windows makinesinde yerel olarak deneyin ve aşağıdaki sonuçları olacaktır:

```console
<coop> is less than <co-op> using en-US culture
<coop> is greater than <co-op> using ordinal comparison
<coop> is less than <cop> using en-US culture
<coop> is less than <cop> using ordinal comparison
<co-op> is less than <cop> using en-US culture
<co-op> is less than <cop> using ordinal comparison
```

Dilsel karşılaştırmalar geçerli kültüre bağlıdır ve işletim sistemi bağlıdır. Dize karşılaştırmaları ile çalışırken bunu dikkate almalısınız.

## <a name="linguistic-sorting-and-searching-strings-in-arrays"></a>Dizilerde dilsel sıralama ve arama dizeleri

Aşağıdaki örnekler, geçerli kültüre bağlı bir dilsel karşılaştırma kullanarak bir dizideki dizeleri nasıl sıralayıp arayacağını gösterir. Parametre alan <xref:System.Array> statik yöntemleri kullanırsınız. <xref:System.StringComparer?displayProperty=nameWithType>

Bu örnek, geçerli kültürü kullanarak bir dizi dize sıralamanasıl gösterilmektedir:

[!code-csharp-interactive[Sorting an array of strings](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#5)]

Dizi sıralandıktan sonra, ikili arama kullanarak girişleri arayabilirsiniz. Koleksiyonun hangi yarısının aranan dizeyi içereceğini belirlemek için koleksiyonun ortasında ikili arama başlar. Sonraki her karşılaştırma, koleksiyonun kalan kısmını ikiye böler.  Dizi , <xref:System.StringComparer.CurrentCulture?displayProperty=nameWithType>. Yerel işlev `ShowWhere` dize nerede bulunduğu hakkında bilgi görüntüler. Dize bulunamadıysa, döndürülen değer bulunursa nerede olacağını gösterir.

[!code-csharp-interactive[Searching in a sorted array](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#6)]

## <a name="ordinal-sorting-and-searching-in-collections"></a>Koleksiyonlarda ordinal sıralama ve arama

Aşağıdaki kod dizeleri depolamak için <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> toplama sınıfını kullanır. Dizeleri <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> yöntemi kullanılarak sıralanır. Bu yöntem, iki dizeleri karşılaştıran ve sipariş eden bir temsilci gerekir. Yöntem <xref:System.String.CompareTo%2A?displayProperty=nameWithType> bu karşılaştırma işlevini sağlar. Örneği çalıştırın ve siparişi izleyin. Bu tür işlem, bir ordinal durumda hassas sıralama kullanır. Farklı karşılaştırma kuralları <xref:System.String.Compare%2A?displayProperty=nameWithType> belirtmek için statik yöntemleri kullanırsınız.

[!code-csharp-interactive[Sorting a list of strings](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#7)]

Sıralandıktan sonra, dizeleri listesi ikili arama kullanılarak aranabilir. Aşağıdaki örnek, aynı karşılaştırma işlevini kullanarak sıralanan listelenen arama nasıl gösterir. Yerel işlev, `ShowWhere` aranan metnin nerede veya nerede olacağını gösterir:

[!code-csharp-interactive[csProgGuideStrings#11](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#8)]

Sıralama ve arama için her zaman aynı tür karşılaştırma kullandığınızdan emin olun. Sıralama ve arama için farklı karşılaştırma türlerinin kullanılması beklenmeyen sonuçlar üretir.

<xref:System.Collections.Hashtable?displayProperty=nameWithType>, <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>, gibi toplama <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> sınıfları ve öğelerin veya anahtarların türü olduğunda <xref:System.StringComparer?displayProperty=nameWithType> `string`bir parametre alan oluşturucular var. Genel olarak, mümkün olduğunda bu yapıcıları kullanmalı <xref:System.StringComparer.Ordinal?displayProperty=nameWithType> ve <xref:System.StringComparer.OrdinalIgnoreCase?displayProperty=nameWithType>ya da.

## <a name="reference-equality-and-string-interning"></a>Referans eşitlik ve dize stajı

Örneklerin hiçbiri . <xref:System.Object.ReferenceEquals%2A> Bu yöntem, iki dize aynı nesne olup olmadığını belirler. Bu dize karşılaştırmaları tutarsız sonuçlara yol açabilir. Aşağıdaki örnek, C#'ın *dize staj* özelliğini göstermektedir. Bir program iki veya daha fazla aynı dize değişkenini beyan ettiğinde, derleyici hepsini aynı konumda saklar. <xref:System.Object.ReferenceEquals%2A> Yöntemi çağırarak, iki dize aslında bellekte aynı nesneye bakın görebilirsiniz. Stajı <xref:System.String.Copy%2A?displayProperty=nameWithType> önlemek için yöntemi kullanın. Kopya yapıldıktan sonra, aynı değere sahip olsalar bile iki dize farklı depolama konumlarına sahiptir. Dizeleri `a` ve `b` aynı depolama paylaşmak anlamına *interned* olduğunu göstermek için aşağıdaki örneği çalıştırın. Dizeleri `a` ve `c` değildir.

[!code-csharp-interactive[Demonstrating string interning](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#9)]

> [!NOTE]
> Dizelerin eşitliği için sınama yaptığınızda, ne tür bir karşılaştırma gerçekleştirmek istediğinizi açıkça belirten yöntemleri kullanmanız gerekir. Kodunuz çok daha korunabilir ve okunabilir. Numaralandırma parametresi alan <xref:System.String?displayProperty=nameWithType> <xref:System.Array?displayProperty=nameWithType> <xref:System.StringComparison> ve sınıfların yöntemlerinin aşırı yüklerini kullanın. Hangi karşılaştırma türünü gerçekleştireceklerini belirtirsiniz. Eşitlik için `==` `!=` test ederken ve işleçleri kullanmaktan kaçının. <xref:System.String.CompareTo%2A?displayProperty=nameWithType> Örnek yöntemleri her zaman bir ordinal büyük/küçük harf duyarlı karşılaştırma gerçekleştirir. Bunlar öncelikle alfabetik dizeleri sıralamak için uygundur.

Bir dize stajyer veya <xref:System.String.Intern%2A?displayProperty=nameWithType> yöntemi çağırarak varolan bir interned dize için bir başvuru almak. Bir dize interned olup olmadığını <xref:System.String.IsInterned%2A?displayProperty=nameWithType> belirlemek için yöntemi arayın.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Globalization.CultureInfo?displayProperty=nameWithType>
- <xref:System.StringComparer?displayProperty=nameWithType>
- [Dize](../programming-guide/strings/index.md)
- [Dizeleri Karşılaştırma](../../standard/base-types/comparing.md)
- [Uygulamaları Genelleştirme ve Yerelleştirme](/visualstudio/ide/globalizing-and-localizing-applications)
