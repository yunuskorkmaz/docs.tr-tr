---
title: Yöntemler-C# Kılavuzu
description: Yöntemlere, yöntem parametrelerine ve yöntem dönüş değerlerine genel bakış
ms.technology: csharp-fundamentals
ms.date: 05/21/2018
ms.assetid: 577a8527-1081-4b36-9b9e-0685b6553c6e
ms.openlocfilehash: 879c553f8df560a3e2f3dccdbbf0d7e8a05c50cd
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89495544"
---
# <a name="methods-in-c"></a>İçindeki Yöntemler (C#)

Yöntemi, bir dizi deyim içeren bir kod bloğudur. Program, metodu çağırarak ve gerekli Yöntem bağımsız değişkenlerini belirterek deyimlerin yürütülmesine neden olur. C# ' de, yürütülen her yönerge bir yöntem bağlamında gerçekleştirilir. `Main`Yöntemi her C# uygulamasının giriş noktasıdır ve program başlatıldığında ortak dil çalışma zamanı (CLR) tarafından çağırılır.

> [!NOTE]
> Bu konuda adlandırılmış yöntemler ele alınmaktadır. Anonim işlevler hakkında daha fazla bilgi için bkz. [Anonim işlevler](programming-guide/statements-expressions-operators/anonymous-functions.md).

<a name="signatures"></a>

## <a name="method-signatures"></a>Yöntem imzaları

Yöntemler bir `class` veya `struct` şunu belirterek belirtilir:

- Veya gibi isteğe bağlı erişim düzeyi `public` `private` . Varsayılan değer: `private`.
- Veya gibi isteğe bağlı `abstract` değiştiriciler `sealed` .
- Dönüş değeri veya `void` metotta hiçbiri yoksa.
- Yöntem adı.
- Herhangi bir yöntem parametresi. Yöntem parametreleri parantez içine alınır ve virgülle ayrılır. Boş parantezler, yöntemin hiçbir parametre gerektirmediğini belirtir.

Bu parçalar birlikte yöntem imzasını oluşturur.

> [!IMPORTANT]
> Bir yöntemin dönüş türü, yöntem aşırı yüklemesi amaçları için yöntemin imzasının bir parçası değildir. Ancak, bir temsilci ve işaret ettiği yöntem arasındaki uyumluluğun belirlenmesi sırasında yönteminin imzasının bir parçasıdır.

Aşağıdaki örnek, beş yöntem içeren adlı bir sınıfı tanımlar `Motorcycle` :

[!code-csharp[csSnippets.Methods#40](../../samples/snippets/csharp/concepts/methods/methods40.cs#40)]

`Motorcycle`Sınıfının aşırı yüklenmiş bir yöntem içerdiğini unutmayın `Drive` . İki yöntem aynı ada sahiptir, ancak parametre türlerine göre farklılaştıralınmalıdır.

<a name="invocation"></a>

## <a name="method-invocation"></a>Yöntem çağırma

Yöntemler *örnek* veya *statik*olabilir. Örnek yöntemini çağırmak için bir nesnesi örneği oluşturabilir ve yöntemi bu nesnede çağırabilirsiniz. örnek yöntemi Bu örnek ve verileri üzerinde çalışır. Yöntemin ait olduğu türün adına başvurarak statik bir yöntem çağırılır; statik yöntemler örnek verilerinde çalışmaz. Bir nesne örneği aracılığıyla statik bir yöntemi çağırma girişimi bir derleyici hatası oluşturur.

Bir yöntemi çağırmak, bir alana erişme gibidir. Nesne adından sonra (bir örnek yöntemi arıyorsanız) veya tür adı (bir `static` yöntemi çağırırken), bir nokta, yöntemin adı ve parantez ekleyin. Bağımsız değişkenler parantez içinde listelenir ve virgülle ayrılır.

Yöntem tanımı, gerekli parametrelerin adlarını ve türlerini belirtir. Bir çağıran yöntemini çağırdığında, her bir parametre için bağımsız değişken olarak adlandırılan somut değerler sağlar. Bağımsız değişkenlerin parametre türüyle uyumlu olması gerekir, ancak çağıran kodda bir tane kullanılırsa bağımsız değişken adının, yönteminde tanımlanan parametre ile aynı olması gerekmez. Aşağıdaki örnekte, `Square` yöntemi i adında tek bir parametre içerir `int` . *i* İlk yöntem çağrısı, `Square` yöntemi `int` *num*; ikinci, sayısal bir sabit ve üçüncü, bir ifade adlı bir değişken olarak geçirir.

[!code-csharp[csSnippets.Methods#74](../../samples/snippets/csharp/concepts/methods/params74.cs#74)]

Yöntem çağırma tarafından kullanılan en yaygın biçim Konumsal bağımsız değişkenler; Yöntem parametreleriyle aynı sırada bağımsız değişkenler sağlar. `Motorcycle`Bu nedenle, sınıfının yöntemleri aşağıdaki örnekte olduğu gibi çağrılabilir. Yöntemine yapılan çağrı, `Drive` Örneğin, yöntemin sözdiziminde iki parametreye karşılık gelen iki bağımsız değişken içerir. İlki parametrenin değeri `miles` , ikinci parametrenin değeri olur `speed` .

[!code-csharp[csSnippets.Methods#41](../../samples/snippets/csharp/concepts/methods/methods40.cs#41)]

Bir yöntemi çağırırken Konumsal bağımsız değişkenler yerine *adlandırılmış bağımsız değişkenler* de kullanabilirsiniz. Adlandırılmış bağımsız değişkenler kullanılırken, ardından iki nokta üst üste (":") ve bağımsız değişken ile parametre adını belirtirsiniz. Yöntem için bağımsız değişkenler tüm gerekli bağımsız değişkenler bulunduğu sürece herhangi bir sırada görünebilir. Aşağıdaki örnek, yöntemini çağırmak için adlandırılmış bağımsız değişkenleri kullanır `TestMotorcycle.Drive` . Bu örnekte, adlandırılmış bağımsız değişkenler metodun parametre listesinden ters sırada geçirilir.

[!code-csharp[csSnippets.Methods#45](../../samples/snippets/csharp/concepts/methods/named1.cs#45)]

Bir yöntemi, hem Konumsal bağımsız değişkenleri hem de adlandırılmış bağımsız değişkenleri kullanarak çağırabilirsiniz. Ancak, Konumsal bağımsız değişkenler yalnızca adlandırılmış bağımsız değişkenler doğru konumlarda olduğunda adlandırılmış bağımsız değişkenleri izleyebilir. Aşağıdaki örnek, `TestMotorcycle.Drive` bir konum bağımsız değişkeni ve bir adlandırılmış bağımsız değişken kullanarak önceki örnekteki yöntemi çağırır.

[!code-csharp[csSnippets.Methods#46](../../samples/snippets/csharp/concepts/methods/named2.cs#46)]

<a name="inherited"></a>

## <a name="inherited-and-overridden-methods"></a>Devralınan ve geçersiz kılınan Yöntemler

Bir tür içinde açıkça tanımlanan üyelere ek olarak, bir tür, temel sınıflarında tanımlanan üyeleri devralır. Yönetilen tür sistemindeki tüm türler doğrudan veya dolaylı olarak sınıfından devraldığı için, <xref:System.Object> tüm türler,, ve gibi üyelerini alırlar <xref:System.Object.Equals(System.Object)> <xref:System.Object.GetType> <xref:System.Object.ToString> . Aşağıdaki örnek, bir `Person` sınıfı tanımlar, iki nesneyi örnekleyen `Person` ve `Person.Equals` iki nesnenin eşit olup olmadığını belirleyen yöntemini çağırır. `Equals`Ancak yöntemi sınıfında tanımlı değildir `Person` ; öğesinden devralınır <xref:System.Object> .

[!code-csharp[csSnippets.Methods#104](../../samples/snippets/csharp/concepts/methods/inherited1.cs#104)]

Türler, anahtar sözcüğünü kullanarak devralınan üyeleri geçersiz kılabilir `override` ve geçersiz kılınan yöntem için bir uygulama sağlar. Yöntem imzası, geçersiz kılınan metodun ile aynı olmalıdır. Aşağıdaki örnek, yönteminin geçersiz kılınmasının dışında, önceki bir <xref:System.Object.Equals(System.Object)> yönteme benzer. (Aynı zamanda yöntemi geçersiz kılar <xref:System.Object.GetHashCode> , çünkü iki yöntem tutarlı sonuçlar sağlamaya yöneliktir.)

[!code-csharp[csSnippets.Methods#105](../../samples/snippets/csharp/concepts/methods/overridden1.cs#105)]

<a name="passing"></a>

## <a name="passing-parameters"></a>Parametreleri geçirme

C# içindeki türler, *değer türleri* ya da *başvuru türleridir*. Yerleşik değer türlerinin bir listesi için bkz. [türler](./tour-of-csharp/types.md). Varsayılan olarak, değer türleri ve başvuru türleri değere göre bir yönteme geçirilir.

<a name="byval"></a>

### <a name="passing-parameters-by-value"></a>Parametreleri değere göre geçirme

Değer türü bir yönteme değere göre geçirildiğinde, nesnesine nesnenin kendisi yerine bir kopyası geçirilir. Bu nedenle, çağrılan yöntemdeki nesne üzerindeki değişikliklerin, Denetim çağırana döndüğünde özgün nesne üzerinde hiçbir etkisi olmaz.

Aşağıdaki örnek bir değer türünü değere göre bir yönteme geçirir ve çağrılan yöntem değer türünün değerini değiştirmeye çalışır. Bir değer türü olan türünde bir değişken tanımlar, `int` değerini 20 olarak başlatır ve `ModifyValue` değişkenin değerini 30 olarak değiştiren adlı bir yönteme geçirir. Ancak yöntemi döndüğünde, değişkenin değeri değişmeden kalır.

[!code-csharp[csSnippets.Methods#10](../../samples/snippets/csharp/concepts/methods/byvalue10.cs#10)]

Başvuru türündeki bir nesne bir değere göre yönteme geçirildiğinde, nesnesine bir başvuru değeri ile geçirilir. Diğer bir deyişle, yöntem nesnenin kendisini değil, nesnenin konumunu gösteren bir bağımsız değişkendir. Bu başvuruyu kullanarak nesnesinin bir üyesini değiştirirseniz, Denetim çağıran yönteme döndüğünde değişiklik nesnesine yansıtılır. Ancak, metoduna geçirilen nesnenin değiştirilmesi, Denetim çağırana döndüğünde özgün nesneyi etkilemez.

Aşağıdaki örnek adlı bir sınıfı (bir başvuru türü) tanımlar `SampleRefType` . Bir nesnesi başlatır `SampleRefType` , alanına 44 atar `value` ve nesneyi `ModifyObject` yöntemine geçirir. Bu örnek temelde önceki örnekle aynı şeyi yapar; bir bağımsız değişkeni değere göre bir yönteme geçirir. Ancak, bir başvuru türü kullanıldığından, sonuç farklıdır. Alanda yapılan değişiklik, `ModifyObject` `obj.value` `value` `rt` `Main` örnekte gösterildiği gibi, yönteminde 33 olan bağımsız değişkenin alanını da değiştirir.

[!code-csharp[csSnippets.Methods#42](../../samples/snippets/csharp/concepts/methods/byvalue42.cs#42)]

<a name="byref"></a>

### <a name="passing-parameters-by-reference"></a>Parametreleri başvuruya göre geçirme

Bir yöntemde bir bağımsız değişkenin değerini değiştirmek istediğinizde ve denetim çağırma yöntemine döndüğünde bu değişikliği yansıtmak istediğinizde, parametreyi başvuruya göre geçirirsiniz. Bir parametreyi başvuruya göre geçirmek için [`ref`](language-reference/keywords/ref.md) veya [`out`](language-reference/keywords/out-parameter-modifier.md) anahtar sözcüğünü kullanırsınız. Kopyalamayı önlemek için bir değeri başvuruya göre geçirebilir, ancak yine de anahtar sözcüğü kullanarak değişiklikleri önleyebilirsiniz [`in`](language-reference/keywords/in-parameter-modifier.md) .

Aşağıdaki örnek, değeri başvuruya göre geçirilme dışında öncekiyle aynıdır `ModifyValue` . Yönteminde parametresinin değeri değiştirildiğinde `ModifyValue` , Denetim çağırana döndüğünde değer değişikliği yansıtılır.

[!code-csharp[csSnippets.Methods#106](../../samples/snippets/csharp/concepts/methods/byref106.cs#106)]

Ref parametreleri tarafından kullanılan ortak bir model, değişkenlerin değerlerini değiştirmeyi içerir. İki değişkeni başvuruya göre bir yönteme geçirirseniz ve yöntemi içeriğini değiştirir. Aşağıdaki örnek, tamsayı değerlerini değiştirir.

[!code-csharp[csSnippets.Methods#106](../../samples/snippets/csharp/concepts/methods/swap107.cs#107)]

Bir başvuru türü parametresinin geçirilmesi, tek öğelerinin veya alanlarının değeri yerine başvurunun kendisinin değerini değiştirmenize izin verir.

<a name="paramarray"></a>

### <a name="parameter-arrays"></a>Parametre dizileri

Bazen, yönteminiz için bağımsız değişkenlerin tam sayısını belirttiğiniz gereksinim kısıtlayıcıdır. `params`Bir parametrenin parametre dizisi olduğunu göstermek için anahtar sözcüğünü kullanarak, yönteminizin değişken sayıda bağımsız değişkenle çağrılmasına izin verebilirsiniz. `params`Anahtar kelimesiyle etiketlenmiş parametre bir dizi türü olmalıdır ve yöntemin parametre listesindeki son parametre olmalıdır.

Bir çağıran daha sonra yöntemi üç yöntemden birini çağırabilir:

- İstenen sayıda öğe içeren uygun türdeki bir diziyi geçirerek.
- Uygun türdeki bağımsız değişkenlerin virgülle ayrılmış bir listesini yöntemine geçirerek.
- Parametre dizisine bir bağımsız değişken sağlamıyor.

Aşağıdaki örnek, `GetVowels` bir parametre dizisinin tüm sesli harfleri döndüren adlı bir yöntemi tanımlar. `Main`Yöntemi, yöntemi çağırmanın üç yolunu gösterir. Değiştirici içeren parametrelere ilişkin bağımsız değişkenler sağlamak için çağıranlar gerekli değildir `params` . Bu durumda, parametresi olur `null` .

[!code-csharp[csSnippets.Methods#75](~/samples/snippets/csharp/concepts/methods/params75.cs#75)]

<a name="optional"></a>

## <a name="optional-parameters-and-arguments"></a>İsteğe bağlı parametreler ve bağımsız değişkenler

Yöntem tanımı parametrelerinin gerekli olduğunu veya isteğe bağlı olduğunu belirtebilir. Varsayılan olarak Parametreler gereklidir. İsteğe bağlı parametreler, parametrenin varsayılan değeri Yöntem tanımına eklenerek belirtilir. Yöntemi çağrıldığında, isteğe bağlı bir parametre için bir bağımsız değişken sağlanmazsa, bunun yerine varsayılan değer kullanılır.

Parametrenin varsayılan değeri aşağıdaki tür ifadelerden biri tarafından atanmalıdır:

- Sabit dize veya sayı gibi bir sabit.
- Formun `new ValType()` bir ifadesi, burada `ValType` bir değer türüdür. Bunun, türün gerçek üyesi olmayan, değer türünün örtük parametresiz oluşturucusunu çağırdığına unutmayın.
- Formun `default(ValType)` bir ifadesi, burada `ValType` bir değer türüdür.

Bir yöntem hem gerekli hem de isteğe bağlı parametreleri içeriyorsa, isteğe bağlı parametreler parametre listesinin sonunda, tüm gerekli parametrelerden sonra tanımlanır.

Aşağıdaki örnek, `ExampleMethod` bir zorunlu ve iki isteğe bağlı parametre içeren bir yöntemini tanımlar.

[!code-csharp[csSnippets.Methods#21](../../samples/snippets/csharp/concepts/methods/optional1.cs#21)]

Birden çok isteğe bağlı bağımsız değişkeni olan bir yöntem Konumsal bağımsız değişkenler kullanılarak çağrılırsa, çağıran ilk bir bağımsız değişken için bağımsız değişkenin sağlandığı en son bir parametre için bir bağımsız değişken sağlamalıdır. Yöntemin söz konusu olduğunda  `ExampleMethod` , örneğin, çağıran parametre için bir bağımsız değişken sağlarsa `description` , bu parametre için de bir tane sağlanmalıdır `optionalInt` . `opt.ExampleMethod(2, 2, "Addition of 2 and 2");` geçerli bir yöntem çağrıdır; `opt.ExampleMethod(2, , "Addition of 2 and 0");` "bağımsız değişken eksik" derleyici hatası oluşturur.

Bir yöntem adlandırılmış bağımsız değişkenler veya konumsal ve adlandırılmış bağımsız değişkenlerin bir birleşimi kullanılarak çağrılırsa, çağıran yöntem çağrısındaki son Konumsal bağımsız değişkeni izleyen tüm bağımsız değişkenleri atlayabilir.

Aşağıdaki örnek, `ExampleMethod` yöntemi üç kez çağırır.  İlk iki yöntem çağıran konum değişkenlerini kullanır. İlki hem isteğe bağlı bağımsız değişkenleri atlar, ikincisi ise son bağımsız değişkeni atlar. Üçüncü yöntem çağrısı, gerekli parametre için bir Konumsal bağımsız değişken sağlar, ancak bağımsız değişkeni atlayarak parametreye bir değer sağlamak için adlandırılmış bir bağımsız değişken kullanır `description` `optionalInt` .

[!code-csharp[csSnippets.Methods#22](../../samples/snippets/csharp/concepts/methods/optional1.cs#22)]

İsteğe bağlı parametrelerin kullanımı, *aşırı yükleme çözünürlüğünü*etkiler veya C# derleyicisinin bir yöntem çağrısı tarafından hangi belirli aşırı yükün çağrılması gerektiğini belirleyen yöntemi aşağıda gösterildiği gibi:

- Bir yöntem, Dizin Oluşturucu veya Oluşturucu, parametrelerinden her biri isteğe bağlı veya bir konuma göre, çağırma deyimindeki tek bir bağımsız değişkene ve bu bağımsız değişken parametre türüne dönüştürülebileceğinden yürütme için bir adaydır.
- Birden fazla aday bulunursa, tercih edilen dönüştürmeler için aşırı yükleme çözümleme kuralları, açıkça belirtilen bağımsız değişkenlere uygulanır. İsteğe bağlı parametreler için Atlanan bağımsız değişkenler yoksayılır.
- İki aday eşit derecede iyi bir şekilde yarar olursa, tercih, çağrıda bağımsız değişkenlerin atlandığı isteğe bağlı parametreleri olmayan bir adaya gider. Bu, daha az parametreye sahip adaylar için aşırı yükleme çözünürlüğünde genel bir tercihin sonucudur.

<a name="return"></a>

## <a name="return-values"></a>Dönüş değerleri

Yöntemler çağırana bir değer döndürebilir. Dönüş türü (yöntem adından önce listelenen tür) değilse `void` , yöntemi anahtar sözcüğünü kullanarak değeri döndürebilir `return` . Anahtar sözcüğünü içeren bir ifade, `return` ardından dönüş türüyle eşleşen bir değişken, sabit veya ifade, bu değeri çağıran yönteme döndürür. `return`Bir değer döndürmek için anahtar sözcüğünü kullanmak için void olmayan bir dönüş türüne sahip metotlar gereklidir. `return`Anahtar sözcüğü, yönteminin yürütülmesini de sonlandırır.

Dönüş türü ise, `void` `return` değeri olmayan bir ifade, metodun yürütülmesini durdurmak için hala yararlıdır. `return`Anahtar sözcüğü olmadan Yöntem, kod bloğunun sonuna ulaştığında yürütmeyi durdurur.

Örneğin, bu iki yöntem `return` tamsayılar döndürmek için anahtar sözcüğünü kullanır:

[!code-csharp[csSnippets.Methods#44](../../samples/snippets/csharp/concepts/methods/return44.cs#44)]

Bir yöntemden döndürülen bir değer kullanmak için, çağırma yöntemi yöntemi tek bir değer olan her yerde, aynı türde bir değer yeterli olacak şekilde kullanabilir. Dönüş değerini bir değişkene de atayabilirsiniz. Örneğin, aşağıdaki iki kod örneği aynı hedefi yerine getirmektedir:

[!code-csharp[csSnippets.Methods#45](../../samples/snippets/csharp/concepts/methods/return44.cs#45)]

[!code-csharp[csSnippets.Methods#46](../../samples/snippets/csharp/concepts/methods/return44.cs#46)]

Bu durumda, `result` bir değeri depolamak için yerel bir değişken kullanmak isteğe bağlıdır. Kodun okunabilirliğini yardımcı olabilir veya metodun tüm kapsamı için bağımsız değişkenin özgün değerini depolamanız gerekirse gerekli olabilir.

Bazen yönteminizin tek bir değerden fazlasını döndürmesini istersiniz. C# 7,0 ' den başlayarak, *kayıt düzeni türlerini* ve *demet sabit*değerlerini kullanarak bunu kolayca yapabilirsiniz. Demet türü, demet öğelerinin veri türlerini tanımlar. Demet sabit değerleri, döndürülen tanımlama grubunun gerçek değerlerini sağlar. Aşağıdaki örnekte, `(string, string, string, int)` yöntemi tarafından döndürülen demet türünü tanımlar `GetPersonalInfo` . İfade, `(per.FirstName, per.MiddleName, per.LastName, per.Age)` tanımlama grubu değişmez değeri; Yöntem, bir nesnenin yaş ve adının yanı sıra birinci, orta ve soyadı döndürür `PersonInfo` .

```csharp
public (string, string, string, int) GetPersonalInfo(string id)
{
    PersonInfo per = PersonInfo.RetrieveInfoById(id);
    return (per.FirstName, per.MiddleName, per.LastName, per.Age);
}
```

Çağıran daha sonra aşağıdaki gibi kodla döndürülen kayıt grubunu kullanabilir:

```csharp
var person = GetPersonalInfo("111111111")
Console.WriteLine("{person.Item1} {person.Item3}: age = {person.Item4}");
```

Adlar, kayıt düzeni türü tanımındaki demet öğelerine de atanabilir. Aşağıdaki örnek, `GetPersonalInfo` adlandırılmış öğeleri kullanan yönteminin alternatif bir sürümünü göstermektedir:

```csharp
public (string FName, string MName, string LName, int Age) GetPersonalInfo(string id)
{
    PersonInfo per = PersonInfo.RetrieveInfoById(id);
    return (per.FirstName, per.MiddleName, per.LastName, per.Age);
}
```

Önceki yönteme yapılan çağrı `GetPersonInfo` daha sonra aşağıdaki gibi değiştirilebilir:

```csharp
var person = GetPersonalInfo("111111111");
Console.WriteLine("{person.FName} {person.LName}: age = {person.Age}");
```

Bir yöntem bir diziyi bağımsız değişken olarak geçirse ve tek tek öğelerin değerini değiştirirse, yöntemin diziyi döndürmesi gerekli değildir, ancak bunun için uygun stil veya işlevsel akış için bunu seçebilirsiniz.  Bunun nedeni C# ' nin tüm başvuru türlerini değere göre geçirme ve dizi başvurusunun değeri dizi işaretçisidir. Aşağıdaki örnekte, yönteminde yapılan dizi içeriklerinde yapılan değişiklikler, `values` `DoubleValues` dizi başvurusu olan herhangi bir kod tarafından Observable ' tır.

[!code-csharp[csSnippets.Methods#101](../../samples/snippets/csharp/concepts/methods/returnarray1.cs#101)]

<a name="extension"></a>

## <a name="extension-methods"></a>Genişletme yöntemleri

Genellikle, varolan bir türe bir yöntem eklemenin iki yolu vardır:

- Bu tür için kaynak kodu değiştirin. Bu, türün kaynak kodunu sahipsiz olmadığınız takdirde bunu yapamazlar. Ayrıca, yöntemi desteklemek için herhangi bir özel veri alanı eklerseniz, bu bir büyük değişiklik haline gelir.
- Yeni metodu türetilmiş bir sınıfta tanımlayın. Bir yöntem, yapılar ve numaralandırmalar gibi diğer türler için devralma kullanılarak bu şekilde eklenemez. Ayrıca, korumalı bir sınıfa bir yöntemi "eklemek" için de kullanılabilir.

Uzantı yöntemleri, türün kendisini değiştirmeden veya yeni yöntemi devralınmış bir tür içinde uygulamadan, varolan bir türe "eklemenize" olanak sağlar. Uzantı yönteminin, genişlettiği türle aynı derlemede bulunması gerekmez. Bir uzantı yöntemini bir türün tanımlı üyesi gibi çağırın.

Daha fazla bilgi için bkz. [Uzantı yöntemleri](programming-guide/classes-and-structs/extension-methods.md).

<a name="async"></a>

## <a name="async-methods"></a>Zaman uyumsuz yöntemler

Async özelliğini kullanarak, açık geri çağırmaları kullanmadan zaman uyumsuz yöntemleri çağırabilir veya kodunuzu birden çok yöntemde veya Lambda ifadelerinde el ile böedebilirsiniz.

[Zaman uyumsuz](language-reference/keywords/async.md) değiştiriciyle bir yöntemi işaretlerseniz, yönteminde [await](language-reference/operators/await.md) işlecini kullanabilirsiniz. Denetim `await` zaman uyumsuz yöntemde bir ifadeye ulaştığında, beklenen görev tamamlanmazsa denetim çağırana döner ve `await` beklenen görev tamamlanana kadar anahtar sözcüğü ile yöntemdeki işlem askıya alınır. Görev tamamlandığında, yürütme yöntemi içinde çalışmaya çalışabilir.

> [!NOTE]
> Zaman uyumsuz bir yöntem, henüz tamamlanmamış olan ilk beklemiş nesneyle karşılaştığında çağırana döner veya zaman uyumsuz yöntemin sonuna kadar, hangisi önce gerçekleşiyorsa.

Zaman uyumsuz bir yöntem,, veya dönüş türüne sahip olabilir <xref:System.Threading.Tasks.Task%601> <xref:System.Threading.Tasks.Task> `void` . `void`Dönüş türü öncelikle bir dönüş türünün gerekli olduğu olay işleyicilerini tanımlamak için kullanılır `void` . Döndüren zaman uyumsuz bir yöntem beklenemez `void` ve void döndüren bir yöntemi çağıran yöntemin aldığı özel durumları yakalayamaz. C# 7,0 ile başlayarak, zaman uyumsuz bir yöntem [herhangi bir görev benzeri dönüş türüne](./whats-new/csharp-7.md#generalized-async-return-types)sahip olabilir.

Aşağıdaki örnekte, `DelayAsync` bir tamsayı döndüren Return ifadesine sahip zaman uyumsuz bir yöntemdir. Zaman uyumsuz bir yöntem olduğundan, metot bildiriminin dönüş türü olmalıdır `Task<int>` . Dönüş türü olduğu için `Task<int>` , `await` içindeki ifadesinin değerlendirmesi, `DoSomethingAsync` aşağıdaki deyimde gösterildiği gibi bir tamsayı oluşturur `int result = await delayTask` .

:::code language="csharp" source="programming-guide/classes-and-structs/snippets/classes-and-structs/methods/Program.cs":::

Zaman uyumsuz bir yöntem hiçbir [içinde](language-reference/keywords/in-parameter-modifier.md), [ref](language-reference/keywords/ref.md)veya [Out](language-reference/keywords/out-parameter-modifier.md) parametrelerini bildiremez, ancak bu parametrelere sahip yöntemleri çağırabilir.

 Zaman uyumsuz yöntemler hakkında daha fazla bilgi için bkz. Async ve await ile zaman uyumsuz [dönüş türleri](programming-guide/concepts/async/async-return-types.md) [ile zaman uyumsuz programlama](async.md) .

<a name="expr"></a>

## <a name="expression-bodied-members"></a>İfade gövdeli üyeler

Yalnızca bir ifadenin sonucuyla hemen dönen veya yöntemin gövdesi olarak tek bir deyimi olan yöntem tanımlarının olması yaygındır.  Kullanarak bu tür yöntemleri tanımlamaya yönelik bir sözdizimi kısayolu vardır `=>` :

```csharp
public Point Move(int dx, int dy) => new Point(x + dx, y + dy);
public void Print() => Console.WriteLine(First + " " + Last);
// Works with operators, properties, and indexers too.
public static Complex operator +(Complex a, Complex b) => a.Add(b);
public string Name => First + " " + Last;
public Customer this[long id] => store.LookupCustomer(id);
```

Yöntemi `void` bir zaman uyumsuz yöntem döndürürse veya ise, yönteminin gövdesi bir deyim ifadesi olmalıdır (Lambdalar ile aynı).  Özellikler ve Dizin oluşturucular için, salt okunurdur ve `get` erişimci anahtar sözcüğünü kullanmayın.

<a name="iterators"></a>

## <a name="iterators"></a>Yineleyiciler

Yineleyici, bir koleksiyon üzerinde liste veya dizi gibi özel bir yineleme gerçekleştirir. Bir yineleyici, her öğeyi birer birer döndürmek için [yield return](language-reference/keywords/yield.md) ifadesini kullanır. Bir `yield return` ifadeye ulaşıldığında, çağıranın sıradaki öğeyi istemesi için geçerli konum hatırlanır.

Yineleyicinin dönüş türü <xref:System.Collections.IEnumerable> ,, <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Collections.IEnumerator> , veya olabilir <xref:System.Collections.Generic.IEnumerator%601> .

Daha fazla bilgi için bkz. [yineleyiciler](programming-guide/concepts/iterators.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Erişim Değiştiricileri](language-reference/keywords/access-modifiers.md)
- [Statik Sınıflar ve Statik Sınıf Üyeleri](programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
- [Devralma](programming-guide/classes-and-structs/inheritance.md)
- [Soyut ve Korumalı Sınıflar ve Sınıf Üyeleri](programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)
- [params](language-reference/keywords/params.md)
- [dışı](language-reference/keywords/out-parameter-modifier.md)
- [ref](language-reference/keywords/ref.md)
- ['ndaki](language-reference/keywords/in-parameter-modifier.md)
- [Parametreleri Geçirme](programming-guide/classes-and-structs/passing-parameters.md)
