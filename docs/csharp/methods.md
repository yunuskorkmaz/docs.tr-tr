---
title: Yöntemler - C# Kılavuzu
description: Yöntemlere, yöntem parametrelerine ve yöntem iade değerlerine genel bakış
ms.technology: csharp-fundamentals
ms.date: 05/21/2018
ms.assetid: 577a8527-1081-4b36-9b9e-0685b6553c6e
ms.openlocfilehash: f44c83408e884d76eef5e2b5abbca511fbae2a1f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399450"
---
# <a name="methods"></a>Yöntemler

Yöntem, bir dizi deyim içeren bir kod bloğudur. Program, yöntem çağırArak ve gerekli yöntem bağımsız değişkenlerini belirterek deyimlerin yürütülmesine neden olur. C#'da, çalıştırılan her yönerge bir yöntem bağlamında gerçekleştirilir. Yöntem `Main` her C# uygulaması için giriş noktasıdır ve program başlatıldığında ortak dil çalışma süresi (CLR) olarak adlandırılır.

> [!NOTE]
> Bu konu adlı yöntemleri tartışır. Anonim işlevler hakkında bilgi için [Bkz. Anonim Fonksiyonlar.](programming-guide/statements-expressions-operators/anonymous-functions.md)

<a name="signatures"></a>

## <a name="method-signatures"></a>Yöntem imzaları

Yöntemler bir `class` veya `struct` belirterek bildirilir:

- İsteğe bağlı bir `public` erişim `private`düzeyi, örneğin. Varsayılan değer: `private`.
- Gibi isteğe bağlı `abstract` `sealed`değiştiriciler veya .
- İade değeri veya `void` yöntemde yok.
- Yöntem adı.
- Herhangi bir yöntem parametreleri. Yöntem parametreleri parantez içinde eklenir ve virgülle ayrılır. Boş parantezler yöntemin parametre gerektirmediğini gösterir.

Bu parçalar birlikte yöntem imzasını oluşturur.

> [!NOTE]
> Yöntemin dönüş türü, yöntem aşırı yükleme amacıyla yöntemin imzasının bir parçası değildir. Ancak, bir temsilci ve işaret ettiği yöntem arasındaki uyumluluğu belirlerken yöntemin imzasının bir parçasıdır.

Aşağıdaki örnekte beş yöntem `Motorcycle` içeren adlandırılmış bir sınıf tanımlanır:

[!code-csharp[csSnippets.Methods#40](../../samples/snippets/csharp/concepts/methods/methods40.cs#40)]

`Motorcycle` Sınıfın aşırı yüklü bir yöntem `Drive`içerdiğini unutmayın. İki yöntem aynı ada sahiptir, ancak parametre türlerine göre ayırt edilmelidir.

<a name="invocation"></a>

## <a name="method-invocation"></a>Yöntem çağırma

Yöntemler *örnek* veya *statik*olabilir. Örnek yöntem çağırmak, bir nesneyi anında alamalısınız ve bu nesneüzerindeki yöntemi çağırın; bir örnek yöntemi o örnek ve verileri üzerinde çalışır. Yöntemin ait olduğu türün adını başvurarak statik bir yöntem çağırırsınız; statik yöntemler örnek veriler üzerinde çalışmaz. Bir nesne örneği aracılığıyla statik bir yöntem çağırmaya çalışmak derleyici hatası oluşturur.

Bir yöntemi çağırmak, bir alana erişmek gibidir. Nesne adı (örnek yöntemi ni çağırıyorsanız) veya tür adı (bir `static` yöntem çağırıyorsanız), bir nokta, yöntemin adını ekleyin ve parantez edin. Bağımsız değişkenler parantez içinde listelenir ve virgülle ayrılır.

Yöntem tanımı, gerekli parametrelerin adlarını ve türlerini belirtir. Bir arayan yöntemi çağırdığında, her parametre için bağımsız değişken adı verilen somut değerler sağlar. Bağımsız değişkenler parametre türüyle uyumlu olmalıdır, ancak çağrı kodunda kullanılan bağımsız değişken adı, yöntemde tanımlanan parametreyle aynı olması gerekmez. Aşağıdaki örnekte, `Square` yöntem `int` *i*adlı tür tek bir parametre içerir. İlk yöntem çağrısı, `Square` *num*adlı `int` tip değişkeninyöntemini geçer; ikincisi, sayısal bir sabit; ve üçüncüsü, bir ifade.

[!code-csharp[csSnippets.Methods#74](../../samples/snippets/csharp/concepts/methods/params74.cs#74)]

Yöntem çağırma en yaygın formu konumsal argümanlar kullanılır; bağımsız değişkenleri yöntem parametreleri ile aynı sırada sağlar. Bu nedenle `Motorcycle` sınıfın yöntemleri aşağıdaki örnekte olduğu gibi çağrılabilir. `Drive` Yönteme çağrı, örneğin, yöntemin sözdiziminde iki parametreye karşılık gelen iki bağımsız değişken içerir. İlk `miles` parametre değeri olur, ikinci `speed` parametre değeri.

[!code-csharp[csSnippets.Methods#41](../../samples/snippets/csharp/concepts/methods/methods40.cs#41)]

Bir yöntem çağırırken konumsal bağımsız değişkenler yerine *adlandırılmış bağımsız değişkenler* de kullanabilirsiniz. Adlandırılmış bağımsız değişkenleri kullanırken, bir üst nokta üst üste (":") ve bağımsız değişkenin ardından parametre adını belirtirsiniz. Gerekli tüm bağımsız değişkenler mevcut olduğu sürece, yöntemin bağımsız değişkenleri herhangi bir sırada görünebilir. Aşağıdaki örnek, yöntemi çağırmak `TestMotorcycle.Drive` için adlandırılmış bağımsız değişkenleri kullanır. Bu örnekte, adlandırılmış bağımsız değişkenler yöntemin parametre listesinden ters sırada geçirilir.

[!code-csharp[csSnippets.Methods#45](../../samples/snippets/csharp/concepts/methods/named1.cs#45)]

Hem konumsal bağımsız değişkenleri hem de adlandırılmış bağımsız değişkenleri kullanarak bir yöntem çağırabilirsiniz. Ancak, konumsal bir bağımsız değişken adlandırılmış bir bağımsız değişkeni izleyemez. Aşağıdaki örnek, bir `TestMotorcycle.Drive` konumsal bağımsız değişken ve bir adlandırılmış bağımsız değişken kullanarak önceki örnekten yöntemi çağırır.

[!code-csharp[csSnippets.Methods#46](../../samples/snippets/csharp/concepts/methods/named2.cs#46)]

<a name="inherited"></a>

## <a name="inherited-and-overridden-methods"></a>Kalıtsal ve geçersiz kılınan yöntemler

Bir türde açıkça tanımlanan üyelere ek olarak, bir tür, temel sınıflarında tanımlanan üyeleri devralır. Yönetilen <xref:System.Object> tür sistemindeki tüm türler sınıftan doğrudan veya dolaylı olarak devraldığı <xref:System.Object.Equals(System.Object)>için, tüm türler , , <xref:System.Object.GetType>ve <xref:System.Object.ToString>. Aşağıdaki örnek, bir `Person` sınıf tanımlar, iki `Person` nesneyi anlık `Person.Equals` olarak çağırır ve iki nesnenin eşit olup olmadığını belirlemek için yöntemi çağırır. Ancak `Equals` yöntem sınıfta tanımlanmaz; `Person` bu miras. <xref:System.Object>

[!code-csharp[csSnippets.Methods#104](../../samples/snippets/csharp/concepts/methods/inherited1.cs#104)]

`override` Türler, anahtar sözcüğü kullanarak ve geçersiz kılınan yöntem için bir uygulama sağlayarak devralınan üyeleri geçersiz kılabilir. Yöntem imzası, geçersiz kılınan yöntemle aynı olmalıdır. Aşağıdaki örnek, <xref:System.Object.Equals(System.Object)> yöntemi geçersiz kılmadışında, önceki örneği gibidir. (Ayrıca, iki <xref:System.Object.GetHashCode> yöntem tutarlı sonuçlar sağlamak için tasarlanmıştır beri yöntemi geçersiz kılar.)

[!code-csharp[csSnippets.Methods#105](../../samples/snippets/csharp/concepts/methods/overridden1.cs#105)]

<a name="passing"></a>

## <a name="passing-parameters"></a>Parametreleri geçirme

C# türü *değer türleri* veya *başvuru türleridir.* Yerleşik değer türlerinin listesi [için, Türleri ve değişkenleri](./tour-of-csharp/types-and-variables.md)görün. Varsayılan olarak, hem değer türleri hem de başvuru türleri değere göre bir yönteme aktarılır.

<a name="byval"></a>

### <a name="passing-parameters-by-value"></a>Parametreleri değere göre geçirme

Değer olarak bir yönteme bir değer aktarıldığında, nesnenin kendisi yerine nesnenin bir kopyası yönteme geçirilir. Bu nedenle, çağrılan yöntemde nesnedeğişiklikleri, denetim arayana döndüğünde özgün nesne üzerinde hiçbir etkisi yoktur.

Aşağıdaki örnek, değere göre bir yönteme bir değer türü geçer ve çağrılan yöntem değer türü değerini değiştirmeye çalışır. Değer türü olan bir `int`tür değişkenini tanımlar, değerini 20'ye başlar ve değişkenin değerini 30'a değiştiren bir `ModifyValue` yönteme geçirir. Ancak yöntem döndüğünde değişkenin değeri değişmeden kalır.

[!code-csharp[csSnippets.Methods#10](../../samples/snippets/csharp/concepts/methods/byvalue10.cs#10)]

Başvuru türündeki bir nesne değer ekiile yönteme geçirildiğinde, nesneye yapılan bir başvuru değere göre geçirilir. Diğer bir zamanda, yöntem nesnenin kendisini değil, nesnenin konumunu gösteren bir bağımsız değişkeni alır. Bu başvuruyu kullanarak nesnenin bir üyesini değiştirirseniz, denetim arama yöntemine döndüğünde değişiklik nesneye yansıtılır. Ancak, yönteme geçirilen nesnenin değiştirilmesi, denetim arayana döndüğünde özgün nesne üzerinde hiçbir etkisi yoktur.

Aşağıdaki örnekte bir sınıf (bir başvuru türü) adlı `SampleRefType`tanımlar. Bir `SampleRefType` nesneyi anında atar, `value` alanına 44 atar ve nesneyi `ModifyObject` yönteme geçirir. Bu örnek, temelde önceki örnekle aynı şeyi yapar -- bir bağımsız değişkeni bir yönteme değer olarak geçirir. Ancak bir başvuru türü kullanıldığından, sonuç farklıdır. `obj.value` Alana yapılan `ModifyObject` değişiklik, örnekteki çıktının `value` gösterdiği gibi, `rt` `Main` yöntemdeki bağımsız değişkenalanını da 33'e değiştirir.

[!code-csharp[csSnippets.Methods#42](../../samples/snippets/csharp/concepts/methods/byvalue42.cs#42)]

<a name="byref"></a>

### <a name="passing-parameters-by-reference"></a>Parametreleri referansa göre geçirme

Bir yöntemdeki bir bağımsız değişkenin değerini değiştirmek istediğinizde ve denetim arama yöntemine döndüğünde bu değişikliği yansıtmak istediğinizde, bir parametreyi başvuru yla geçirirsiniz. Bir parametreyi referansla geçirmek [`ref`](language-reference/keywords/ref.md) için, anahtar kelimeyi veya [`out`](language-reference/keywords/out-parameter-modifier.md) anahtar sözcüğü kullanırsınız. Ayrıca kopyalamayı önlemek için referans olarak bir değer geçirebilir, [`in`](language-reference/keywords/in-parameter-modifier.md) ancak anahtar kelimeyi kullanarak değişiklikleri yine de önleyebilirsiniz.

Aşağıdaki örnek, `ModifyValue` yönteme başvuruyla geçirilen değer dışında, öncekiyle aynıdır. `ModifyValue` Yöntemde parametrenin değeri değiştirildiğinde, denetim arayana döndüğünde değer değişikliği yansıtılır.

[!code-csharp[csSnippets.Methods#106](../../samples/snippets/csharp/concepts/methods/byref106.cs#106)]

Ref parametreleri tarafından kullanılan yaygın bir desen değişkenlerin değerlerini takas içerir. İki değişkeni başvuru yla bir yönteme geçirirsiniz ve yöntem içeriğini değiştirir. Aşağıdaki örnek, sonsayı değerlerini değiştirir.

[!code-csharp[csSnippets.Methods#106](../../samples/snippets/csharp/concepts/methods/swap107.cs#107)]

Başvuru türü parametresi geçmek, tek tek öğelerinin veya alanlarının değeri yerine başvurunun değerini değiştirmenize olanak tanır.

<a name="paramarray"></a>

### <a name="parameter-arrays"></a>Parametre dizileri

Bazen, yönteminizin bağımsız değişkenlerinin tam sayısını belirtme gereksinimi kısıtlayıcıdır. `params` Bir parametrenin bir parametre dizisi olduğunu belirtmek için anahtar sözcüğü kullanarak, yönteminizin değişken sayıda bağımsız değişkenle çağrılmasını sağlarsınız. `params` Anahtar kelimeyle etiketlenen parametre bir dizi türü olmalı ve yöntemin parametre listesindeki son parametre olmalıdır.

Arayan daha sonra yöntemi üç şekilde çağırabilir:

- İstenilen sayıda öğe içeren uygun türde bir dizi geçirerek.
- Yönteme uygun türde bireysel bağımsız değişkenlerin virgülden ayrılmış bir listesini geçirerek.
- Parametre dizilimi için bir bağımsız değişken sağlamayarak.

Aşağıdaki örnek, bir parametre dizisinden tüm sesli harfleri döndüren adlandırılmış `GetVowels` bir yöntem tanımlar. Yöntem, `Main` yöntemi çağırmak için üç yolu da gösterir. Arayanlar, `params` değiştiriciiçeren parametreler için herhangi bir bağımsız değişken sağlamaları gerekmez. Bu durumda, parametre `null`.

[!code-csharp[csSnippets.Methods#75](~/samples/snippets/csharp/concepts/methods/params75.cs#75)]

<a name="optional"></a>

## <a name="optional-parameters-and-arguments"></a>İsteğe bağlı parametreler ve bağımsız değişkenler

Yöntem tanımı, parametrelerinin gerekli olduğunu veya isteğe bağlı olduğunu belirtebilir. Varsayılan olarak, parametreler gereklidir. İsteğe bağlı parametreler, yöntem tanımına parametrenin varsayılan değeri ekleyerek belirtilir. Yöntem çağrıldığında, isteğe bağlı bir parametre için bağımsız değişken sağlanmazsa, varsayılan değer kullanılır.

Parametrenin varsayılan değeri aşağıdaki ifade türlerinden biri tarafından atanmalıdır:

- Bir sabit, bir edebi dize veya sayı gibi.
- Formun `new ValType()`bir ifadesi `ValType` , değer türü nerede. Bunun, değer türünün gerçek bir üyesi olmayan örtük parametresiz oluşturucusu çağırır.
- Formun `default(ValType)`bir ifadesi `ValType` , değer türü nerede.

Bir yöntem hem gerekli hem de isteğe bağlı parametreler içeriyorsa, gerekli tüm parametrelerden sonra parametre listesinin sonunda isteğe bağlı parametreler tanımlanır.

Aşağıdaki örnekte, `ExampleMethod`bir gerekli ve iki isteğe bağlı parametre içeren bir yöntem tanımlanır.

[!code-csharp[csSnippets.Methods#21](../../samples/snippets/csharp/concepts/methods/optional1.cs#21)]

Birden çok isteğe bağlı bağımsız değişkeniçeren bir yöntem konumsal bağımsız değişkenler kullanılarak çağrılırsa, arayan ilkinden bağımsız değişkenin sağlandığı son yönteme kadar tüm isteğe bağlı parametreler için bir bağımsız değişken sağlamalıdır. `ExampleMethod` Yöntem söz konusu olduğunda, örneğin, arayan `description` parametre için bir bağımsız değişken sağlıyorsa, `optionalInt` parametre için de bir bağımsız değişken sağlaması gerekir. `opt.ExampleMethod(2, 2, "Addition of 2 and 2");`geçerli bir yöntem çağrısıdır; `opt.ExampleMethod(2, , "Addition of 2 and 0");` bir "Bağımsız değişken eksik" derleyici hatası oluşturur.

Adlandırılmış bağımsız değişkenler veya konumsal ve adlandırılmış bağımsız değişkenlerin birleşimi kullanılarak bir yöntem çağrılırsa, arayan yöntem çağrısındaki son konumsal bağımsız değişkeni izleyen tüm bağımsız değişkenleri atlayabilir.

Aşağıdaki örnek, `ExampleMethod` yöntemi üç kez çağırır.  İlk iki yöntem konumsal bağımsız değişkenleri kullanır. İlki her iki isteğe bağlı bağımsız değişkeni atlarken, ikinci bağımsız değişken son bağımsız değişkeni atlar. Üçüncü yöntem çağrı, gerekli parametre için konumsal bir bağımsız değişken sağlar, `description` ancak `optionalInt` bağımsız değişkeni atlarken parametreye değer sağlamak için adlandırılmış bir bağımsız değişken kullanır.

[!code-csharp[csSnippets.Methods#22](../../samples/snippets/csharp/concepts/methods/optional1.cs#22)]

İsteğe bağlı parametrelerin kullanımı *aşırı yük çözünürlüğünü*veya C# derleyicisinin bir yöntem çağrısı yla hangi aşırı yükün çağrılması gerektiğini belirleme biçimini aşağıdaki gibi etkiler:

- Parametrelerinin her biri isteğe bağlı ysa veya ada veya konuma göre, çağrı deyimindeki tek bir bağımsız değişkene karşılık gelen ve bu bağımsız değişken parametre türüne dönüştürülebiliyorsa, bir yöntem, dizin oluşturucu veya oluşturucu yürütme için adaydır.
- Birden fazla aday bulunursa, tercih edilen dönüşümler için aşırı yükleme çözümleme kuralları açıkça belirtilen bağımsız değişkenlere uygulanır. İsteğe bağlı parametreler için atlanan bağımsız değişkenler yoksayılır.
- İki adayın eşit derecede iyi olduğuna karar vereliise, tercih, çağrıda bağımsız değişkenlerin atlandığı isteğe bağlı parametrelere sahip olmayan bir adaya gider. Bu, daha az parametreye sahip adaylar için aşırı yük çözümünde genel bir tercihin sonucudur.

<a name="return"></a>

## <a name="return-values"></a>Döndürülen değerler

Yöntemler arayana bir değer döndürebilir. İade türü (yöntem adından önce listelenen tür) değilse, `void`yöntem `return` anahtar sözcüğü kullanarak değeri döndürebilir. Anahtar kelimenin `return` ardından gelen değişken, sabit veya ifadeyle eşleşen bir ifade, bu değeri yöntem arayana döndürecektir. Geçersiz olmayan bir iade türüne sahip `return` yöntemlerin, bir değeri döndürmek için anahtar sözcüğü kullanması gerekir. Anahtar `return` kelime de yöntemin yürütülmesini durdurur.

İade türü ise, `void` `return` değeri olmayan bir deyim, yöntemin yürütülmesini durdurmak için yine de yararlıdır. `return` Anahtar kelime olmadan, yöntem kod bloğunun sonuna ulaştığında yürütmeyi durdurur.

Örneğin, bu iki yöntem, sonlu ları döndürmek için `return` anahtar sözcüğü kullanır:

[!code-csharp[csSnippets.Methods#44](../../samples/snippets/csharp/concepts/methods/return44.cs#44)]

Bir yöntemden döndürülen bir değeri kullanmak için, arama yöntemi nin kendisini her yerde aynı türde bir değerin yeterli olduğu her yerde çağırın yöntemini kullanabilir. İade değerini bir değişkene de atayabilirsiniz. Örneğin, aşağıdaki iki kod örneği aynı amacı gerçekleştirir:

[!code-csharp[csSnippets.Methods#45](../../samples/snippets/csharp/concepts/methods/return44.cs#45)]

[!code-csharp[csSnippets.Methods#46](../../samples/snippets/csharp/concepts/methods/return44.cs#46)]

Yerel bir değişkenkullanarak, bu `result`durumda, bir değeri depolamak için isteğe bağlıdır. Kodun okunabilirliğine yardımcı olabilir veya yöntemin tüm kapsamı için bağımsız değişkenin özgün değerini depolamanız gerekiyorsa gerekli olabilir.

Bazen, yönteminizin tek bir değerden daha fazlasını döndürmesini istersiniz. C# 7.0 ile başlayarak, *tuple türleri* ve *tuple literals*kullanarak kolayca yapabilirsiniz. Tuple türü, tuple elemanlarının veri türlerini tanımlar. Tuple literals döndürülen tuple gerçek değerlerini sağlar. Aşağıdaki örnekte, `(string, string, string, int)` `GetPersonalInfo` yöntem tarafından döndürülen tuple türünü tanımlar. İfade `(per.FirstName, per.MiddleName, per.LastName, per.Age)` tuple literal olduğunu; yöntem, bir `PersonInfo` nesnenin yaşıyla birlikte ilk, orta ve soyadını döndürür.

```csharp
public (string, string, string, int) GetPersonalInfo(string id)
{
    PersonInfo per = PersonInfo.RetrieveInfoById(id);
    return (per.FirstName, per.MiddleName, per.LastName, per.Age);
}
```

Arayan daha sonra aşağıdaki gibi kod ile döndürülen tuple tüketebilir:

```csharp
var person = GetPersonalInfo("111111111")
Console.WriteLine("{person.Item1} {person.Item3}: age = {person.Item4}");
```

Adlar, tuple türü tanımındaki tuple öğelerine de atanabilir. Aşağıdaki örnek, adı geçen `GetPersonalInfo` öğeleri kullanan yöntemin alternatif bir sürümünü gösterir:

```csharp
public (string FName, string MName, string LName, int Age) GetPersonalInfo(string id)
{
    PersonInfo per = PersonInfo.RetrieveInfoById(id);
    return (per.FirstName, per.MiddleName, per.LastName, per.Age);
}
```

`GetPersonInfo` Yönteme önceki çağrı daha sonra aşağıdaki gibi değiştirilebilir:

```csharp
var person = GetPersonalInfo("111111111");
Console.WriteLine("{person.FName} {person.LName}: age = {person.Age}");
```

Bir yöntem bir dizi bağımsız değişken olarak geçirilirse ve tek tek öğelerin değerini değiştirirse, iyi stil veya işlevsel değerler akışı için bunu seçebilirsiniz rağmen, dizi döndürmek için yöntem için gerekli değildir.  Bunun nedeni, C#'ın tüm başvuru türlerini değere göre geçirmesi ve bir dizi referansının değerinin diziişaretçisi olmasıdır. Aşağıdaki örnekte, `values` `DoubleValues` yöntemde yapılan dizinin içeriğindeki değişiklikler, diziye başvuru yapan herhangi bir kod tarafından gözlemlenebilir.

[!code-csharp[csSnippets.Methods#101](../../samples/snippets/csharp/concepts/methods/returnarray1.cs#101)]

<a name="extension"></a>

## <a name="extension-methods"></a>Uzatma yöntemleri

Normalde, varolan bir türe yöntem eklemenin iki yolu vardır:

- Bu tür için kaynak kodunu değiştirin. Türün kaynak koduna sahip değilseniz, elbette bunu yapamazsınız. Ayrıca yöntemi desteklemek için herhangi bir özel veri alanları eklerseniz bu bir kırılma değişikliği olur.
- Türemiş bir sınıfta yeni yöntemi tanımlayın. Yapılar ve sayısallaştırmalar gibi diğer türler için kalıtım kullanılarak bu şekilde bir yöntem eklenemez. Ne de mühürlü bir sınıfa bir yöntem "eklemek" için kullanılabilir.

Uzantı yöntemleri, tür kendisini değiştirmeden veya devralınan bir türde yeni yöntemi uygulamadan varolan bir türe bir yöntem "eklemenize" izin vermez. Uzantı yöntemi de uzattığı türle aynı derlemede ikamet etmek zorunda değildir. Bir uzantı yöntemini, bir türün tanımlı bir üyesiymiş gibi çağırırsınız.

Daha fazla bilgi için [Uzantı Yöntemleri'ne](programming-guide/classes-and-structs/extension-methods.md)bakın.

<a name="async"></a>

## <a name="async-methods"></a>Async Yöntemleri

Async özelliğini kullanarak, açık geri aramalar kullanmadan veya kodunuzu birden çok yöntem veya lambda ifadeleri arasında el ile bölmeden eşzamanlı yöntemler çağırabilirsiniz.

Bir yöntemi [async](language-reference/keywords/async.md) değiştirici ile işaretlerseniz, yöntemde [bekleme](language-reference/operators/await.md) işlecini kullanabilirsiniz. Denetim async `await` yönteminde bir ifadeye ulaştığında, beklenen görev tamamlanmadığında denetim arayanın alıbına döner ve beklenen görev tamamlanana kadar `await` anahtar sözcük ile yöntemdeki ilerleme askıya alınır. Görev tamamlandığında, yürütme yöntemde devam edebilir.

> [!NOTE]
> Async yöntemi, henüz tamamlanmamış ilk beklenen nesneyle karşılaştığında veya önce hangisi gerçekleşirse async yönteminin sonuna geldiğinde arayanın karşısına geçer.

Bir async yöntemi <xref:System.Threading.Tasks.Task%601>, , <xref:System.Threading.Tasks.Task>veya `void`. `void` İade türü öncelikle, `void` iade türünün gerekli olduğu olay işleyicilerini tanımlamak için kullanılır. Döndüren `void` bir async yöntemi beklenemez ve geçersiz döndüren bir yöntemin arayan yöntematar özel durumlar yakalamak olamaz. C# 7.0 ile başlayarak, bir async yöntemi [herhangi bir görev benzeri dönüş türü](./whats-new/csharp-7.md#generalized-async-return-types)ne olabilir.

Aşağıdaki örnekte, `DelayAsync` bir tamsayı döndüren bir iade deyimi olan bir async yöntemidir. Bir async yöntemi olduğundan, yöntem bildiriminin `Task<int>`bir dönüş türü ne sahip olması gerekir. `Task<int>`İade türü olduğundan, aşağıdaki `await` `DoSomethingAsync` `int result = await delayTask` ifadenin gösterdiği gibi, ifadenin değerlendirilmesi bir karşımlama üretir.

[!code-csharp[csSnippets.Methods#102](../../samples/snippets/csharp/concepts/methods/async1.cs#102)]

Bir async yöntemi [herhangi](language-reference/keywords/in-parameter-modifier.md)bir bildiremez , [ref](language-reference/keywords/ref.md), veya [dışarı](language-reference/keywords/out-parameter-modifier.md) parametreleri, ama bu tür parametreleri olan yöntemleri çağırabilir.

 Async yöntemleri hakkında daha fazla bilgi için, [Async ve Await ile Asynchronous Programlama](async.md)bakın , [Async Programları Kontrol Akışı](programming-guide/concepts/async/control-flow-in-async-programs.md), ve [Async İade Türleri](programming-guide/concepts/async/async-return-types.md).

<a name="expr"></a>

## <a name="expression-bodied-members"></a>İfade gövdeli üyeler

Yalnızca bir ifadenin sonucuyla hemen dönen veya yöntemin gövdesi olarak tek bir ifadeye sahip yöntem tanımlarına sahip olması yaygındır.  Bu tür yöntemleri tanımlamak için bir sözdizimi kısayolu vardır: `=>`

```csharp
public Point Move(int dx, int dy) => new Point(x + dx, y + dy);
public void Print() => Console.WriteLine(First + " " + Last);
// Works with operators, properties, and indexers too.
public static Complex operator +(Complex a, Complex b) => a.Add(b);
public string Name => First + " " + Last;
public Customer this[long id] => store.LookupCustomer(id);
```

Yöntem döndürür `void` veya bir async yöntemi ise, yöntemin gövdesi bir deyim ifadesi olmalıdır (lambdas ile aynı).  Özellikler ve dizin leyiciler için salt okunur olmaları gerekir `get` ve erişimci anahtar sözcüğü kullanmazsınız.

<a name="iterators"></a>

## <a name="iterators"></a>Yineleyiciler

Yineleyici, liste veya dizi gibi bir koleksiyon üzerinde özel bir yineleme gerçekleştirir. Bir yineleyici, her öğeyi birer birer döndürmek için [verim iade](language-reference/keywords/yield.md) deyimini kullanır. Bir `yield return` bildirime ulaşıldığında, arayan kişinin dizideki bir sonraki öğeyi isteyebileceği şekilde geçerli konum hatırlanır.

Bir yineleyicinin dönüş türü <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, <xref:System.Collections.Generic.IEnumerator%601>veya .

Daha fazla bilgi için [bkz.](programming-guide/concepts/iterators.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Erişim Değiştiricileri](language-reference/keywords/access-modifiers.md)
- [Statik Sınıflar ve Statik Sınıf Üyeleri](programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
- [Devralma](programming-guide/classes-and-structs/inheritance.md)
- [Soyut ve Korumalı Sınıflar ve Sınıf Üyeleri](programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)
- [params](language-reference/keywords/params.md)
- [çıkış](language-reference/keywords/out-parameter-modifier.md)
- [Referans](language-reference/keywords/ref.md)
- [Inç](language-reference/keywords/in-parameter-modifier.md)
- [Parametreleri Geçirme](programming-guide/classes-and-structs/passing-parameters.md)
