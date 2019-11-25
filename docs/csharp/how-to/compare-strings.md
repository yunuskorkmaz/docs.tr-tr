---
title: Dizeleri karşılaştırma- C# kılavuz
description: Kültüre özgü sıralamaya sahip ya da olmadan dize değerlerini karşılaştırmayı ve bu durum olmadan nasıl karşılaştırılacağını ve sıraleyeceğinizi öğrenin
ms.date: 10/03/2018
helpviewer_keywords:
- strings [C#], comparison
- comparing strings [C#]
ms.openlocfilehash: dda3ec8cb6a0131867e6ea3bb0cf7199d86058ff
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73973327"
---
# <a name="how-to-compare-strings-in-c"></a>C\# dizeleri karşılaştırma

Dizeleri iki sorudan birini yanıtlayacak şekilde karşılaştırırsınız: "Bu iki dizeniz eşittir mi?" or "Bu dizeler sıralandığında hangi sırada yerleştirilmesi gerekir?"

Bu iki soru, dize karşılaştırmaları etkileyen faktörlerle karmaşıktır:

- Sıra veya dil karşılaştırması seçebilirsiniz.
- Büyük/küçük harf önemli seçeneğini belirleyebilirsiniz.
- Kültüre özgü karşılaştırmalar seçebilirsiniz.
- Dil karşılaştırmaları kültür ve platforma bağımlıdır.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Dizeleri karşılaştırdığınızda, aralarında bir sıra tanımlarsınız. Karşılaştırmalar, bir dizi dizeyi sıralamak için kullanılır. Sıra, bilinen bir sıra olduğunda, hem yazılım hem de insanların aranması daha kolay olur. Diğer karşılaştırmalar dizelerin aynı olup olmadığını kontrol edebilir. Bu sameness denetimleri eşitlik ile benzerdir, ancak büyük/küçük harf farklılıkları gibi bazı farklılıklar göz ardı edilebilir.

## <a name="default-ordinal-comparisons"></a>Varsayılan sıralı karşılaştırmalar

Varsayılan olarak en yaygın işlemler şunlardır:

- <xref:System.String.CompareTo%2A?displayProperty=nameWithType>
- <xref:System.String.Equals%2A?displayProperty=nameWithType>
- <xref:System.String.op_Equality%2A?displayProperty=nameWithType> ve <xref:System.String.op_Inequality%2A?displayProperty=nameWithType>, diğer bir deyişle, [eşitlik işleçleri sırasıyla `==` ve `!=`](../language-reference/operators/equality-operators.md#string-equality)

büyük/küçük harfe duyarlı bir sıra karşılaştırması gerçekleştirin ve gerekirse geçerli kültürü kullanın. Aşağıdaki örnek şunu gösterir:

[!code-csharp-interactive[Comparing strings using an ordinal comparison](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#1)]

Varsayılan sıra karşılaştırma, dizeleri karşılaştırırken dile göre kuralları hesaba almaz. Her <xref:System.Char> nesnesinin ikili değerini iki dizelerdeki karşılaştırır. Sonuç olarak, varsayılan sıra karşılaştırması de büyük/küçük harfe duyarlıdır.

<xref:System.String.Equals%2A?displayProperty=nameWithType> ve `==` ve `!=` işleçlerini eşitlik testinin <xref:System.String.CompareTo%2A?displayProperty=nameWithType> ve <xref:System.String.Compare(System.String,System.String)?displayProperty=nameWithType)> yöntemleri kullanılarak dize karşılaştırmasından farklı olduğunu unutmayın. Eşitlik için testler, büyük/küçük harfe duyarlı bir sıra karşılaştırması gerçekleştirirken, karşılaştırma yöntemleri geçerli kültürü kullanarak büyük/küçük harfe duyarlı, kültüre duyarlı bir karşılaştırma gerçekleştirir. Varsayılan karşılaştırma yöntemleri genellikle farklı karşılaştırma türleri gerçekleştirirken, gerçekleştirilecek karşılaştırma türünü açıkça belirten bir aşırı yükleme çağırarak kodunuzun amacını her zaman açık yapmanızı öneririz.

## <a name="case-insensitive-ordinal-comparisons"></a>Büyük/küçük harfe duyarsız sıralı karşılaştırmalar

<xref:System.String.Equals(System.String,System.StringComparison)?displayProperty=nameWithType> yöntemi, <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> <xref:System.StringComparison> değerini belirtmenizi sağlar
büyük/küçük harfe duyarsız bir sıra karşılaştırması için. <xref:System.StringComparison> bağımsız değişkeni için bir <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> değeri belirtirseniz, büyük/küçük harfe duyarsız sıralı karşılaştırma gerçekleştiren bir statik <xref:System.String.Compare(System.String,System.String,System.StringComparison)?displayProperty=nameWithType> yöntemi de vardır. Bunlar aşağıdaki kodda gösterilmiştir:

[!code-csharp-interactive[Comparing strings ignoring case](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#2)]

Büyük/küçük harfe duyarsız bir sıra karşılaştırması gerçekleştirirken, bu yöntemler [sabit kültürün](xref:System.Globalization.CultureInfo.InvariantCulture)büyük/küçük harf kurallarını kullanır.

## <a name="linguistic-comparisons"></a>Dil karşılaştırmaları

Dizeler aynı zamanda geçerli kültür için dil kuralları kullanılarak da sıralanmış olabilir.
Bu bazen "sözcük sıralama düzeni" olarak adlandırılır. Bir dil karşılaştırması gerçekleştirdiğinizde, alfasayısal olmayan bazı Unicode karakterler atanmış özel ağırlıkya sahip olabilir. Örneğin, "-" tirein, "Co-op" ve "Coop" nin yanında sıralama düzeninde görünmesini sağlayacak çok küçük bir ağırlığı olabilir. Ayrıca, bazı Unicode karakterler <xref:System.Char> örnek dizisine eşdeğer olabilir. Aşağıdaki örnek, "cadde içinde dans ettikleri" tümceciğini kullanır. Almanya 'da, bir dizede "ss" (U + 0073 U + 0073) ve başka bir dizedeki ' ß ' (U + 00DF). Dilsel (Windows 'da), "ss", hem "en-US" hem de "de" de "de" kültürleri için Alman Esszet: ' ß ' karakterine eşittir.

[!code-csharp-interactive[Comparing strings using linguistic rules](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#3)]

Bu örnek, dil karşılaştırmalarının işletim sistemine bağımlı yapısını gösterir. Etkileşimli pencere için ana bilgisayar bir Linux ana bilgisayarı. Dil ve sıra karşılaştırmaları aynı sonuçları üretir. Aynı örneği bir Windows ana bilgisayarında çalıştırdıysanız, aşağıdaki çıktıyı görürsünüz:

```console
<coop> is less than <co-op> using invariant culture
<coop> is greater than <co-op> using ordinal comparison
<coop> is less than <cop> using invariant culture
<coop> is less than <cop> using ordinal comparison
<co-op> is less than <cop> using invariant culture
<co-op> is less than <cop> using ordinal comparison
```

Windows 'da, bir dil karşılaştırmadan sıralı karşılaştırmaya değiştirdiğinizde "COP", "Coop" ve "Co-op" sıralama düzeni değişir. İki Alman cümle, farklı karşılaştırma türlerini kullanarak farklı şekilde de karşılaştırılır.

## <a name="comparisons-using-specific-cultures"></a>Belirli kültürleri kullanan karşılaştırmalar

Bu örnek, en-US ve de serbest kültür için <xref:System.Globalization.CultureInfo> nesnelerini depolar.
Karşılaştırmalar, kültüre özgü bir karşılaştırma sağlamak için <xref:System.Globalization.CultureInfo> nesnesi kullanılarak gerçekleştirilir.

Kullanılan kültür, dil karşılaştırmaları etkiler. Aşağıdaki örnek, "en-US" kültürünü ve "de-DE" kültürünü kullanarak iki Alman cümle karşılaştırmasına ilişkin sonuçları gösterir:

[!code-csharp-interactive[Comparing strings across cultures](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#4)]

Kültüre duyarlı karşılaştırmalar genellikle kullanıcılara göre diğer dizeler ile kullanıcılara göre dize girişlerini karşılaştırmak ve sıralamak için kullanılır. Bu dizelerin karakter ve sıralama kuralları, kullanıcının bilgisayarının yerel ayarına bağlı olarak değişebilir. Aynı karakterleri içeren dizeler bile geçerli iş parçacığının kültürüne bağlı olarak farklı şekilde sıralama gösterebilir. Ayrıca, bu örnek kodu bir Windows makinesinde yerel olarak deneyin ve aşağıdaki sonuçları elde edersiniz:

```console
<coop> is less than <co-op> using en-US culture
<coop> is greater than <co-op> using ordinal comparison
<coop> is less than <cop> using en-US culture
<coop> is less than <cop> using ordinal comparison
<co-op> is less than <cop> using en-US culture
<co-op> is less than <cop> using ordinal comparison
```

Dil karşılaştırmaları geçerli kültüre bağımlıdır ve işletim sistemine bağımlıdır. Dize karşılaştırmaları ile çalışırken bunu dikkate almanız gerekir.

## <a name="linguistic-sorting-and-searching-strings-in-arrays"></a>Dizelerdeki dil sıralaması ve arama dizeleri

Aşağıdaki örneklerde, geçerli kültüre bağlı bir dil karşılaştırması kullanarak bir dizideki dizelerin nasıl sıralanması ve aranacağı gösterilmektedir. Bir <xref:System.StringComparer?displayProperty=nameWithType> parametresi alan statik <xref:System.Array> yöntemlerini kullanırsınız.

Bu örnek, geçerli kültürü kullanarak bir dize dizisinin nasıl sıralanacağını gösterir:

[!code-csharp-interactive[Sorting an array of strings](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#5)]

Dizi sıralandığında, bir ikili arama kullanarak girdi arayabilirsiniz. Bir ikili arama, koleksiyonun ortasında başlar ve toplamanın hangi yarısını aranan dizeyi içereceği belirlenir. İzleyen her karşılaştırma, koleksiyonun kalan bölümünü yarıya böler.  Dizi <xref:System.StringComparer.CurrentCulture?displayProperty=nameWithType> kullanılarak sıralanır. Yerel işlev `ShowWhere` dizenin nerede bulunduğu hakkında bilgi gösterir. Dize bulunmazsa döndürülen değer, nerede bulunursa nerede olacağını gösterir.

[!code-csharp-interactive[Searching in a sorted array](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#6)]

## <a name="ordinal-sorting-and-searching-in-collections"></a>Koleksiyonlar içinde sıralı sıralama ve arama

Aşağıdaki kod dizeleri depolamak için <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> Collection sınıfını kullanır. Dizeler <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> yöntemi kullanılarak sıralanır. Bu yöntem, iki dizeyi karşılaştıran ve sipariş eden bir temsilciye ihtiyaç duyuyor. <xref:System.String.CompareTo%2A?displayProperty=nameWithType> yöntemi, bu karşılaştırma işlevini sağlar. Örneği çalıştırın ve siparişi gözlemleyin. Bu sıralama işlemi, sıralı büyük/küçük harfe duyarlı sıralama kullanır. Statik <xref:System.String.Compare%2A?displayProperty=nameWithType> yöntemlerini farklı karşılaştırma kuralları belirtmek için kullanacaksınız.

[!code-csharp-interactive[Sorting a list of strings](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#7)]

Sıralandığında, dizeler listesi bir ikili arama kullanılarak aranabilir. Aşağıdaki örnek, aynı karşılaştırma işlevi kullanılarak listelenen sıralanmaların nasıl arandığını gösterir. Yerel işlev `ShowWhere` aranan metnin nerede olduğunu gösterir veya şöyle olacaktır:

[!code-csharp-interactive[csProgGuideStrings#11](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#8)]

Her zaman sıralama ve arama için aynı karşılaştırma türünü kullandığınızdan emin olun. Sıralama ve arama için farklı karşılaştırma türleri kullanılması beklenmeyen sonuçlar veriyor.

<xref:System.Collections.Hashtable?displayProperty=nameWithType>, <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>ve <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> gibi koleksiyon sınıfları, öğelerin veya anahtarların türü `string`olduğunda bir <xref:System.StringComparer?displayProperty=nameWithType> parametresi alan oluşturuculara sahiptir. Genel olarak, mümkün olan her durumda bu oluşturucuları kullanmanız ve <xref:System.StringComparer.Ordinal?displayProperty=nameWithType> ya da <xref:System.StringComparer.OrdinalIgnoreCase?displayProperty=nameWithType> ' i belirtmeniz gerekir.

## <a name="reference-equality-and-string-interning"></a>Başvuru eşitliği ve dize oluşturma

Örneklerden hiçbiri <xref:System.Object.ReferenceEquals%2A>kullanılmadı. Bu yöntem, iki dizenin aynı nesne olup olmadığını belirler. Bu, dize karşılaştırmalarında tutarsız sonuçlara yol açabilir. Aşağıdaki örnek, öğesinin *dize* özelliği olan C#özelliğini gösterir. Bir program iki veya daha fazla özdeş dize değişkeni bildiriyorsa, derleyici bunları aynı konumda depolar. <xref:System.Object.ReferenceEquals%2A> yöntemini çağırarak, iki dizenin bellekteki aynı nesneye gerçekten başvurduğundan emin olabilirsiniz. <xref:System.String.Copy%2A?displayProperty=nameWithType> yöntemini kullanarak, kullanmaktan kaçının. Kopya yapıldıktan sonra, aynı değere sahip olsalar bile iki dize farklı depolama konumlarına sahiptir. `a` dizeleri göstermek için aşağıdaki örneği çalıştırın ve `b` aynı depolama alanını *paylaştıkları anlamına gelir* . `a` ve `c` dizeleri değildir.

[!code-csharp-interactive[Demonstrating string interning](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#9)]

> [!NOTE]
> Dizelerin eşitliğini test ettiğinizde, gerçekleştirmeyi planladığınız karşılaştırma türünü açıkça belirten yöntemleri kullanmanız gerekir. Kodunuz çok daha sürdürülebilir ve okunabilir. <xref:System.String?displayProperty=nameWithType> yöntemlerinin ve <xref:System.StringComparison> bir numaralandırma parametresi alan sınıfların <xref:System.Array?displayProperty=nameWithType> aşırı yüklerini kullanın. Gerçekleştirilecek karşılaştırma türünü belirtirsiniz. Eşitlik için test ettiğinizde `==` ve `!=` işleçlerini kullanmaktan kaçının. <xref:System.String.CompareTo%2A?displayProperty=nameWithType> örnek yöntemleri her zaman sıralı büyük küçük harfe duyarlı karşılaştırma gerçekleştirir. Genellikle dizeleri alfabetik olarak sıralamak için uygundur.

<xref:System.String.Intern%2A?displayProperty=nameWithType> yöntemini çağırarak bir dizeyi düzenleyebilir veya varolan bir dizeye başvuru alabilirsiniz. Bir dizenin birbirine bağlı olup olmadığını anlamak için <xref:System.String.IsInterned%2A?displayProperty=nameWithType> yöntemini çağırın.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Globalization.CultureInfo?displayProperty=nameWithType>
- <xref:System.StringComparer?displayProperty=nameWithType>
- [Dizeler](../programming-guide/strings/index.md)
- [Dizeleri Karşılaştırma](../../standard/base-types/comparing.md)
- [Uygulamaları Genelleştirme ve Yerelleştirme](/visualstudio/ide/globalizing-and-localizing-applications)
