---
title: Yöntemler - C# Kılavuzu
description: Yöntem, yöntem parametreleri ve dönüş değerleri yöntemi genel bakış
author: rpetrusha
ms.author: ronpet
ms.date: 05/21/2018
ms.assetid: 577a8527-1081-4b36-9b9e-0685b6553c6e
ms.openlocfilehash: 9e7434f2267baf82021dfb3875f2da39552e72ef
ms.sourcegitcommit: 462dc41a13942e467984e48f4018d1f79ae67346
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58186084"
---
# <a name="methods"></a>Yöntemler

Bir dizi deyim içeren kod bloğu bir yöntemdir. Bir program yöntemini çağırarak ve tüm gerekli metot bağımsız değişkenleri belirtme yürütülecek deyimler neden olur. C# içinde yürütülen her yönerge bir yöntem bağlamında gerçekleştirilir. `Main` Yöntemi her C# uygulaması için giriş noktasıdır ve programı başlatıldığında ortak dil çalışma zamanı tarafından (CLR) çağrılır.

> [!NOTE]
> Bu konuda, adlandırılmış yöntemler anlatılmaktadır. Anonim işlevler hakkında daha fazla bilgi için bkz: [anonim işlevler](programming-guide/statements-expressions-operators/anonymous-functions.md).

Bu konu aşağıdaki bölümleri içermektedir:

- [Yöntem imzaları](#signatures)
- [Yöntem çağırma](#invocation)
- [Devralınan ve geçersiz kılınan yöntemleri](#inherited)
- [Parametreleri geçirme](#passing)
  - [Parametrelerin değere göre geçirme](#byval)
  - [Parametreleri başvuruya göre geçirme](#byref)
  - [Parametre dizileri](#paramarray)
- [İsteğe bağlı parametreler ve bağımsız değişkenler](#optional)
- [Dönüş değerleri](#return)
- [Genişletme yöntemleri](#extension)
- [Zaman uyumsuz yöntemler](#async)
- [İfade gövdeli üyeler](#expr)
- [Yineleyiciler](#iterators)

<a name="signatures"></a>

## <a name="method-signatures"></a>Yöntem imzaları

Yöntem içinde bildirilen bir `class` veya `struct` belirterek:

- İsteğe bağlı bir erişim düzeyi, gibi `public` veya `private`. Varsayılan, `private` değeridir.
- İsteğe bağlı değiştiricilere gibi `abstract` veya `sealed`.
- Dönüş değeri veya `void` yöntemi hiçbiri varsa.
- Yöntem adı.
- Herhangi bir yöntem parametreleri. Yöntem parametreleri ayraç içine alınır ve virgülle ayrılır. Boş ayraçlar yöntemi hiçbir parametre gerektirmiyor gösterir.

Bu parçaların birlikte yöntem imzası oluşturur.

> [!NOTE]
> Bir yöntemin dönüş türü yöntemi aşırı yükleme amaçları için yöntem imzasının bir parçası değil. Ancak, bir temsilci ve işaret yöntemi arasındaki uyumluluk belirlerken metodun imzası bir parçası olur.

Aşağıdaki örnek adlı bir sınıf tanımlar `Motorcycle` , beş yöntemleri içerir:

[!code-csharp[csSnippets.Methods#40](../../samples/snippets/csharp/concepts/methods/methods40.cs#40)]

Unutmayın `Motorcycle` sınıfı içeren bir aşırı yüklenmiş yöntem `Drive`. İki yöntem aynı ada sahip, ancak kendi parametre türlerine göre ayırt edilebilir.

<a name="invocation"></a>

## <a name="method-invocation"></a>Yöntem çağırma

Yöntem ya da olabilir *örneği* veya *statik*. Bir örnek yöntemi çağrılırken bir nesne örneği oluşturun ve bu nesnede yöntemi çağrısı gerektirir; bir örnek yöntemi, bu örneği ve verileri üzerinde çalışır. Statik bir yöntemi, yöntemin ait olduğu tür adını başvurarak Çağır; statik yöntemler, örnek veri çalıştırmayın. Bir nesne örneği aracılığıyla statik bir yöntemi çağırmak çalışırken, bir derleyici hatası oluşturur.

Bir alan erişme gibi olan bir yöntemi çağırmak. Nesne adı (bir örnek yöntemi çağırıyorsanız) ya da tür adı (çağırıyorsanız, bir `static` yöntemi), nokta, adı yöntemi ve parantez ekleyin. Bağımsız değişkenler, parantez içinde listelenir ve virgülle ayrılır.

Yöntem tanımını adlarını ve türlerini, gerekli olan herhangi bir parametre belirtir. Arayanın yöntemi çağırdığında, her parametre için bir bağımsız değişken olarak adlandırılan somut değerleri sağlar. Bağımsız değişken parametre türü ile uyumlu olması gerekir, ancak çağıran kod içinde kullanılıyorsa bağımsız değişken adı aynı adlı bir parametre olarak yönteminde tanımlanmış olması gerekmez. Aşağıdaki örnekte, `Square` yöntemi içeren tek bir parametre türü `int` adlı *miyim*. İlk yöntem çağrısı geçişleri `Square` türünde değişken bir yöntem `int` adlı *num*; ikinci, sayısal sabit; ve üçüncü, bir ifade.

[!code-csharp[csSnippets.Methods#74](../../samples/snippets/csharp/concepts/methods/params74.cs#74)]

Konumsal bağımsız değişkenler en yaygın formun yöntemi çağrısının kullanılır. Bu yöntem parametreleri aynı sırada bağımsız değişkenleri sağlar. Yöntemlerinin `Motorcycle` sınıfı bu nedenle aşağıdaki örnekte olduğu gibi çağrılabilir. Çağrı `Drive` yöntemi, örneğin, iki parametre yöntemin sözdiziminde karşılık gelen iki bağımsız değişken içerir. İlk değeri olur `miles` parametresi, ikinci değeri `speed` parametresi.

[!code-csharp[csSnippets.Methods#41](../../samples/snippets/csharp/concepts/methods/methods40.cs#41)]

Ayrıca kullanılabilir *adlandırılmış bağımsız değişkenler* yerine bir yöntem çağrılırken konumsal bağımsız değişkenler. Adlandırılmış bağımsız değişkenler kullanarak, belirttiğiniz üste parametre adı (":") ve bağımsız değişken. Yöntemi için bağımsız değişkeni, tüm gerekli bağımsız değişkenler mevcut olduğu sürece herhangi bir sırada görünebilir. Aşağıdaki örnek, adlandırılmış bağımsız değişkenler çağrılacak kullanır `TestMotorcycle.Drive` yöntemi. Bu örnekte, yöntem parametresi listesinden ters sırada adlandırılmış bağımsız değişkenler geçirilir.

[!code-csharp[csSnippets.Methods#45](../../samples/snippets/csharp/concepts/methods/named1.cs#45)]

Hem konumsal bağımsız değişkenleri kullanarak bir yöntemi çağırabilir ve adlandırılmış bağımsız değişkenler. Ancak, konumsal bağımsız değişken bir adlandırılmış bağımsız değişken gelemez. Aşağıdaki örnek çağırır `TestMotorcycle.Drive` konumsal bağımsız değişken ve bir adlandırılmış bağımsız değişken kullanarak önceki örnekte yöntemi.

[!code-csharp[csSnippets.Methods#46](../../samples/snippets/csharp/concepts/methods/named2.cs#46)]

<a name="inherited"></a>

## <a name="inherited-and-overridden-methods"></a>Devralınan ve geçersiz kılınan yöntemleri

Açık bir tür içinde tanımlanan üyeler ek olarak, bir tür temel sınıflarının içinde tanımlanan üyelerini devralır. Yönetilen tür sistemindeki tüm türleri doğrudan veya dolaylı olarak devralınacak beri <xref:System.Object> sınıfı, tüm türleri devralır, bu grubun üyeleri gibi <xref:System.Object.Equals(System.Object)>, <xref:System.Object.GetType>, ve <xref:System.Object.ToString>. Aşağıdaki örnekte tanımlayan bir `Person` sınıfı, iki `Person` nesneleri ve çağıran `Person.Equals` iki nesnenin eşit olup olmadığını belirlemek için yöntemi. `Equals` Yöntemi, ancak tanımlı değil `Person` sınıfı; öğesinden devralındı <xref:System.Object>.

[!code-csharp[csSnippets.Methods#104](../../samples/snippets/csharp/concepts/methods/inherited1.cs#104)]

Türleri kullanarak devralınan üyeleri kılabilir `override` anahtar sözcüğü ve geçersiz kılınan yöntemi için bir uygulama sağlama. Yöntem imzası, geçersiz kılınan yöntemi ile aynı olmalıdır. Bu geçersiz kılmaları hariç, aşağıdaki örnek Öncekine, <xref:System.Object.Equals(System.Object)> yöntemi. (Ayrıca geçersiz kılar <xref:System.Object.GetHashCode> yöntemi, bu yana iki yöntem, tutarlı sonuçlar sağlamak için tasarlanmıştır.)

[!code-csharp[csSnippets.Methods#105](../../samples/snippets/csharp/concepts/methods/overridden1.cs#105)]

<a name="passing"></a>

## <a name="passing-parameters"></a>Parametreleri geçirme

C# türlerinde değerleri *değer türleri* veya *başvuru türleri*. Yerleşik türlerin listesi için bkz. [türler ve değişkenler](./tour-of-csharp/types-and-variables.md). Varsayılan olarak, hem değer türleri ve başvuru türleri için bir yöntem değere göre geçirilir.

<a name="byval"></a>

### <a name="passing-parameters-by-value"></a>Parametrelerin değere göre geçirme

Bir değer türü değere göre bir yönteme geçildiğinde, nesnenin kendisi yerine nesnesinin bir kopyasını yöntemine geçirilir. Bu nedenle, Denetim çağırana döndürüldüğünde çağrılan yöntem nesnesinde yapılan özgün nesne üzerinde etkisi yoktur.

Aşağıdaki örnek bir değer türü değere göre bir yönteme geçirir ve değer türün değeri değiştirmek çağrılan yöntem çalışır. Türünün değişkenini tanımlar `int`, bir değer türüdür, 20 değerine başlatır ve adlandırılmış bir yönteme geçirir `ModifyValue` 30, değişkenin değeri değişir. Ancak, bu yöntem döndüğünde, değişkenin değeri değişmeden kalır.

[!code-csharp[csSnippets.Methods#10](../../samples/snippets/csharp/concepts/methods/byvalue10.cs#10)]

Başvuru türünde bir nesne değerine göre bir yönteme geçildiğinde nesnesine bir başvuru değere göre geçirilir. Diğer bir deyişle, yöntem, nesnenin kendisini değil, ancak nesnenin konumu gösteren bir bağımsız değişken alır. Bu başvuruyu kullanarak bir nesnenin üyesi değiştirirseniz, Denetim çağıran Metoda döndürür değişiklik nesnesinde yansıtılır. Denetim çağırana döner, ancak, yönteme geçirilen nesneyi değiştirme özgün nesne üzerinde etkisi yoktur.

Aşağıdaki örnekte adlı (bir başvuru türü olan) bir sınıf tanımlar `SampleRefType`. Örneğini oluşturduğunda bir `SampleRefType` nesne, 44 için atar, `value` alan ve nesneye geçirir `ModifyObject` yöntemi. Bu örnek önceki örneğe temelde aynı şeyi yapar; bu bağımsız değişken değerine göre bir yönteme geçirir. Ancak bir başvuru türü kullanıldığından sonucu farklıdır. İçinde yapılan değişikliği `ModifyObject` için `obj.value` alan da değişiklikleri `value` bağımsız değişken alan `rt`, `Main` 33, bir yönteme örnekteki çıktısı olarak.

[!code-csharp[csSnippets.Methods#42](../../samples/snippets/csharp/concepts/methods/byvalue42.cs#42)]

<a name="byref"></a>

### <a name="passing-parameters-by-reference"></a>Parametreleri başvuruya göre geçirme

Yöntemde bir bağımsız değişkeninin değerini değiştirme ve denetimi çağıran Metoda döndürür, bu değişikliği yansıtacak şekilde istediğiniz istediğinizde başvuruya göre bir parametre geçirin. Başvuruya göre bir parametre geçirmek için kullandığınız [ `ref` ](language-reference/keywords/ref.md) veya [ `out` ](language-reference/keywords/out-parameter-modifier.md) anahtar sözcüğü. Başvuruya göre kopyalama kaçının ancak yine de kullanarak değişiklikleri önlemek için de bir değer geçirebilirsiniz [ `in` ](language-reference/keywords/in-parameter-modifier.md) anahtar sözcüğü.

Başvuru tarafından geçirilen değer dışında aşağıdaki örnek, önceki bir, aynı `ModifyValue` yöntemi. İçinde parametresinin değeri değiştirildiğinde `ModifyValue` değerindeki yöntemi, Denetim arayana geri döndüğünde yansıtılır.

[!code-csharp[csSnippets.Methods#106](../../samples/snippets/csharp/concepts/methods/byref106.cs#106)]

Ref parametreleri kullanan bir ortak desen, değişkenlerin değerleri değiştirmeyi içerir. İki değişken başvuru ile bir yönteme geçirin ve bunların içeriğini yöntemi değiştirir. Aşağıdaki örnek, tamsayı değerlerini değiştirir.

[!code-csharp[csSnippets.Methods#106](../../samples/snippets/csharp/concepts/methods/swap107.cs#107)]

Bir başvuru türü parametre geçirerek, ayrı ayrı öğeler veya alanlar yerine başvuru değeri değiştirmenize izin verir.

<a name="paramarray"></a>

### <a name="parameter-arrays"></a>Parametre dizileri

Bazı durumlarda, yönteminize tam sayı bağımsız değişkenleri belirtme gereksinimi sınırlayıcıdır. Kullanarak `params` anahtar sözcüğü, bir parametre dizisi bir parametredir, değişken sayıda bağımsız değişkenle çağrılması yönteminizi izin belirtmek için. Parametresi ile etiketlenmiş `params` anahtar sözcüğü, bir dizi türü olmalıdır ve yöntemin parametre listesindeki son parametre olmalıdır.

Çağıran, sonra üç yoldan biriyle yöntemi çağırabilirsiniz:

- Uygun türde bir dizi geçirerek İstenen öğe sayısını içerir.
- Yöntemine geçirerek uygun türde bağımsız değişkenlerin virgülle ayrılmış listesi.
- Parametre dizisi bağımsız değişkeni sağlayarak değil.

Aşağıdaki örnek adlı bir yöntem tanımlar `DoStringOperation` kendi ilk parametre tarafından belirtilen dize işlemi gerçekleştiren bir `StringOperation` numaralandırma üyesi. Bu işlemi gerçekleştirmek için olduğu dizeleri bir parametre dizisi tarafından tanımlanır. `Main` Yöntemi metodu çağrılırken, tüm üç yol göstermektedir. Yöntem ile etiketlenmiş Not `params` anahtar sözcüğü hazır, böylece değerini parametre dizisi için hiçbir bağımsız değişken sağlanmazsa durumu işlemek için `null`.

[!code-csharp[csSnippets.Methods#106](../../samples/snippets/csharp/concepts/methods/byref108.cs#108)]

<a name="optional"></a>

## <a name="optional-parameters-and-arguments"></a>İsteğe bağlı parametreler ve bağımsız değişkenler

Parametreleri gerekli veya isteğe bağlı bir yöntem tanımını belirtebilirsiniz. Varsayılan olarak, gerekli parametrelerdir. İsteğe bağlı parametreler parametrenin varsayılan değeri yöntem tanımında dahil ederek belirtilir. Yöntem çağrıldığında, isteğe bağlı bir parametre için hiçbir bağımsız değişken sağlanmazsa, bunun yerine varsayılan değeri kullanılır.

Parametrenin varsayılan değeri aşağıdaki türde ifadeler biri tarafından atanmış olmalıdır:

- Bir değişmez değer dize veya sayı gibi bir sabit.
- Bir ifade formun `new ValType`burada `ValType` bir değer türüdür. Bu bir gerçek üye türü değil. değer türünün örtülü varsayılan oluşturucu çağırır unutmayın.
- Bir ifade formun `default(ValType)`burada `ValType` bir değer türüdür.

Bir yöntem gerekli ve isteğe bağlı parametreleri içeriyorsa, isteğe bağlı parametreler tüm gerekli parametreleri parametre listesinin sonunda tanımlanır.

Aşağıdaki örnek bir yöntemi tanımlar `ExampleMethod`, biri gerekli ve isteğe bağlı parametrelerden sahiptir.

[!code-csharp[csSnippets.Methods#21](../../samples/snippets/csharp/concepts/methods/optional1.cs#21)]

Birden fazla isteğe bağlı bağımsız değişkenlere sahip bir yöntemi, konumsal bağımsız değişkenler kullanarak çağrılır, çağrıyı birinci bağımsız değişken olarak sağlanan sonuncu için isteğe bağlı tüm parametreler için bağımsız değişken sağlamalısınız. Durumunda, `ExampleMethod` arayan için bağımsız değişken sağlar. Örneğin, bir yöntem `description` parametresi gerekir ayrıca sağlaması için bir tane `optionalInt` parametresi. `opt.ExampleMethod(2, 2, "Addition of 2 and 2");` Geçerli bir yöntem çağrısı sınıflandırabilirsiniz. `opt.ExampleMethod(2, , "Addition of 2 and 0");` bir "bağımsız değişkeni eksik" oluşturur derleyici hatası.

Adlandırılmış bağımsız değişkenler veya konumsal ve adlandırılmış bağımsız değişken bir birleşimini kullanarak bir yöntemi çağrılırsa, çağıran yöntem çağrısında son konumsal bağımsız değişken izleyen herhangi bir bağımsız değişken atlayabilirsiniz.

Aşağıdaki örnek çağrıları `ExampleMethod` üç kez yöntemi.  İlk iki yöntem çağrılarını konumsal bağımsız değişkenler kullanın. Son bağımsız değişken ikinci atlar sırasında ilk iki isteğe bağlı bağımsız değişkenlere atlar. Üçüncü yöntem çağrısı gerekli parametre için konumsal bağımsız değişken sağlar, ancak adlandırılmış bir bağımsız değişken için bir değer sağlamak için kullandığı `description` atlama sırasında parametre `optionalInt` bağımsız değişken.

[!code-csharp[csSnippets.Methods#22](../../samples/snippets/csharp/concepts/methods/optional1.cs#22)]

İsteğe bağlı parametreler kullanımını etkiler *aşırı yükleme çözümlemesi*, ya da C# derleyicisi belirleyen bir yöntem çağrısı tarafından hangi belirli bir aşırı yükleme gibi çağrılmalıdır yolu:

- Yöntem, dizin oluşturucu veya Oluşturucu bir aday yürütme için kendi parametrelerinin her biri, isteğe bağlı olduğunu veya karşılık gelen, adına veya konumuna çağrı deyimindeki tek bir bağımsız değişken ve bağımsız değişken, parametre türüne dönüştürülebilen olur.
- Birden fazla aday bulunursa, tercih edilen dönüştürmeler için aşırı yükleme çözünürlüğü kuralları açıkça belirtilen bağımsız değişkenler için uygulanır. İsteğe bağlı parametreler için atlanmış bağımsız değişkenler yoksayılır.
- İki adayları eşit derecede iyi olmasını materyali çağrıda atlanıp bağımsız değişkenler için isteğe bağlı parametrelere sahip olmayan bir aday için tercih gider. Bu aşırı yükleme çözünürlüğü içinde genel bir tercih daha az parametrelere sahip adayları için bir sonuç olur.

<a name="return"></a>

## <a name="return-values"></a>Döndürülen değerler

Yöntemler, çağırana bir değer döndürebilir. Dönüş türü (önce yöntem adını listelenen) değilse `void`, yöntem kullanarak değer döndürebilir `return` anahtar sözcüğü. With deyimi `return` anahtar sözcüğü bir değişken, sabit ya da dönüş türüyle eşleşen bir ifade tarafından izlenen, metodu çağırana değeri döndürecektir. Yöntemleriyle void olmayan dönüş türü kullanmak için gerekli `return` bir değer döndürmek için anahtar sözcüğü. `return` Anahtar sözcüğü de yöntemin yürütülmesini durdurur.

Dönüş türü ise `void`, `return` deyimi bir değer olmadan, yöntemin yürütülmesini durdurmak yine de kullanışlıdır. Olmadan `return` anahtar sözcüğü, yöntem durdurur kod bloğunun sonuna ulaştığında yürütülüyor.

Örneğin, bu iki yöntem kullanmak `return` anahtar sözcüğü, tamsayı döndüren için:

[!code-csharp[csSnippets.Methods#44](../../samples/snippets/csharp/concepts/methods/return44.cs#44)]

Yöntemi tarafından döndürülen bir değer kullanmak için yöntemi çağrılırken, aynı türde bir değer yeterli yöntemi çağrının kendisini her yerde kullanabilirsiniz. Ayrıca, dönüş değeri bir değişkene atayabilirsiniz. Örneğin, aşağıdaki iki kod örnekleri ve aynı hedefe ulaşmak:

[!code-csharp[csSnippets.Methods#45](../../samples/snippets/csharp/concepts/methods/return44.cs#45)]

[!code-csharp[csSnippets.Methods#46](../../samples/snippets/csharp/concepts/methods/return44.cs#46)]

Yerel değişken, bu durumda, kullanarak `result`depolamak için bir değer isteğe bağlıdır. Yöntemin tüm kapsam için bağımsız değişkenin özgün değeri depolamak gerekiyorsa gerekli olabilir veya kodun okunabilirliğini yardımcı olabilir.

Bazen, birden çok tek bir değer döndürmek için yönteminizi istersiniz. C# 7.0 ile başlayarak, kolayca kullanarak bunu yapabilirsiniz *tanımlama grubu türleri* ve *demet sabit*. Demet türü düzeninin öğelerin veri türlerini tanımlar. Demet sabit döndürülen kayıt düzeninin gerçek değerleri sağlayın. Aşağıdaki örnekte, `(string, string, string, int)` tarafından döndürülen dizi türünü tanımlayan `GetPersonalInfo` yöntemi. İfade `(per.FirstName, per.MiddleName, per.LastName, per.Age)` kayıt yöntemi birinci, ikinci ve son adı, yaşı, birlikte döndürür; sabitidir bir `PersonInfo` nesne.

```csharp
public (string, string, string, int) GetPersonalInfo(string id)
{
    PersonInfo per = PersonInfo.RetrieveInfoById(id);
    return (per.FirstName, per.MiddleName, per.LastName, per.Age);
}
```

Çağıranın sonra döndürülen kayıt düzeni aşağıdaki gibi kod ile kullanabilir:

```csharp
var person = GetPersonalInfo("111111111")
Console.WriteLine("{person.Item1} {person.Item3}: age = {person.Item4}");
```

Demet türü tanımı tanımlama grubu öğe adları da atanabilir. Aşağıdaki örnek, farklı bir sürümünü gösterir. `GetPersonalInfo` kullanan yöntemi adlı öğeleri:

```csharp
public (string FName, string MName, string LName, int Age) GetPersonalInfo(string id)
{
    PersonInfo per = PersonInfo.RetrieveInfoById(id);
    return (per.FirstName, per.MiddleName, per.LastName, per.Age);
}
```

Önceki çağrısı `GetPersonInfo` yöntemi daha sonra değiştirilebilir gibi:

```csharp
var person = GetPersonalInfo("111111111");
Console.WriteLine("{person.FName} {person.LName}: age = {person.Age}");
```

Bir yöntem bir dizi bağımsız değişken olarak geçirilir ve tek tek öğelerin değerini değiştirir, iyi stil veya değerlerin işlevsel akış için bunu tercih edebilirsiniz ancak dizi döndürmek yöntemin için ise gerekli değildir.  C# tüm başvuru türleri değeri geçirir ve bir dizi başvuru değeri dizi işaretçisi olduğundan budur. Aşağıdaki örnekte, içeriğini değiştirir `values` içinde yapılan bir dizi `DoubleValues` dizi için bir başvuruya sahip herhangi bir kod tarafından gözlemlenebilir bir yöntemdir.

[!code-csharp[csSnippets.Methods#101](../../samples/snippets/csharp/concepts/methods/returnarray1.cs#101)]

<a name="extension"></a>

## <a name="extension-methods"></a>Genişletme yöntemleri

Normalde, var olan bir türü için bir yöntem eklemek için iki yolu vardır:

- Bu tür için kaynak kodunu değiştirin. Elbette, türün kaynak kodu değil aitse bunu yapamaz. Ve yöntemini desteklemek için herhangi bir özel veri alanları eklerseniz, bu bir değişiklik olur.
- Yeni bir yöntem, türetilen bir sınıfta tanımlayın. Bir yöntem, yapılar ve sabit listeleri gibi diğer türleri için devralma kullanarak bu şekilde eklenemez. Ya da "bir korumalı sınıf için bir yöntem eklemek için" kullanılabilir.

Genişletme yöntemleri "bir yöntem var olan bir türe türü değiştirme ya da devralınmış bir türünün yeni yöntemi uygulama olmadan eklemenizi" sağlar. Genişletme yöntemi genişlettiği türü olarak aynı bütünleştirilmiş kodun bulunacağı de yok. Tanımlı bir tür üyesi değilmiş gibi uzantı metodu çağırma.

Daha fazla bilgi için [genişletme yöntemleri](programming-guide/classes-and-structs/extension-methods.md).

<a name="async"></a>

## <a name="async-methods"></a>Zaman uyumsuz yöntemler

Zaman uyumsuz özelliğini kullanarak, açık geri çağırmaları kullanarak veya kodunuzun birden çok yöntemlerde veya lambda ifadelerinde el ile bölme olmadan zaman uyumsuz yöntemler çağırabilirsiniz.

Bir yöntem ile işaretlerseniz [zaman uyumsuz](language-reference/keywords/async.md) kullanabileceğiniz değiştiricisi [await](language-reference/keywords/await.md) yönteminde işleci. Ulaştığında denetlemek bir `await` denetimini zaman uyumsuz yöntemin ifadede, döndürür imzalamasına tamamlanmamış olursa arayan ve ilerleme durumu ile metodu `await` awaited görevi tamamlanıncaya kadar anahtar sözcüğü askıya alınır. Görev tamamlandığında, yürütme yönteminde devam edebilir.

> [!NOTE]
> Henüz tamamlanmadı ilk beklenen nesne karşılaşır veya zaman uyumsuz yöntemin sonuna alır, zaman uyumsuz yöntemini çağırana döner hangisi önce gerçekleşirse.

Bir zaman uyumsuz yöntem dönüş türüne sahip olabilir <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task>, veya `void`. `void` Türü öncelikle olay işleyicilerini tanımlamak için kullanılan dönüş burada bir `void` dönüş türünün gerekli. Döndüren zaman uyumsuz bir yöntem `void` beklenemez, ve void döndüren bir yöntemi çağıran kişi, yöntemin oluşturduğu özel durumları yakalayamaz. C# 7.0 ile başlayarak, zaman uyumsuz bir yöntem olabilir [herhangi bir görev benzeri dönüş türü](./whats-new/csharp-7.md#generalized-async-return-types).

Aşağıdaki örnekte, `DelayAsync` tamsayı döndüren bir return deyimi içeren zaman uyumsuz bir yöntem olduğundan. Zaman uyumsuz bir yöntem olduğundan, dönüş türü, yöntem bildiriminden olmalıdır `Task<int>`. Dönüş türü olduğundan `Task<int>`, değerlendirmesi `await` ifadesinde `DoSomethingAsync` aşağıdaki gibi bir tamsayı üretir `int result = await delayTask` deyimi gösterilmektedir.

[!code-csharp[csSnippets.Methods#102](../../samples/snippets/csharp/concepts/methods/async1.cs#102)]

Herhangi bir zaman uyumsuz yöntem bildiremezsiniz [içinde](language-reference/keywords/in-parameter-modifier.md), [ref](language-reference/keywords/ref.md), veya [kullanıma](language-reference/keywords/out-parameter-modifier.md) parametreleri, ancak bu tür parametreleri olan yöntemleri çağırabilir.

 Zaman uyumsuz yöntemler hakkında daha fazla bilgi için bkz. [Async ve Await ile zaman uyumsuz programlama](async.md), [zaman uyumsuz programlarda akış kontrolü](programming-guide/concepts/async/control-flow-in-async-programs.md), ve [Async Return Types](programming-guide/concepts/async/async-return-types.md).

<a name="expr"></a>

## <a name="expression-bodied-members"></a>İfade gövdeli üyeler

Yalnızca hemen bir ifade sonucunu döndürür veya Yöntemin gövdesi tek bir deyimde olan yöntem tanımlarını yaygındır.  Kullanarak bu yöntemleri tanımlamak için bir söz dizimi kısayolu yok `=>`:

```csharp
public Point Move(int dx, int dy) => new Point(x + dx, y + dy);
public void Print() => Console.WriteLine(First + " " + Last);
// Works with operators, properties, and indexers too.
public static Complex operator +(Complex a, Complex b) => a.Add(b);
public string Name => First + " " + Last;
public Customer this[long id] => store.LookupCustomer(id);
```

Yöntem döndürüyorsa `void` veya zaman uyumsuz bir yöntem, yöntem gövdesini bir deyim ifadesi (aynı lambdalar gibi) olması gerekir.  Özellikler ve dizin oluşturucular için salt okunur olmalıdır ve kullanmanızı `get` erişimci anahtar sözcüğü.

<a name="iterators"></a>

## <a name="iterators"></a>Yineleyiciler

Bir yineleyici listesini veya bir dizi gibi bir koleksiyon üzerinde özel yineleme gerçekleştirir. Yineleyici [yield return](language-reference/keywords/yield.md) her öğeyi bir defada döndürmek için deyimi. Olduğunda bir `yield return` çağıran dizideki sonraki öğeye isteyebilmesi deyimine ulaşıldığında, geçerli konumu hatırlanır.

Dönüş türü bir yineleyicinin olabilir <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, veya <xref:System.Collections.Generic.IEnumerator%601>.

Daha fazla bilgi için [yineleyiciler](programming-guide/concepts/iterators.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Erişim Değiştiricileri](language-reference/keywords/access-modifiers.md)
- [Statik Sınıflar ve Statik Sınıf Üyeleri](programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
- [Devralma](programming-guide/classes-and-structs/inheritance.md)
- [Soyut ve Korumalı Sınıflar ve Sınıf Üyeleri](programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)
- [params](language-reference/keywords/params.md)
- [out](language-reference/keywords/out-parameter-modifier.md)
- [ref](language-reference/keywords/ref.md)
- [in](language-reference/keywords/in-parameter-modifier.md)
- [Parametreleri Geçirme](programming-guide/classes-and-structs/passing-parameters.md)
