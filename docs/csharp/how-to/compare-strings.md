---
title: Dizeleri karşılaştırma-C# Kılavuzu
description: Kültüre özgü sıralamaya sahip ya da olmadan dize değerlerini karşılaştırmayı ve bu durum olmadan nasıl karşılaştırılacağını ve sıraleyeceğinizi öğrenin
ms.date: 10/03/2018
helpviewer_keywords:
- strings [C#], comparison
- comparing strings [C#]
ms.openlocfilehash: 725441f5399f72b6457af461d51419c35077f4c2
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662920"
---
# <a name="how-to-compare-strings-in-c"></a>C 'de dizeleri karşılaştırma\#

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
- <xref:System.String.op_Equality%2A?displayProperty=nameWithType>ve, <xref:System.String.op_Inequality%2A?displayProperty=nameWithType> diğer bir deyişle, [eşitlik işleçleri `==` ve `!=` ](../language-reference/operators/equality-operators.md#string-equality)sırasıyla

büyük/küçük harfe duyarlı bir sıra karşılaştırması gerçekleştirin ve gerekirse geçerli kültürü kullanın. Aşağıdaki örnek şunu gösterir:

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs" id="Snippet1":::

Varsayılan sıra karşılaştırma, dizeleri karşılaştırırken dile göre kuralları hesaba almaz. <xref:System.Char>İki dizelerdeki her nesnenin ikili değerini karşılaştırır. Sonuç olarak, varsayılan sıra karşılaştırması de büyük/küçük harfe duyarlıdır.

Ve ve işleçleri ile eşitlik testinin <xref:System.String.Equals%2A?displayProperty=nameWithType> `==` `!=` , ve yöntemleri kullanılarak dize karşılaştırmasından farklı olduğunu unutmayın <xref:System.String.CompareTo%2A?displayProperty=nameWithType> <xref:System.String.Compare(System.String,System.String)?displayProperty=nameWithType)> . Eşitlik için testler, büyük/küçük harfe duyarlı bir sıra karşılaştırması gerçekleştirirken, karşılaştırma yöntemleri geçerli kültürü kullanarak büyük/küçük harfe duyarlı, kültüre duyarlı bir karşılaştırma gerçekleştirir. Varsayılan karşılaştırma yöntemleri genellikle farklı karşılaştırma türleri gerçekleştirirken, gerçekleştirilecek karşılaştırma türünü açıkça belirten bir aşırı yükleme çağırarak kodunuzun amacını her zaman açık yapmanızı öneririz.

## <a name="case-insensitive-ordinal-comparisons"></a>Büyük/küçük harfe duyarsız sıralı karşılaştırmalar

<xref:System.String.Equals(System.String,System.StringComparison)?displayProperty=nameWithType>Yöntemi, bir değeri belirtmenizi sağlar <xref:System.StringComparison><xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType>
büyük/küçük harfe duyarsız bir sıra karşılaştırması için. <xref:System.String.Compare(System.String,System.String,System.StringComparison)?displayProperty=nameWithType>Bağımsız değişken için bir değer belirtirseniz, büyük/küçük harfe duyarsız sıralı karşılaştırma gerçekleştiren bir statik yöntem de vardır <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> <xref:System.StringComparison> . Bunlar aşağıdaki kodda gösterilmiştir:

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs" id="Snippet2":::

Büyük/küçük harfe duyarsız bir sıra karşılaştırması gerçekleştirirken, bu yöntemler [sabit kültürün](xref:System.Globalization.CultureInfo.InvariantCulture)büyük/küçük harf kurallarını kullanır.

## <a name="linguistic-comparisons"></a>Dil karşılaştırmaları

Dizeler aynı zamanda geçerli kültür için dil kuralları kullanılarak da sıralanmış olabilir.
Bu bazen "sözcük sıralama düzeni" olarak adlandırılır. Bir dil karşılaştırması gerçekleştirdiğinizde, alfasayısal olmayan bazı Unicode karakterler atanmış özel ağırlıkya sahip olabilir. Örneğin, "-" tirein, "Co-op" ve "Coop" nin yanında sıralama düzeninde görünmesini sağlayacak çok küçük bir ağırlığı olabilir. Ayrıca, bazı Unicode karakterler bir örnek dizisine eşdeğer olabilir <xref:System.Char> . Aşağıdaki örnek, "cadde içinde dans ettikleri" tümceciğini kullanır. Almanya 'da, bir dizede "ss" (U + 0073 U + 0073) ve başka bir dizedeki ' ß ' (U + 00DF). Dilsel (Windows 'da), "ss", hem "en-US" hem de "de" de "de" kültürleri için Alman Esszet: ' ß ' karakterine eşittir.

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs" id="Snippet3":::

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

Bu örnek <xref:System.Globalization.CultureInfo> , en-US ve de serbest kültürleri için nesneleri depolar.
Karşılaştırmalar, <xref:System.Globalization.CultureInfo> kültüre özgü bir karşılaştırma sağlamak için bir nesnesi kullanılarak gerçekleştirilir.

Kullanılan kültür, dil karşılaştırmaları etkiler. Aşağıdaki örnek, "en-US" kültürünü ve "de-DE" kültürünü kullanarak iki Alman cümle karşılaştırmasına ilişkin sonuçları gösterir:

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs" id="Snippet4":::

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

Aşağıdaki örneklerde, geçerli kültüre bağlı bir dil karşılaştırması kullanarak bir dizideki dizelerin nasıl sıralanması ve aranacağı gösterilmektedir. <xref:System.Array>Parametresi alan statik yöntemleri kullanırsınız <xref:System.StringComparer?displayProperty=nameWithType> .

Bu örnek, geçerli kültürü kullanarak bir dize dizisinin nasıl sıralanacağını gösterir:

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs" id="Snippet5":::

Dizi sıralandığında, bir ikili arama kullanarak girdi arayabilirsiniz. Bir ikili arama, koleksiyonun ortasında başlar ve toplamanın hangi yarısını aranan dizeyi içereceği belirlenir. İzleyen her karşılaştırma, koleksiyonun kalan bölümünü yarıya böler.  Dizisi kullanılarak sıralanır <xref:System.StringComparer.CurrentCulture?displayProperty=nameWithType> . Yerel işlev, `ShowWhere` dizenin nerede bulunduğu hakkında bilgi görüntüler. Dize bulunmazsa döndürülen değer, nerede bulunursa nerede olacağını gösterir.

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs" id="Snippet6":::

## <a name="ordinal-sorting-and-searching-in-collections"></a>Koleksiyonlar içinde sıralı sıralama ve arama

Aşağıdaki kod <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> dizeleri depolamak için koleksiyon sınıfını kullanır. Dizeler yöntemi kullanılarak sıralanır <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> . Bu yöntem, iki dizeyi karşılaştıran ve sipariş eden bir temsilciye ihtiyaç duyuyor. <xref:System.String.CompareTo%2A?displayProperty=nameWithType>Yöntemi, bu karşılaştırma işlevini sağlar. Örneği çalıştırın ve siparişi gözlemleyin. Bu sıralama işlemi, sıralı büyük/küçük harfe duyarlı sıralama kullanır. <xref:System.String.Compare%2A?displayProperty=nameWithType>Farklı karşılaştırma kuralları belirtmek için statik yöntemleri kullanırsınız.

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs" id="Snippet7":::

Sıralandığında, dizeler listesi bir ikili arama kullanılarak aranabilir. Aşağıdaki örnek, aynı karşılaştırma işlevi kullanılarak listelenen sıralanmaların nasıl arandığını gösterir. Yerel işlev, `ShowWhere` Aranan metnin nerede olduğunu veya şöyle olacağını gösterir:

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs" id="Snippet8":::

Her zaman sıralama ve arama için aynı karşılaştırma türünü kullandığınızdan emin olun. Sıralama ve arama için farklı karşılaştırma türleri kullanılması beklenmeyen sonuçlar veriyor.

, Ve gibi koleksiyon sınıfları, <xref:System.Collections.Hashtable?displayProperty=nameWithType> <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> <xref:System.StringComparer?displayProperty=nameWithType> öğelerin veya anahtarların türü olduğunda bir parametre alan oluşturucular vardır `string` . Genel olarak, mümkün olan her durumda bu oluşturucuları kullanmanız ve ya da ' i belirtmeniz gerekir <xref:System.StringComparer.Ordinal?displayProperty=nameWithType> <xref:System.StringComparer.OrdinalIgnoreCase?displayProperty=nameWithType> .

## <a name="reference-equality-and-string-interning"></a>Başvuru eşitliği ve dize oluşturma

Örneklerden Hiçbiri kullanılmadı <xref:System.Object.ReferenceEquals%2A> . Bu yöntem, iki dizenin aynı nesne olup olmadığını belirler. Bu, dize karşılaştırmalarında tutarsız sonuçlara yol açabilir. Aşağıdaki örnek, C# ' nin *dize özelliklerini* gösterir. Bir program iki veya daha fazla özdeş dize değişkeni bildiriyorsa, derleyici bunları aynı konumda depolar. <xref:System.Object.ReferenceEquals%2A>Yöntemini çağırarak, iki dizenin bellekteki aynı nesneye gerçekten başvurduğundan emin olabilirsiniz. ' İ <xref:System.String.Copy%2A?displayProperty=nameWithType> kullanmaktan kaçınmak için yöntemini kullanın. Kopya yapıldıktan sonra, aynı değere sahip olsalar bile iki dize farklı depolama konumlarına sahiptir. Bu dizeleri göstermek için aşağıdaki örneği çalıştırın `a` ve `b` aynı depolama *interned* alanını paylaştıkları anlamına gelir. Dizeler `a` ve `c` değildir.

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs" id="Snippet9":::

> [!NOTE]
> Dizelerin eşitliğini test ettiğinizde, gerçekleştirmeyi planladığınız karşılaştırma türünü açıkça belirten yöntemleri kullanmanız gerekir. Kodunuz çok daha sürdürülebilir ve okunabilir. <xref:System.String?displayProperty=nameWithType> <xref:System.Array?displayProperty=nameWithType> Bir numaralandırma parametresi alan ve sınıflarının yöntemlerinin aşırı yüklerini kullanın <xref:System.StringComparison> . Gerçekleştirilecek karşılaştırma türünü belirtirsiniz. `==` `!=` Eşitlik için test ettiğinizde ve operatörlerini kullanmaktan kaçının. <xref:System.String.CompareTo%2A?displayProperty=nameWithType>Örnek yöntemleri her zaman sıralı büyük küçük harfe duyarlı bir karşılaştırma gerçekleştirir. Genellikle dizeleri alfabetik olarak sıralamak için uygundur.

Yöntemini çağırarak bir dizeyi düzenleyebilir veya varolan bir dizeye başvuru alabilirsiniz <xref:System.String.Intern%2A?displayProperty=nameWithType> . Bir dizenin birbirine bağlı olup olmadığını anlamak için <xref:System.String.IsInterned%2A?displayProperty=nameWithType> yöntemini çağırın.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Globalization.CultureInfo?displayProperty=nameWithType>
- <xref:System.StringComparer?displayProperty=nameWithType>
- [Dizeler](../programming-guide/strings/index.md)
- [Dizeleri karşılaştırma](../../standard/base-types/comparing.md)
- [Uygulamaları Genelleştirme ve yerelleştirme](/visualstudio/ide/globalizing-and-localizing-applications)
