---
title: 'Nasıl yapılır: dizeleri - C# Kılavuzu karşılaştırmak'
description: Karşılaştırma ve dize değerlerini, ile veya durumda, ile veya kültüre özgü sıralama olmadan olmadan sipariş hakkında bilgi edinin
ms.date: 03/20/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- strings [C#], comparison
- comparing strings [C#]
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3edc1ffdcb4d084f8f76ff27144402fbf98fcbdb
ms.sourcegitcommit: 935d5267c44f9bce801468ef95f44572f1417e8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/28/2018
---
# <a name="how-to-compare-strings-in-c"></a>C# dizeleri karşılaştırma #

Yanıta iki sorulardan biri dizeleri karşılaştırmak: "Bu iki dizeyi eşitse?" veya "hangi sırada bu dizeler bunları sıralarken yerleştirilmelidir?"

Bu iki soru dize karşılaştırmaları etkileyen faktörler tarafından karmaşık: 
- Bir sıra veya dil karşılaştırma seçebilirsiniz.
- Servis talebi önemlidir, seçebilirsiniz.
- Kültüre özgü karşılaştırmaları seçebilirsiniz.
- Dil comparisions kültür ve platform bağımlı ' dir.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Dizeleri karşılaştırmak için siparişe aralarında tanımlayın. Karşılaştırmaları bir dizi dize sıralamak için kullanılır. Bilinen bir sırada dizisi başladıktan sonra aramak hem yazılım hem insanlar için daha kolaydır. Diğer karşılaştırmaları dizeleri aynı olup olmadığını kontrol edebilirsiniz. Bu benzerlik denetimleri eşitlik için benzerdir, ancak büyük farklar gibi bazı farklar yoksayılabilir.

## <a name="default-ordinal-comparisons"></a>Varsayılan sıra karşılaştırmaları

En yaygın işlemleri <xref:System.String.CompareTo%2A?displayProperty=nameWithType> ve <xref:System.String.Equals%2A?displayProperty=nameWithType> veya <xref:System.String.op_Equality%2A?displayProperty=nameWithType> bir sıralı karşılaştırma büyük küçük harfe duyarlı karşılaştırma ve geçerli kültürü kullanın. Aşağıdaki örnekte sonuçları gösterilmektedir.

[!code-csharp-interactive[Comparing strings using an ordinal comparison](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#1)]

Sıralı karşılaştırmaları dil kuralları dizeleri karşılaştırma zaman dikkate değil. Bunlar karakter dizeleri karşılaştırır. Büyük küçük harfe duyarlı karşılaştırmalar kendi karşılaştırmalarında büyük/küçük harf kullanın. En önemli bu varsayılan karşılaştırma yöntemleri hakkında geçerli kültürü kullandıkları için sonuçları makine yerel ve dil ayarlarını üzerinde bağımlı oldukları çalıştırdığı noktasıdır. Bu karşılaştırmalar sipariş makineler veya konumları arasında tutarlı olması gereken yerde karşılaştırmaları için uygun değil.

## <a name="case-insensitive-ordinal-comparisons"></a>Büyük küçük harf duyarsız sıralı karşılaştırmaları

<xref:System.String.Equals%2A?displayProperty=nameWithType> Yöntemi belirtmenize olanak sağlayan bir <xref:System.StringComparison> değerini <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> büyük küçük harf duyarsız bir karşılaştırma belirtmek için. Ayrıca bir statik olduğundan <xref:System.String.Compare%2A> duyarlı karşılaştırmalar belirtmek için bir Boole bağımsız değişkeni içerir yöntemi. Bunlar aşağıdaki kodda gösterilir:

[!code-csharp-interactive[Comparing strings ignoring case](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#2)]

## <a name="linguistic-comparisons"></a>Dil karşılaştırmaları

Dizeleri geçerli kültür için dil kurallarını kullanarak da sıralanabilir.
Bu bazen "word sıralama düzeni." adlandırılır Dil karşılaştırması gerçekleştirdiğinizde, alfasayısal olmayan bazı Unicode karakterler atanan özel ağırlıklara sahip olabilir. Örneğin, kısa çizgi "-" "co-op" ve "coop" birbirinin yanına sıralama düzenini görünmesini sağlayacak şekilde atanmış çok küçük bir ağırlık olabilir. Ayrıca, bazı Unicode karakterler, alfasayısal characterss bir dizi için eşdeğer olabilir. Aşağıdaki örnek, "Bunlar Sokak dans." tümceciği kullanır Almanca 'ß' ve "ss". İncelemeye (Windows), "ss" Almanca Essetz eşittir: "en-US" ve "de-DE" kültür 'ß' karakter. 

[!code-csharp-interactive[Comparing strings using linguistic rules](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#3)]

Bu örnek dil karşılaştırmaları işletim sistemi bağımlı yapısını gösterir. Ana bilgisayar etkileşimli penceresi için bir Linux ana bilgisayardır. Dil ve sıralı karşılaştırmaları aynı sonucu verir. Bu aynı örnek bir Windows konakta, aşağıdaki çıkış görür:

```console
<coop> is less than <co-op> using invariant culture
<coop> is greater than <co-op> using ordinal comparison
<coop> is less than <cop> using invariant culture
<coop> is less than <cop> using ordinal comparison
<co-op> is less than <cop> using invariant culture
<co-op> is less than <cop> using ordinal comparison
```

Sıralı bir karşılaştırma için bir dil karşılaştırmadan değiştirdiğinizde "coop" ve "co-op" Windows, "Kopyala" sıralama düzenini değiştirin. İki Almanca cümleleri farklı farklı karşılaştırma türlerini kullanarak da karşılaştırın.

## <a name="comparisons-using-specific-cultures"></a>Belirli kültürü kullanarak karşılaştırmaları

Bu örnek depolar <xref:System.Globalization.CultureInfo> geçerli kültür için.
Özgün kültürü ayarlama ve geçerli iş parçacığı nesnesinde alınır. Karşılaştırmaları kullanılarak gerçekleştirilen <xref:System.StringComparison.CurrentCulture> kültüre özgü karşılaştırma emin olmak için değeri.

Kullanılan kültür dil karşılaştırmaları etkiler. Aşağıdaki örnekte, "en-US" kültür ve "de-DE" kültürü kullanarak iki Almanca cümle karşılaştırma sonuçlarını gösterir:

[!code-csharp-interactive[Comparing strings across cultures](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#4)]

Kültüre duyarlı karşılaştırmaları genellikle karşılaştırın ve dizeleri giriş sıralamak için kullanıcılar tarafından kullanıcılar tarafından giriş diğer dizeleri ile kullanılır. Karakterler ve sıralama kuralları bu dizeler, kullanıcının bilgisayarındaki yerel ayara bağlı olarak değişebilir. Aynı karakterler içeren bile dizeleri geçerli iş parçacığı kültürünü bağlı olarak farklı sıralama. Ayrıca, bu örnek kod bir Windows makinesinde yerel olarak deneyin ve aşağıdaki sonuçları olur:

```console
<coop> is less than <co-op> using en-US culture
<coop> is greater than <co-op> using ordinal comparison
<coop> is less than <cop> using en-US culture
<coop> is less than <cop> using ordinal comparison
<co-op> is less than <cop> using en-US culture
<co-op> is less than <cop> using ordinal comparison
```

Dil comparisions geçerli kültür üzerinde bağımlı olduğunda ve işletim sistemi bağımlı. Dize karşılaştırmaları ile çalışırken, dikkate almanız gerekir.

## <a name="linguistic-sorting-and-searching-strings-in-arrays"></a>Dil sıralama ve dizilerde dizeleri arama

Aşağıdaki örnekler nasıl sıralanacağını ve geçerli kültür üzerinde bağımlı bir dil karşılaştırma kullanarak bir dizi dizelerini arayın. Statik kullandığınız <xref:System.Array> ele yöntemleri bir <xref:System.StringComparer?displayProperty=nameWithType> parametresi.

Bu örnek, bir dizi geçerli kültürü kullanarak dizeleri sıralama gösterilmektedir: 

[!code-csharp-interactive[Sorting an array of strings](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#5)]

Dizi sıralanmış sonra ikili arama özelliğini kullanarak girişleri için arama yapabilirsiniz. İkili arama koleksiyonun hangi yarı Aranan dize içerecektir belirlemek için koleksiyon ortasında başlar. Sonraki her karşılaştırma yarısı koleksiyonda kalan kısmını subdivides.  Dizi kullanılarak sıralanmış <xref:System.StringComparer.CurrentCulture?displayProperty=nameWithType>. Yerel işlevi `ShowWhere` dize bulunduğu hakkında bilgileri görüntüler. Burada olacaktır döndürülen değer dizesi bulunamadı, gösterir, bulunmuşsa.

[!code-csharp-interactive[Searching in a sorted array](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#6)]

## <a name="ordinal-sorting-and-searching-in-collections"></a>Sıralı sıralama ve koleksiyonlarda arama

Aşağıdaki kod <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> dize depolamak için koleksiyon sınıfı. Dizeleri kullanarak sıralanır <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> yöntemi. Bu yöntemin karşılaştırır ve iki dizeyi siparişler bir temsilci gerekir. <xref:System.String.CompareTo%2A?displayProperty=nameWithType> Yöntemi bu karşılaştırma işlevi sağlar. Örneği çalıştırmak ve sırasını gözlemleyin. Bu sıralama işlemi sıralı büyük küçük harfe duyarlı sıralama kullanır. Statik kullanırsınız <xref:System.String.Compare%2A?displayProperty=nameWithType> farklı karşılaştırma kurallarını belirtmek için yöntemleri.

[!code-csharp-interactive[Sorting a list of strings](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#7)]

Sıralanmış sonra dizelerin listesi ikili arama özelliğini kullanarak aranabilir. Aşağıdaki örnek, aynı karşılaştırma işlevini kullanarak listelenen sıralanmış arama yapma gösterir. Yerel işlevi `ShowWhere` burada Aranan metni veya olacaktır gösterir:

[!code-csharp-interactive[csProgGuideStrings#11](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#8)]

Her zaman aynı karşılaştırma türünü sıralama ve arama için kullandığınızdan emin olun. Farklı karşılaştırma türlerini sıralama ve arama üretir beklenmeyen sonuçlar için kullanma. 

Koleksiyon sınıfları gibi <xref:System.Collections.Hashtable?displayProperty=nameWithType>, <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>, ve <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> ele oluşturucular sahip bir <xref:System.StringComparer?displayProperty=nameWithType> öğeleri veya anahtarları türünü olduğunda parametre `string`. Genel olarak, mümkün olduğunda bu oluşturucular kullanın ve gerekir ya da belirtin <xref:System.StringComparer.Ordinal?displayProperty=nameWithType> veya <xref:System.StringComparer.OrdinalIgnoreCase?displayProperty=nameWithType>.

## <a name="reference-equality-and-string-interning"></a>Referans eşitlik ve dize interning

Örneklerin hiçbiri kullanmış <xref:System.Object.ReferenceEquals%2A>. Bu yöntem, iki dizeyi aynı nesne olup olmadığını belirler. Bu dize karşılaştırmaları içinde tutarsız sonuçlara neden olabilir. Aşağıdaki örnekte gösterilmiştir *dize interning* C# özelliğidir. İki veya daha çok özdeş dizesi değişkenlerinin bir program bildirir, derleyici bunların tümü aynı konumda depolar. Çağırarak <xref:System.Object.ReferenceEquals%2A> yöntemi, iki dizeyi aslında aynı nesneye bellekte başvurmadığından görebilirsiniz. Kullanım <xref:System.String.Copy%2A?displayProperty=nameWithType> interning önlemek için yöntem. Kopya kurulduktan sonra aynı değer olsa bile iki dizeyi farklı depolama konumları sahip. Dizeleri göstermek için aşağıdaki örneği çalıştırmak `a` ve `b` olan *interned* aynı depolama paylaştıkları anlamına gelir. Dizeleri `a` ve `c` değil.

[!code-csharp-interactive[Demonstrating string interning](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#9)]

> [!NOTE]
> Dizeleri eşitlik için test ettiğinizde, gerçekleştirmek istediğiniz karşılaştırma türünü açıkça belirtmek yöntemlerini kullanmanız gerekir. Kodunuzu daha sürdürülebilir ve okunabilir. Aşırı yöntemlerinden birini kullanın <xref:System.String?displayProperty=nameWithType> ve <xref:System.Array?displayProperty=nameWithType> sınıfları süren bir <xref:System.StringComparison> numaralandırma parametresi. Hangi gerçekleştirmek için karşılaştırma türünü belirtin. Kullanmaktan kaçının `==` ve `!=` eşitlik için test ettiğinizde işleçler. <xref:System.String.CompareTo%2A?displayProperty=nameWithType> Örnek yöntemleri her zaman sıralı büyük küçük harfe duyarlı karşılaştırma gerçekleştirin. Bunlar öncelikle dizeleri alfabetik olarak sıralamak için uygundur.

## <a name="see-also"></a>Ayrıca bkz.
 <xref:System.Globalization.CultureInfo?displayProperty=nameWithType>  
 <xref:System.StringComparer?displayProperty=nameWithType>  
 [Dizeler](../programming-guide/strings/index.md)  
 [Dizeleri Karşılaştırma](../../standard/base-types/comparing.md)  
 [Uygulamaları Genelleştirme ve Yerelleştirme](/visualstudio/ide/globalizing-and-localizing-applications)