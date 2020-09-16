---
title: C#-ana dil alanlarının turu
description: C# ' ta yeni misiniz? Dilin temel bilgilerini öğrenin.
ms.date: 08/06/2020
ms.openlocfilehash: 9069bb194169a7743f12d998b2842186ed0ef404
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558181"
---
# <a name="major-language-areas"></a>Ana dil alanları

## <a name="arrays-collections-and-linq"></a>Diziler, koleksiyonlar ve LINQ

C# ve .NET birçok farklı koleksiyon türü sağlar. Diziler, dil tarafından tanımlanan sözdizimine sahiptir. Genel koleksiyon türleri <xref:System.Collections.Generic?displayProperty=fullName> ad alanında listelenir. Özel Koleksiyonlar <xref:System.Span%601?displayProperty=nameWithType> yığın çerçevesindeki sürekli belleğe erişmek ve <xref:System.Memory%601?displayProperty=nameWithType> yönetilen yığında sürekli belleğe erişmek için içerir. Tüm Koleksiyonlar (diziler dahil) <xref:System.Span%601> ve <xref:System.Memory%601> yineleme için bir yönetimlerini birleştirmesiyle sonuçlanır ilkesini paylaşma. <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>Arabirimini kullanırsınız. Bu, koleksiyon türlerinin herhangi birinin LINQ sorguları veya diğer algoritmalarla kullanılabileceği anlamına gelir. Yöntemlerini kullanarak yazarsınız <xref:System.Collections.Generic.IEnumerable%601> ve bu algoritmalar herhangi bir koleksiyonla birlikte çalışır.

### <a name="arrays"></a>Diziler

[***Dizi***](../programming-guide/arrays/index.md) , hesaplanan dizinler üzerinden erişilen çeşitli değişkenler içeren bir veri yapısıdır. Dizinin ***öğeleri*** olarak da adlandırılan bir dizide bulunan değişkenler aynı türde. Bu tür, dizinin ***öğe türü*** olarak adlandırılır.

Dizi türleri başvuru türlerdir ve bir dizi değişkeninin bildirimi, bir dizi örneğine yönelik bir başvuru için yalnızca alan ayırın. Gerçek dizi örnekleri, işleci kullanılarak çalışma zamanında dinamik olarak oluşturulur `new` . `new`İşlem, daha sonra örneğin ömrü boyunca düzeltilen yeni dizi örneğinin ***uzunluğunu*** belirtir. Bir dizi öğelerinin ' den ' a kadar olan dizinleri `0` `Length - 1` . `new`İşleci, bir dizinin öğelerini otomatik olarak varsayılan değerlerine başlatır. Bu, örneğin, tüm sayısal türler ve `null` tüm başvuru türleri için sıfırdır.

Aşağıdaki örnek, bir dizi öğe oluşturur `int` , diziyi başlatır ve dizinin içeriğini yazdırır.

:::code language="csharp" source="./snippets/shared/Features.cs" ID="ArraysSample":::

Bu örnek, ***tek boyutlu bir dizi***üzerinde oluşturur ve çalışır. C#, ***çok boyutlu dizileri***de destekler. Dizi türünün ***derecesi*** olarak da bilinen bir dizi türünün boyut sayısı, dizi türünün köşeli ayraçları arasına yazılan virgüllerin sayısıdır. Aşağıdaki örnek, sırasıyla tek boyutlu, iki boyutlu ve üç boyutlu bir diziyi ayırır.

:::code language="csharp" source="./snippets/shared/Features.cs" ID="DeclareArrays":::

`a1`Dizi 10 öğe içeriyorsa, `a2` dizi 50 (10 × 5) öğesi içerir ve `a3` dizi 100 (10 × 5 × 2) öğesi içerir.
Bir dizinin öğe türü, bir dizi türü de dahil olmak üzere herhangi bir tür olabilir. Dizi türündeki öğeleri içeren bir dizi, bazen öğe dizilerinin uzunluklarının tümünün aynı olması gerektiğinden ***pürüzlü dizi*** olarak adlandırılır. Aşağıdaki örnek dizi dizilerini ayırır `int` :

:::code language="csharp" source="./snippets/shared/Features.cs" ID="ArrayOfArrays":::

İlk satır, her biri türü `int[]` ve her biri bir başlangıç değeri olan üç öğe içeren bir dizi oluşturur `null` . Sonraki satırlar, Farklı uzunluklardaki ayrı dizi örneklerine yönelik başvuruları olan üç öğeyi başlatır.

`new`İşleci, dizi öğelerinin başlangıç değerlerinin, sınırlayıcılar ve arasında yazılan ifadelerin listesi olan bir ***dizi başlatıcısı***kullanılarak belirtilmesine izin verir `{` `}` . Aşağıdaki örnek, üç öğesi ile bir ayırır ve başlatır `int[]` .

:::code language="csharp" source="./snippets/shared/Features.cs" ID="InitializeArray":::

Dizi uzunluğu, ve arasındaki ifade sayısından çıkarsanamıyor `{` `}` . Yerel değişken ve alan bildirimleri daha fazla kısaltılarak, dizi türünün yeniden oluşturulması gerekmez.

:::code language="csharp" source="./snippets/shared/Features.cs" ID="InitializeShortened":::

Yukarıdaki örneklerin her ikisi de aşağıdaki koda eşdeğerdir:

:::code language="csharp" source="./snippets/shared/Features.cs" ID="InitializeGenerated":::

`foreach`Deyimleri herhangi bir koleksiyonun öğelerini numaralandırmak için kullanılabilir. Aşağıdaki kod, önceki örnekteki diziyi numaralandırır:

:::code language="csharp" source="./snippets/shared/Features.cs" ID="EnumerateArray":::

`foreach`İfade <xref:System.Collections.Generic.IEnumerable%601> arabirimini kullanır, bu nedenle herhangi bir koleksiyonla birlikte çalışabilir.

## <a name="string-interpolation"></a>Dize ilişkilendirme

C# [***dize ilişkilendirme***](../language-reference/tokens/interpolated.md) , sonuçları bir biçim dizesine yerleştirilmiş ifadeler tanımlayarak dizeleri biçimlendirmenize olanak sağlar. Örneğin, aşağıdaki örnek, sıcaklığını belirli bir gün için hava durumu verilerinden yazdırır:

:::code language="csharp" source="./snippets/shared/Features.cs" ID="StringInterpolation":::

Enterpolasyonlu bir dize, `$` belirteç kullanılarak bildirilmiştir. Dize ilişkilendirme, ve arasındaki ifadeleri `{` değerlendirir `}` , sonra sonucu bir öğesine dönüştürür `string` ve köşeli ayraçlar arasındaki metni ifadenin dize sonucuyla değiştirir. `:`İlk ifadede, `{weatherData.Date:MM-DD-YYYY}` *biçim dizesini*belirtir. Yukarıdaki örnekte, tarihin "AA-GG-YYYY" biçiminde yazdırılması gerektiğini belirtir.

## <a name="pattern-matching"></a>Desen eşleştirme

C# dili, bir nesnenin durumunu sorgulamak ve bu duruma göre kodu yürütmek için [***kalıp eşleştirme***](../pattern-matching.md) ifadeleri sağlar. Hangi eylemin gerçekleştirilecek olduğunu belirleyebilmek için türleri ve özellik ve alanların değerlerini inceleyebilirsiniz. `switch`İfade, model eşleştirme için birincil ifadedir.

## <a name="delegates-and-lambda-expressions"></a>Temsilciler ve lambda ifadeleri

Bir [***temsilci türü***](../delegates-overview.md) , belirli bir parametre listesi ve dönüş türü olan yöntemlere yapılan başvuruları temsil eder. Temsilciler, yöntemleri değişkenlere atanabilecek ve parametre olarak geçirilen varlıklar olarak işleme olanağı tanır. Temsilciler, bazı diğer dillerde bulunan işlev işaretçileri kavramına benzerdir. İşlev işaretçilerinden farklı olarak, temsilciler nesne odaklı ve tür açısından güvenlidir.

Aşağıdaki örnek adlı bir temsilci türü bildirir ve kullanır `Function` .

:::code language="csharp" source="./snippets/shared/Features.cs" ID="DelegateExample":::

Temsilci türünün bir örneği, `Function` `double` bağımsız değişken alan ve bir değer döndüren herhangi bir yönteme başvurabilir `double` . `Apply`Yöntemi, bir öğesine verilen `Function` öğeleri uygular `double[]` ve `double[]` sonuçları ile döndürür. `Main`Yönteminde, `Apply` bir öğesine üç farklı işlev uygulamak için kullanılır `double[]` .

Bir temsilci, statik bir yönteme (örn `Square` `Math.Sin` . veya önceki örnekte olduğu gibi) ya da bir örnek yöntemine (örneğin `m.Multiply` , önceki örnekte olduğu gibi) başvurabilir. Örnek yönteme başvuran bir temsilci belirli bir nesneye de başvurur ve örnek yöntemi temsilci aracılığıyla çağrıldığında, bu nesne `this` çağrı içinde olur.

Temsilciler, bildirildiği sırada oluşturulan "satır içi Yöntemler" olan anonim işlevler kullanılarak da oluşturulabilir. Anonim işlevler, çevresindeki yöntemlerin yerel değişkenlerini görebilir. Aşağıdaki örnek bir sınıf oluşturmaz:

:::code language="csharp" source="./snippets/shared/Features.cs" ID="UseDelegate":::

Temsilci, başvurduğu yöntemin sınıfını bilmez veya buna uymuyor. Her önemli şey, başvurulan yöntemin aynı parametrelere sahip olması ve temsilciyle aynı türde dönüş türüdür.

## <a name="async--await"></a>zaman uyumsuz/await

C# iki anahtar sözcükle zaman uyumsuz programları destekler: `async` ve `await` . `async`Yöntemin zaman uyumsuz olduğunu bildirmek için bir yöntem bildirimine değiştiricisini eklersiniz. `await`İşleci, derleyicinin bir sonucun bitmesini zaman uyumsuz olarak beklemesini söyler. Denetim çağırana döndürülür ve yöntemi zaman uyumsuz çalışmanın durumunu yöneten bir yapı döndürür. Yapı genellikle bir olur <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> , ancak awaiter modelini destekleyen herhangi bir tür olabilir. Bu özellikler, zaman uyumlu olarak okuyan ve zaman uyumsuz olarak yürüten kodu yazmanızı sağlar. Örneğin, aşağıdaki kod [Microsoft docs](/)için giriş sayfasını indirir:

:::code language="csharp" source="./snippets/shared/Features.cs" ID="AsyncExample":::

Bu küçük örnek, zaman uyumsuz programlama için önemli özellikleri gösterir:

- Yöntem bildirimi, değiştiricisini içerir `async` .
- Yöntemin gövdesi, yönteminin `await` dönüşü `GetByteArrayAsync` .
- İfadesinde belirtilen tür, `return` yöntemi için bildirimdeki tür bağımsız değişkeniyle eşleşir `Task<T>` . (Bir `Task` `return` bağımsız değişken içermeyen deyimleri kullanan bir yöntem).

## <a name="attributes"></a>Öznitelikler

Bir C# programındaki türler, Üyeler ve diğer varlıklar, davranışlarının belirli yönlerini denetleyen değiştiricileri destekler. Örneğin, bir yöntemin erişilebilirliği,,, `public` `protected` `internal` ve değiştiricileri kullanılarak denetlenir `private` . C#, bu özelliği, Kullanıcı tanımlı bildirime dayalı bilgi türleri program varlıklarına iliştirilebilecek ve çalışma zamanında alınabilecek şekilde genelleştirir. Programlar, [***öznitelikleri***](../programming-guide/concepts/attributes/index.md)tanımlayarak ve kullanarak bu ek bildirime dayalı bilgileri belirtir.

Aşağıdaki örnek, `HelpAttribute` ilişkili belgelerinin bağlantılarını sağlamak için program varlıklarına yerleştirilebilecek bir özniteliği bildirir.

:::code language="csharp" source="./snippets/shared/Features.cs" ID="DefineAttribute":::

Tüm öznitelik sınıfları <xref:System.Attribute> , .NET kitaplığı tarafından sunulan temel sınıftan türetilir. Öznitelikler, ilişkili bildirimden hemen önceki köşeli parantez içinde, adı ve bağımsız değişkenlerle birlikte uygulanabilir. Bir özniteliğin adı içinde biterse `Attribute` , özniteliğe başvuruluyorsa adın bu bölümü atlanabilir. Örneğin, `HelpAttribute` aşağıdaki gibi kullanılabilir.

:::code language="csharp" source="./snippets/shared/Features.cs" ID="UseAttributes":::

Bu örnek sınıfına bir iliştirir `HelpAttribute` `Widget` . `HelpAttribute`Sınıfında yöntemine bir tane ekler `Display` . Öznitelik sınıfının ortak oluşturucuları, özniteliği bir program varlığına eklendiğinde sağlanması gereken bilgileri denetler. Öznitelik sınıfının genel okuma-yazma özelliklerine (daha önce özelliğine başvuru gibi) başvurarak ek bilgiler sunulabilir `Topic` .

Öznitelikler tarafından tanımlanan meta veriler, yansıma kullanılarak çalışma zamanında okunabilir ve değiştirilebilir. Bu tekniği kullanarak belirli bir öznitelik istendiğinde, öznitelik sınıfı için Oluşturucu program kaynağında sağlanan bilgilerle çağrılır ve sonuçta elde edilen öznitelik örneği döndürülür. Özellikler aracılığıyla ek bilgiler sağlanmışsa, öznitelik örneği döndürülmeden önce bu özellikler verilen değerlere ayarlanır.

Aşağıdaki kod örneği, `HelpAttribute` sınıfıyla ve yöntemiyle ilişkili örneklerin nasıl alınacağını gösterir `Widget` `Display` .

:::code language="csharp" source="./snippets/shared/Features.cs" ID="ReadAttributes":::

## <a name="learn-more"></a>Daha fazla bilgi edinin

[Öğreticilerimizden](../tutorials/index.md)birini deneyerek C# hakkında daha fazla bilgi bulabilirsiniz.

>[!div class="step-by-step"]
>[Önceki](program-building-blocks.md)
