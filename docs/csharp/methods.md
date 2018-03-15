---
title: "Yöntemler - C# Kılavuzu"
description: "Yöntem, yöntem parametreleri ve dönüş değerleri yöntemi genel bakış"
keywords: .NET, .NET Core, C#
author: rpetrusha
ms.author: ronpet
ms.date: 10/26/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 577a8527-1081-4b36-9b9e-0685b6553c6e
ms.openlocfilehash: 48127d5168ace7733f29f78dc3f72d9c0d051e4e
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2018
---
# <a name="methods"></a>Yöntemler #

Bir dizi deyimi içeren kod bloğu bir yöntemdir. Bir program yöntemini çağırarak ve tüm gerekli yöntemi bağımsız değişkenleri belirtme yürütülecek deyimleri neden olur. C# ' ta yürütülen her yönerge bir yöntem bağlamında gerçekleştirilir. `Main` Yöntemi her C# uygulaması için giriş noktasıdır ve program başlatıldığında, ortak dil çalışma zamanı tarafından (CLR) adı verilir.

> [!NOTE]
> Bu konu, adlandırılmış yöntemleri açıklar. Anonim işlevler hakkında daha fazla bilgi için bkz: [anonim işlevler](programming-guide/statements-expressions-operators/anonymous-functions.md).

Bu konu aşağıdaki bölümleri içermektedir:

- [Yöntem imzaları](#signatures)
- [Yöntem çağırma](#invocation)
- [Devralınan ve geçersiz kılınan yöntemleri](#inherited)
- [Parametreleri geçirme](#passing)
  - [Parametreleri değere göre geçirme](#byval)
  - [Parametreleri başvuruya göre geçirme](#byref)
  - [Parametre dizileri](#paramarray)
- [İsteğe bağlı parametreler ve bağımsız değişkenler](#optional)
- [Dönüş değerleri](#return)
- [Genişletme yöntemleri](#extension)
- [Zaman uyumsuz yöntemleri](#async)
- [İfade gövdeli üyeler](#expr)
- [Yineleyiciler](#iterators)

<a name="signatures"></a>
## <a name="method-signatures"></a>Yöntem imzaları ##

İçinde bildirilen yöntemleri bir `class` veya `struct` belirterek:

- İsteğe bağlı bir erişim düzeyi, gibi `public` veya `private`. Varsayılan, `private` değeridir.
- İsteğe bağlı değiştiricileri gibi `abstract` veya `sealed`.
- Dönüş değeri veya `void` yöntemi hiçbiri varsa.
- Yöntem adı.
- Herhangi bir yöntem parametreleri. Yöntem parametreleri parantez içine alınmış ve virgülle ayrılır. Boş parantez yöntemi hiçbir parametre gerektirmiyor gösterir.

Bu bölümleri birlikte yöntem imzası oluştururlar.

> [!NOTE]
> Bir yöntemin dönüş türü yöntemi için yöntem aşırı yükleme amacıyla imza parçası değil. Ancak, bir temsilci ve işaret yöntemi uyumluluğu belirlerken yöntemi imzası parçası olan.

Aşağıdaki örnek adlı bir sınıf tanımlar `Motorcycle` beş yöntemleri içerir:

[!code-csharp[csSnippets.Methods#40](../../samples/snippets/csharp/concepts/methods/methods40.cs#40)]

Unutmayın `Motorcycle` sınıfı içeren bir aşırı yüklenmiş yöntemin `Drive`. İki yöntem aynı ada sahip, ancak bunların parametre türleri tarafından ayrıştırılan gerekir.

<a name="invocation"></a>
## <a name="method-invocation"></a>Yöntem çağırma ##

Yöntemleri olabilir ya da *örneği* veya *statik*. Bir örnek yöntemi çağrılırken bir nesne örneği ve bu nesnede metodunu çağırın gerektirir; Bu örnek ve verileri üzerinde örnek yöntemi çalışır. Yöntemin ait olduğu türünün adı başvurarak bir statik yöntem çağırma; statik yöntemler çalışan örnek veriler üzerinde çalıştırmayın. Bir nesne örneği aracılığıyla statik bir yöntem çağrısı çalışılıyor derleyici hatası oluşturur.

Bir yöntemi çağırmak için bir alan erişim gibi olur. Nesne adı (örnek yöntemi arıyorsanız,) veya tür adı sonra (aradığınız varsa bir `static` yöntemi), nokta, yöntemi ve parantez adını ekleyin. Bağımsız değişkenler ayraç içinde listelenmiştir ve virgülle ayrılır.

Yöntem tanımı adlarını ve gerekli olan herhangi bir parametre türlerini belirtir. Çağıran yöntemi çağırır her parametre için bağımsız değişken olarak adlandırılan somut değerleri sağlar. Bağımsız değişken parametre türü ile uyumlu olması gerekir, ancak bir arama kodda kullandıysanız bağımsız değişken adını, aynı adlı parametre yönteminde tanımlanmış olması gerekmez. Aşağıdaki örnekte, `Square` yöntemi içeren tek bir parametre türü `int` adlı *ı*. İlk yöntem çağrısı geçişleri `Square` yöntemi bir değişkeni türü `int` adlı *num*; saniye, sabit bir sayısal değer; ve üçüncü, bir ifade.

[!code-csharp[csSnippets.Methods#74](../../samples/snippets/csharp/concepts/methods/params74.cs#74)]

En yaygın formun yöntemi çağırma konumsal bağımsız değişkenleri kullanılır. Yöntem parametreleri aynı sırada değişkenlerinde sağlar. Yöntemlerinin `Motorcycle` sınıfı bu nedenle aşağıdaki örnekteki çağrılabilir. Çağrı `Drive` yöntemi, örneğin, iki parametre yöntemin sözdiziminde karşılık gelen iki bağımsız değişken içerir. İlk değeri olur `miles` parametresi, ikinci değerini `speed` parametresi.

[!code-csharp[csSnippets.Methods#41](../../samples/snippets/csharp/concepts/methods/methods40.cs#41)]

Ayrıca kullanabilir *bağımsız değişkenleri adlı* yerine bir yöntem çağrılırken, konuma göre bağımsız değişken. Adlandırılmış bağımsız değişkenler kullanma, belirttiğiniz üste parametre adı (":") ve bağımsız değişkeni. Yöntemin bağımsız değişkenler, tüm gerekli bağımsız mevcut olduğu sürece herhangi bir sırada yer alabilir. Aşağıdaki örnek, çağrılacak adlandırılmış bağımsız değişkenler kullanır `TestMotorcycle.Drive` yöntemi. Bu örnekte, adlandırılmış bağımsız değişkenler yöntemin parametre listesinden ters sırada geçirildi.

[!code-csharp[csSnippets.Methods#45](../../samples/snippets/csharp/concepts/methods/named1.cs#45)]

Konumsal iki bağımsız değişken'ı kullanarak bir yöntem çağırabileceği ve adlandırılmış bağımsız değişkenler. Ancak, bir konumsal bağımsız değişkeni bir adlandırılmış bağımsız değişkeni izlenemiyor. Aşağıdaki örnek çağırır `TestMotorcycle.Drive` bir konumsal bağımsız değişkeni ve bir adlandırılmış bağımsız değişkeni kullanarak önceki örnekten yöntemi.

[!code-csharp[csSnippets.Methods#46](../../samples/snippets/csharp/concepts/methods/named2.cs#46)]

 <a name="inherited"></a>
 ##<a name="inherited-and-overridden-methods"></a>Devralınan ve geçersiz kılınan yöntemleri ##

Açıkça bir türde tanımlanan üyeleri ek olarak, bir türü, taban sınıflarından tanımlanan üyeleri devralır. Yönetilen tür sistemi içindeki tüm türler doğrudan veya dolaylı olarak devralınmalıdır beri <xref:System.Object> sınıfı, tüm türleri devral, bu grubun üyeleri gibi <xref:System.Object.Equals(System.Object)>, <xref:System.Object.GetType>, ve <xref:System.Object.ToString>. Aşağıdaki örnek tanımlayan bir `Person` sınıfı, iki başlatır `Person` nesneleri ve çağırır `Person.Equals` iki nesnenin eşit olup olmadığını belirlemek için yöntemi. `Equals` Yöntemi, ancak tanımlı değil de `Person` sınıf; kaynağından devralındı <xref:System.Object>.

[!code-csharp[csSnippets.Methods#104](../../samples/snippets/csharp/concepts/methods/inherited1.cs#104)]

Türlerini kullanarak devralınan üyeleri kılabilirsiniz `override` anahtar sözcüğü ve geçersiz kılınan yöntemi için bir uygulama sağlama. Yöntem imzası geçersiz kılınan yöntemi olarak aynı olmalıdır. Bu geçersiz kılmaları aşağıdaki örnek önceki bir gibi olmasıdır <xref:System.Object.Equals(System.Object)> yöntemi. (Ayrıca geçersiz kılar <xref:System.Object.GetHashCode> tutarlı sonuçlar sağlamak için iki yöntem amaçlandığından yöntemi.)

[!code-csharp[csSnippets.Methods#105](../../samples/snippets/csharp/concepts/methods/overridden1.cs#105)]

<a name="passing"></a>
## <a name="passing-parameters"></a>Parametreleri geçirme ##

C# türleridir ya da *değer türleri* veya *başvuru türleri*. Yerleşik değer türlerinin listesi için bkz: [türleri ve değişkenleri](./tour-of-csharp/types-and-variables.md). Varsayılan olarak, değer türleri ve başvuru türleri bir yönteme değeriyle geçirilir.

<a name="byval"></a>
### <a name="passing-parameters-by-value"></a>Parametreleri değere göre geçirme ###

Değer türü değere göre bir yönteme geçirildiğinde nesnenin nesne yerine bir kopyasını yönteme geçirilir. Bu nedenle, Denetim çağırana döndürüldüğünde çağrılan yöntemin Nesne değişiklikleri özgün nesne üzerinde etkisi yoktur.

Aşağıdaki örnek bir değer türü için bir yöntem tarafından değeri geçirir ve değer türünün değerini değiştirmek çağrılan yöntemin çalışır. Türünde bir değişken tanımlar `int`, bir değer türü, 20 değerine başlatır ve adlı bir yönteme geçirir `ModifyValue` 30 değişkenin değeri değişir. Ancak, yöntem döndüğünde, değişkenin değeri değişmeden kalır.

[!code-csharp[csSnippets.Methods#10](../../samples/snippets/csharp/concepts/methods/byvalue10.cs#10)]

Başvuru türünde bir nesne değeri tarafından bir yönteme geçirildiğinde nesneye bir başvurusu tarafından geçirildi. Diğer bir deyişle, nesnenin kendisini değil ancak nesnenin konumunu belirten bir bağımsız değişken yöntemi alır. Bu başvuru kullanarak nesne üyesi değiştirirseniz, değişiklik denetimi için arama yöntem döndüğünde nesnesinde yansıtılır. Denetim çağırana döndürdüğünde ancak, yönteme geçirilen nesneyi değiştirme özgün nesne üzerinde etkisi yoktur.

Aşağıdaki örnek adında (bir başvuru türü olan) bir sınıfı tanımlar `SampleRefType`. Bunu başlatır bir `SampleRefType` nesne, 44 için atar kendi `value` alan ve nesnesine geçirir `ModifyObject` yöntemi. Bu örnek önceki örnekteki gibi temelde aynı şeyi yapar--bu bağımsız değişken değeri tarafından bir yönteme geçirir. Ancak bir başvuru türü kullanıldığından, sonuç farklıdır. İçinde yapılan değişiklik `ModifyObject` için `obj.value` alan de değişiklikleri `value` bağımsız değişken alan `rt`, `Main` 33, bir yönteme örnek gösterir çıktısı olarak.

[!code-csharp[csSnippets.Methods#42](../../samples/snippets/csharp/concepts/methods/byvalue42.cs#42)]

<a name="byref"></a>
### <a name="passing-parameters-by-reference"></a>Parametreleri başvuruya göre geçirme ###

Bir yöntem bir bağımsız değişken değerini değiştirin ve bu değişiklik denetimi için arama yöntem döndüğünde refect istediğiniz istediğinizde başvuruya göre bir parametre geçirin. Başvuruya göre bir parametre geçirmek için kullandığınız [ `ref` ](language-reference/keywords/ref.md) veya [ `out` ](language-reference/keywords/out-parameter-modifier.md) anahtar sözcüğü. Başvuruya göre kopyalama kaçının ancak hala kullanarak değişiklikleri önlemek için de bir değer geçirebilirsiniz [ `in` ](language-reference/keywords/in-parameter-modifier.md) anahtar sözcüğü.

Başvuru tarafından geçirilen değer dışında aşağıdaki örnekte önceki birine aynıdır `ModifyValue` yöntemi. Parametresinin değeri değiştirildiği içinde `ModifyValue` yöntemi, değerindeki değişikliği denetim çağırana döndürdüğünde yansıtılır.

[!code-csharp[csSnippets.Methods#106](../../samples/snippets/csharp/concepts/methods/byref106.cs#106)]

Ref parametreleri kullanan genel bir desen değişkenlerin değerleri değiştirmeyi içerir. İki değişkenleri başvuruya göre bir yönteme geçirin ve içeriklerini yöntemi değiştirir. Aşağıdaki örnek tamsayı değerleri değiştirir.

[!code-csharp[csSnippets.Methods#106](../../samples/snippets/csharp/concepts/methods/swap107.cs#107)]

Bir başvuru türü parametre geçirme ayrı ayrı öğeler veya alanlar değeri yerine başvuru değeri değiştirmenize izin verir.

<a name="paramarray"></a>
### <a name="parameter-arrays"></a>Parametre dizileri ###

Bazı durumlarda, tam sayıda bağımsız değişken yönteminize belirtin kısıtlayıcı gereksinimdir. Kullanarak `params` parametre dizisine bir parametredir, değişken sayıda bağımsız değişken çağrılacak yönteminizi izin göstermek için anahtar sözcüğü. Parametresi ile etiketlenmiş `params` anahtar sözcüğü bir dizi türünde olması gerekir ve bu yöntemin parametre listesindeki son parametre olmalıdır.

Çağıran, ardından üç yolla yöntemi çağırabilirsiniz:

- Uygun türde bir dizi geçirerek öğeleri istenen sayısını içerir.
- Uygun bir tür bağımsız değişkenleri, virgülle ayrılmış listesini yönteme geçirerek.
- Bir bağımsız değişken parametre dizisine sağlayarak değil.

Aşağıdaki örnek, adlandırılmış bir yöntem tanımlar `DoStringOperation` ilk parametresiyle belirtilen dize işlemi gerçekleştiren bir `StringOperation` numaralandırma üyesi. Sonra işlemi gerçekleştirmek için olduğu dizeleri bir parametre dizisi tarafından tanımlanır. `Main` Yöntemi yöntemi çağırma tüm üç yolu gösterilmektedir. Yöntem ile etiketlenmiş Not `params` anahtar sözcüğü hazırlanmış, böylece değerini bağımsız değişken parametre dizisi için sağlanmaktadır durumu işlemek için `null`.

[!code-csharp[csSnippets.Methods#106](../../samples/snippets/csharp/concepts/methods/byref108.cs#108)]

<a name="optional"></a>
## <a name="optional-parameters-and-arguments"></a>İsteğe bağlı parametreler ve bağımsız değişkenler ##

Bir yöntemin tanımı parametrelerini gerekli veya isteğe bağlı oldukları belirtebilirsiniz. Varsayılan olarak, parametreler gereklidir. İsteğe bağlı parametreler yöntemi tanımı'nda parametrenin varsayılan değeri dahil olmak üzere belirtildi. Yöntem çağrıldığında, bağımsız değişken için isteğe bağlı parametresi belirtilirse, varsayılan değer yerine kullanılır.

Parametrenin varsayılan değeri ifadeleri şu tür biri tarafından atanmış gerekir:

- Değişmez değer dize veya sayı gibi bir sabiti.
- Bir ifade formun `new ValType`, burada `ValType` değer türü değil. Bu tür gerçek bir üyesi değil değer türünün örtük varsayılan oluşturucu çağırır unutmayın.
- Bir ifade formun `default(ValType)`, burada `ValType` değer türü değil.

Bir yöntem gerekli ve isteğe bağlı parametreleri içeriyorsa, isteğe bağlı parametreler parametre listesi, tüm gerekli parametreleri sonunda tanımlanır.

Aşağıdaki örnek, bir yöntem tanımlar `ExampleMethod`, bir gerekli ve isteğe bağlı parametrelerden sahiptir.

[!code-csharp[csSnippets.Methods#21](../../samples/snippets/csharp/concepts/methods/optional1.cs#21)]

Birden çok isteğe bağlı bağımsız değişkenlere sahip bir yöntem kullanarak konumsal bağımsız değişkenlerine çağrılırsa, çağıran bir bağımsız değişken sağlanan sonuncu birinciye tüm isteğe bağlı parametreler için bağımsız değişken girmeniz gerekir. Durumunda `ExampleMethod` yöntemi, örneğin, çağıran bir bağımsız değişken sağlarsa `description` parametresi, onu gerekir ayrıca sağlamak için bir tane `optionalInt` parametresi. `opt.ExampleMethod(2, 2, "Addition of 2 and 2");` Geçerli yöntem çağırma olduğu; `opt.ExampleMethod(2, , "Addition of 2 and 0);` bir "bağımsız değişkeni eksik" oluşturur derleyici hatası.

Adlandırılmış bağımsız değişkenler veya konumsal ve adlandırılmış bağımsız değişkenler bir birleşimini kullanarak bir yöntem çağrılırsa, çağıran yöntem çağrısı son konumsal değişkeninde izleyin herhangi bir bağımsız değişken atlayabilirsiniz.

Aşağıdaki örnek çağrıları `ExampleMethod` yöntemi üç kez.  İlk iki yöntem çağrılarını konumsal bağımsız değişkenlerini kullanın. Son bağımsız değişken ikinci atlar sırada ilk iki isteğe bağlı bağımsız değişkenler atlar. Üçüncü yöntem çağrısı gerekli parametre için konumsal bir bağımsız değişken sağlar, ancak adlandırılmış bağımsız değişkeni için bir değer sağlamak için kullanır `description` atlama sırasında parametre `optionalInt` bağımsız değişkeni.

[!code-csharp[csSnippets.Methods#22](../../samples/snippets/csharp/concepts/methods/optional1.cs#22)]

İsteğe bağlı parametreler kullanımını etkiler *aşırı yükleme çözümü*, veya C# Derleyici belirler belirli hangi aşırı yüklemenin bir yöntem çağrısı tarafından gibi çağrılması gereken şekilde:

- Yöntemi, dizin oluşturucu veya oluşturucusu yürütme aday, tüm parametrelerinin isteğe bağlı olduğu veya karşılık gelen, adıyla veya konuma arama deyiminde tek bir bağımsız değişken ve bağımsız değişken parametre türüne dönüştürülebilir ise.
- Birden fazla aday bulunursa, tercih edilen dönüştürmeleri için aşırı çözümleme kurallarını açıkça belirtilen bağımsız değişkenler için uygulanır. İsteğe bağlı parametreleri belirtilmemişse bağımsız değişkenleri göz ardı edilir.
- İki aday eşit iyi olmasını nitelendirilmiştir, tercih değişkenleri çağrısında atlanmış isteğe bağlı parametreler yok bir aday gider. Daha az parametrelere sahip bir aday aşırı çözünürlük genel bir tercih sonucu budur.

 <a name="return"></a>
 ## <a name="return-values"></a>Döndürülen değerler ##

Yöntemleri bir değer çağırana geri dönebilirsiniz. Dönüş türü (önce yöntem adını listelenen) değilse, `void`, yöntem kullanarak değeri döndürebilir `return` anahtar sözcüğü. With deyimi `return` değişken, sabit veya dönüş türüyle eşleşen ifadesi tarafından anahtar sözcüğünü yöntemi çağırana bu değeri döndürür. Void olmayan yöntemleriyle dönüş türü kullanmak için gerekli `return` bir değer döndürmek üzere anahtar sözcük. `return` Anahtar sözcüğü yönteminin yürütülmesi de durdurulur.

Dönüş türü ise `void`, `return` deyimi bir değer olmadan yönteminin yürütülmesi durdurmak hala faydalıdır. Olmadan `return` anahtar sözcüğü yöntemi durduracak kod bloğunu sonuna ulaştığında yürütülüyor.

Örneğin, bu iki yöntem kullanmak `return` tamsayılar döndürmek için anahtar sözcüğü:

[!code-csharp[csSnippets.Methods#44](../../samples/snippets/csharp/concepts/methods/return44.cs#44)]

Bir yönteminden döndürülen bir değer kullanmak için arama yöntemi aynı türde bir değer yeterli olacaktır yöntem çağrısının kendisini her yerde kullanabilirsiniz. Dönüş değeri bir değişkene de atayabilirsiniz. Örneğin, aşağıdaki iki kod örnekleri aynı hedefe gerçekleştirirsiniz:

[!code-csharp[csSnippets.Methods#45](../../samples/snippets/csharp/concepts/methods/return44.cs#45)]

[!code-csharp[csSnippets.Methods#46](../../samples/snippets/csharp/concepts/methods/return44.cs#46)]

Yerel bir değişken, bu durumda, kullanarak `result`depolamak için bir değer isteğe bağlıdır. Tüm kapsamını yöntemi için bağımsız değişken özgün değeri depolamak gerekiyorsa gerekli olabilir veya kod okunabilirliğini yardımcı olabilir.

Bazen, tek bir değer birden fazla döndürülecek yönteminizi istersiniz. C# 7. 0'dan başlayarak, kolayca kullanarak bunu yapabilirsiniz *kayıt türlerinin* ve *dizi değişmez değerleri*. Kayıt türü demete ait öğeleri veri türlerini tanımlar. Dizi değişmez değerleri döndürülen kayıt gerçek değerler sağlayın. Aşağıdaki örnekte, `(string, string, string, int)` tarafından döndürülen dizi türünü tanımlayan `GetPersonalInfo` yöntemi. İfade `(per.FirstName, per.MiddleName, per.LastName, per.Age)` tanımlama yöntemi döndürür, Orta, adı ve Soyadı, geçerlilik süresi ile birlikte değişmez değer; olan bir `PersonInfo` nesnesi.

```csharp
public (string, string, string, int) GetPersonalInfo(string id)
{
    PersonInfo per = PersonInfo.RetrieveInfoById(id);
    if (per != null)
       return (per.FirstName, per.MiddleName, per.LastName, per.Age);
    else
       return null;
}
```

Çağıran, ardından aşağıdaki gibi kod ile döndürülen tanımlama grubu kullanmasını sağlayabilirsiniz:

```csharp
var person = GetPersonalInfo("111111111")
if (person != null)
   Console.WriteLine("{person.Item1} {person.Item3}: age = {person.Item4}");
```

Adları tanımlama grubu türü tanımında başlığın öğeleri yeniden atanabilir. Aşağıdaki örnek, farklı bir sürümünü gösterir `GetPersonalInfo` kullanan yöntemi adlı öğeleri:

```csharp
public (string FName, string MName, string LName, int Age) GetPersonalInfo(string id)
{
    PersonInfo per = PersonInfo.RetrieveInfoById(id);
    if (per != null)
       return (per.FirstName, per.MiddleName, per.LastName, per.Age);
    else
       return null;
}
```

Önceki çağrısı `GetPersonInfo` yöntemi sonra değiştirilebilir gibi:

```csharp
var person = GetPersonalInfo("111111111");
if (person != null)
   Console.WriteLine("{person.FName} {person.LName}: age = {person.Age}");
```

Bir yöntem bağımsız değişken olarak bir dizi geçirilir ve ayrı ayrı öğeler değerini değiştirir, iyi stili veya değerlerin işlevsel akış için bunu seçebilirsiniz ancak bu yöntem dizi döndürecek şekilde gerekli değildir.  C# değerine göre tüm başvuru türleri geçer ve bir dizi başvurusu dizi yönelik işaretçinin değeri nedeni budur. Aşağıdaki örnekte, içeriğini değiştirir `values` içinde yapılan dizi `DoubleValues` observable dizi başvuruyor herhangi bir kod tarafından bir yöntemdir.

[!code-csharp[csSnippets.Methods#101](../../samples/snippets/csharp/concepts/methods/returnarray1.cs#101)]

 <a name="exten"></a>
 ## <a name="extension-methods"></a>Genişletme yöntemleri ##

Normalde, mevcut bir türle bir yöntem eklemek için iki yolu vardır:

- Bu tür için kaynak kodunu değiştirin. Elbette, tür kaynak kodu kendisine değil, bunu yapamaz. Ve ayrıca yöntemini desteklemek için tüm özel veri alanları eklerseniz, bu önemli bir değişiklik olur.
- Türetilen bir sınıfta yeni yöntemi tanımlayın. Bir yöntemi, yapılar ve numaralandırmalar gibi diğer türleri için devralma kullanarak bu şekilde eklenemez. Veya "korumalı bir sınıf için bir yöntem eklemek için" kullanılabilir.

"Bir yöntem için mevcut bir türle türü değiştirme veya devralınan bir türünün yeni yöntemi uygulama olmadan Ekle" genişletme yöntemleri sağlar. Genişletme yöntemi, onu genişletir türü ile aynı bütünleştirilmiş kodda bulunmasını da yok. Tanımlanan bir tür üyesi değilmiş gibi bir genişletme yöntemi çağırın.

Daha fazla bilgi için bkz: [genişletme yöntemleri](programming-guide/classes-and-structs/extension-methods.md).

<a name="async"></a>
## <a name="async-methods"></a>Zaman uyumsuz yöntemleri ##

Async özelliği kullanarak, açık geri aramalar kullanarak veya birden çok yöntem veya lambda ifadeleri kodunuzu el ile bölme olmadan zaman uyumsuz yöntemleri çağırabilirsiniz.

Bir yöntem ile işaretlerseniz [zaman uyumsuz](language-reference/keywords/async.md) kullanabileceğiniz değiştiricisi, [await](language-reference/keywords/await.md) yönteminde işleci. Ulaştığında denetlemek bir `await` async yöntemi ifadesinde, Denetim döndürür awaited görev tamamlanmadı, çağıran ve yöntemiyle ediyor `await` awaited görevi tamamlanana kadar anahtar sözcüğü askıya alındı. Görev tamamlandığında, yürütme yönteminde devam edebilirsiniz.

> [!NOTE]
> Bir zaman uyumsuz yöntem henüz tamamlanmadı ilk awaited nesne bulduğu veya zaman uyumsuz yönteminin sonuna alır çağırana döndürür hangisi önce gerçekleşir.

Zaman uyumsuz yöntem dönüş türüne sahip olabilir <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task>, veya `void`. `void` Türü öncelikle olay işleyicileri tanımlamak için kullanılan dönüş burada bir `void` dönüş türü gerekli. Döndüren bir zaman uyumsuz yöntem `void` beklemenin olamaz, ve void döndüren bir yöntem arayan yöntemi atar özel durumlarını yakalama olamaz. C# yayımlandığında, 7, bir zaman uyumsuz yöntem izin vermek için bu kısıtlama kolaylaştırır [herhangi bir görev benzeri türü döndürülecek](https://github.com/ljw1004/roslyn/blob/features/async-return/docs/specs/feature%20-%20arbitrary%20async%20returns.md).

Aşağıdaki örnekte, `DelayAsync` bir tamsayı döndürür bir dönüş ifadesi olan bir zaman uyumsuz bir yöntemdir. Bir zaman uyumsuz yöntem olduğu için yöntemi bildiriminden dönüş türüne sahip olmalıdır `Task<int>`. Dönüş türü olduğundan `Task<int>`, değerlendirmesi `await` ifadesinde `DoSomethingAsync` aşağıdaki gibi bir tamsayı üreten `int result = await delayTask` deyimini gösterir.

[!code-csharp[csSnippets.Methods#102](../../samples/snippets/csharp/concepts/methods/async1.cs#102)]

Herhangi bir zaman uyumsuz yöntem bildiremezsiniz [içinde](language-reference/keywords/in-parameter-modifier.md), [ref](language-reference/keywords/ref.md), veya [çıkışı](language-reference/keywords/out-parameter-modifier.md) parametreleri, ancak bu tür parametrelerine sahip yöntemleri çağırabilirsiniz.

 Zaman uyumsuz yöntemleri hakkında daha fazla bilgi için bkz: [uyumsuz ve bekleme ile zaman uyumsuz programlama](async.md), [akış denetimi zaman uyumsuz programlarda](programming-guide/concepts/async/control-flow-in-async-programs.md), ve [zaman uyumsuz dönüş türleri](programming-guide/concepts/async/async-return-types.md).

<a name="expr"></a>
## <a name="expression-bodied-members"></a>İfade bodied üyeleri ##

Yalnızca hemen ifade ile sonuç ya da tek bir deyimde yönteminin gövdesi olarak sahip yöntemi tanımı yaygındır.  Bu tür yöntemlerini kullanarak tanımlamak için bir söz dizimi kısayol yoktur `=>`:

```csharp
public Point Move(int dx, int dy) => new Point(x + dx, y + dy);
public void Print() => Console.WriteLine(First + " " + Last);
// Works with operators, properties, and indexers too.
public static Complex operator +(Complex a, Complex b) => a.Add(b);
public string Name => First + " " + Last;
public Customer this[long id] => store.LookupCustomer(id);
```

Yöntem döndürüyorsa `void` veya bir zaman uyumsuz yöntem yönteminin gövdesi bir deyim ifadesi (aynı Lambda'lar gibi) olmalıdır.  Özellikler ve dizin oluşturucular için salt okunur olmaları gerekir ve kullanmaz `get` erişimci anahtar sözcüğü.

<a name="iterators"></a>
## <a name="iterators"></a>Yineleyiciler ##

Yineleyici özel bir yineleme listesini veya bir dizi gibi bir koleksiyon üzerinden gerçekleştirir. Yineleyici kullanan [verim return](language-reference/keywords/yield.md) her öğeye aynı anda geri dönmek için deyimi. Zaman bir `yield return` arayan dizisi sonraki öğe istemesini deyimi ulaşıldığında, geçerli konumu hatırlanır.

Yineleyici dönüş türü olabilir <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, veya <xref:System.Collections.Generic.IEnumerator%601>.

Daha fazla bilgi için bkz: [yineleyiciler](programming-guide/concepts/iterators.md).

## <a name="see-also"></a>Ayrıca bkz. ##

[Erişim değiştiricileri](language-reference/keywords/access-modifiers.md)   
[Statik sınıflar ve statik sınıf üyeleri](programming-guide/classes-and-structs/static-classes-and-static-class-members.md)   
[Devralma](programming-guide/classes-and-structs/inheritance.md)   
[Soyut ve korumalı sınıflar ve sınıf üyeleri](programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)   
[Parametreleri](language-reference/keywords/params.md)   
[Çıkışı](language-reference/keywords/out-parameter-modifier.md)   
[Ref](language-reference/keywords/ref.md)   
[İçinde](language-reference/keywords/in-parameter-modifier.md)   
[Parametreleri Geçirme](programming-guide/classes-and-structs/passing-parameters.md)
