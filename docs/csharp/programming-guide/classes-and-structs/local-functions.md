---
title: Yerel işlevler-C# Programlama Kılavuzu
description: C# ' deki yerel işlevler, başka bir üyede iç içe yerleştirilmiş ve kendi kapsayıcı üyelerinden çağrılabilecek özel yöntemlerdir.
ms.date: 10/02/2020
helpviewer_keywords:
- local functions [C#]
ms.openlocfilehash: a91995757048c8c54253d7f4b923d5194f69bc7b
ms.sourcegitcommit: 4d45bda8cd9558ea8af4be591e3d5a29360c1ece
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/02/2020
ms.locfileid: "91654926"
---
# <a name="local-functions-c-programming-guide"></a>Yerel işlevler (C# Programlama Kılavuzu)

C# 7,0 ' den başlayarak, c# *Yerel Işlevleri*destekler. Yerel işlevler, başka bir üyede iç içe yerleştirilmiş bir türün özel yöntemleridir. Yalnızca kendi kapsayıcı üyelerinden çağrılabilir. Yerel işlevler içinde bildirilebilecek ve şuradan çağrılabilir:

- Yöntemler, özellikle Yineleyici yöntemleri ve zaman uyumsuz yöntemler
- Oluşturucular
- Özellik erişimcileri
- Olay erişimcileri
- Anonim Yöntemler
- Lambda ifadeleri
- Sonlandırıcılar
- Diğer yerel işlevler

Ancak, yerel işlevler ifade-Bodied üyesi içinde bildirilemez.

> [!NOTE]
> Bazı durumlarda, bir yerel işlev tarafından desteklenen işlevselliği uygulamak için bir lambda ifadesi kullanabilirsiniz. Bir karşılaştırma için bkz [. yerel işlevler ve lambda ifadeleri](#local-functions-vs-lambda-expressions).

Yerel işlevler, kodunuzun amacını açık hale getirir. Kodunuzu okuyan herkes, yöntemin kapsayan Yöntem dışında çağrılabilir olmadığını görebilir. Ekip projeleri için, başka bir geliştiricinin yöntemi doğrudan sınıf veya yapı içinde başka bir yerde çağırmak olanaksız hale getirir.

## <a name="local-function-syntax"></a>Yerel işlev sözdizimi

Yerel bir işlev, kapsayan bir üye içinde iç içe geçmiş bir yöntem olarak tanımlanır. Tanımı aşağıdaki sözdizimine sahiptir:

```csharp
<modifiers> <return-type> <method-name> <parameter-list>
```

Aşağıdaki değiştiricileri yerel bir işlevle kullanabilirsiniz:

- [`async`](../../language-reference/keywords/async.md)
- [`unsafe`](../../language-reference/keywords/unsafe.md)
- [`static`](../../language-reference/keywords/static.md) (C# 8,0 ve üzeri sürümlerde). Statik bir yerel işlev yerel değişkenler veya örnek durumu yakalayamaz.
- [`extern`](../../language-reference/keywords/extern.md) (C# 9,0 ve üzeri sürümlerde). Dış yerel işlev olmalıdır `static` .

Yöntem parametreleri de dahil olmak üzere, kapsayan üyede tanımlanan tüm yerel değişkenlere statik olmayan bir yerel işlevde erişilebilir.

Bir yöntem tanımının aksine, yerel bir işlev tanımı üye erişim değiştiricisini içeremez. Tüm yerel işlevler özel olduğundan, anahtar sözcüğü gibi bir erişim değiştiricisi de dahil olmak üzere, `private` "özel ' değiştiricisi Bu öğe için geçerli değil."

Ayrıca, öznitelikler yerel işleve veya parametrelerine ve parametre türüne uygulanamaz.

Aşağıdaki örnek adlı bir yerel işlevi tanımlar `AppendPathSeparator` `GetText` :

[!code-csharp[LocalFunctionExample](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions1.cs)]  

## <a name="local-functions-and-exceptions"></a>Yerel işlevler ve özel durumlar

Yerel işlevlerin yararlı özelliklerinden biri, özel durumların hemen yüzeyine izin verebilir. Yöntem yineleyiciler için, özel durumlar yalnızca döndürülen dizi numaralandırıldıktan sonra, yineleyici alındığında değil, ortaya çıkacak. Zaman uyumsuz metotlar için, bir zaman uyumsuz yöntemde oluşturulan özel durumlar, döndürülen görev beklendiğinde gözlemlenir.

Aşağıdaki örnek, `OddSequence` belirtilen bir Aralık arasındaki tek sayıları numaralandırır bir yöntemi tanımlar. Numaralandırıcı yöntemine 100 ' den büyük bir sayı geçirdiğinden `OddSequence` , yöntemi bir oluşturur <xref:System.ArgumentOutOfRangeException> . Örneğin çıkışının gösterdiği gibi, özel durum yalnızca sayıları tekrarladığı zaman, numaralandırıcıyı alırken değil, yüzeyleri.

[!code-csharp[LocalFunctionIterator1](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator1.cs)]

Bunun yerine, aşağıdaki örnekte gösterildiği gibi, bir yerel işlevden Yineleyici döndürerek, doğrulama gerçekleştirirken ve yineleyici almadan önce bir özel durum oluşturabilirsiniz.

[!code-csharp[LocalFunctionIterator2](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator2.cs)]

Yerel işlevler, zaman uyumsuz işlem dışındaki özel durumları işlemek için benzer bir şekilde kullanılabilir. Genellikle, zaman uyumsuz yöntemde oluşturulan özel durumlar, öğesinin iç özel durumlarını incelemenizi gerektirir <xref:System.AggregateException> . Yerel işlevler, kodunuzun hızlı bir şekilde başarısız olmasına olanak tanır ve özel durumun hem zaman uyumlu olarak hem de aynı şekilde gözlemlenip

Aşağıdaki örnek, belirtilen saniye sayısını duraklatmak için adlı zaman uyumsuz bir yöntem kullanır `GetMultipleAsync` ve bu sayıda saniyeden oluşan rastgele bir değer döndürür. En fazla gecikme 5 saniyedir; <xref:System.ArgumentOutOfRangeException> değer 5 ' ten büyükse bir sonuç elde edilir. Aşağıdaki örnekte gösterildiği gibi, yöntemine 6 değeri geçirildiğinde oluşturulan özel durum, `GetMultipleAsync` <xref:System.AggregateException> Yöntem yürütmeye başladıktan sonra bir öğesine kaydırılır `GetMultipleAsync` .

[!code-csharp[LocalFunctionAsync](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async1.cs)]

Yöntem yineleyicisi ile yaptığımız gibi, zaman uyumsuz metodu çağırmadan önce doğrulamayı gerçekleştirmek için bu örnekteki kodu yeniden düzenleyebilirsiniz. Aşağıdaki örnekteki Çıktının gösterdiği gibi, ' <xref:System.ArgumentOutOfRangeException> a sarmalanmaz <xref:System.AggregateException> .

[!code-csharp[LocalFunctionAsync](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async2.cs)]

## <a name="local-functions-vs-lambda-expressions"></a>Yerel işlevler ve lambda ifadeleri karşılaştırması

İlk bakışta, yerel işlevler ve [lambda ifadeleri](../../language-reference/operators/lambda-expressions.md) çok benzerdir. Birçok durumda, lambda ifadeleri ve yerel işlevler kullanma arasında seçim stili ve kişisel tercihlerden bağımsız olur. Ancak, dikkat etmeniz gereken bir veya diğerini kullanabileceğiniz gerçek farklılıklar vardır.

Bu, yerel işlev ve çarpınımı algoritmasının lambda ifadesi uygulamaları arasındaki farkları inceleyelim. Yerel bir işlev kullanan ilk sürüm:

[!code-csharp[LocalFunctionFactorial](../../../../samples/snippets/csharp/new-in-7/MathUtilities.cs#37_LocalFunctionFactorial "Recursive factorial using local function")]

Bu uygulamayı lambda ifadeleri kullanan bir sürümle karşıtlık:

[!code-csharp[26_LambdaFactorial](../../../../samples/snippets/csharp/new-in-7/MathUtilities.cs#38_LambdaFactorial "Recursive factorial using lambda expressions")]

Yerel işlevlerin adları vardır. Lambda ifadeleri, veya türündeki değişkenlere atanan anonim yöntemlerdir `Func` `Action` . Yerel bir işlev bildirdiğinizde, bağımsız değişken türleri ve dönüş türü, işlev bildiriminin bir parçasıdır. Lambda ifadesinin gövdesi bir parçası olmak yerine, bağımsız değişken türleri ve dönüş türü, lambda ifadesinin değişken türü bildiriminin bir parçasıdır. Bu iki fark kodun daha net bir şekilde oluşmasına neden olabilir.

Yerel işlevler, lambda ifadelerinden kesin atama için farklı kurallara sahiptir. Bir yerel işlev bildirimine, kapsamdaki herhangi bir kod konumundan başvurulabilir. Bir lambda ifadesi, erişilebilmesi için önce bir temsilci değişkenine atanmalıdır (veya lambda ifadesine başvuran temsilci aracılığıyla çağrılabilir). Lambda ifadesini kullanan sürümün, lambda ifadesini tanımlamadan önce bildirmelidir ve başlatması gerektiğini unutmayın `nthFactorial` . Bu nedenle, atamadan önce başvurmak için derleme zamanı hatasına neden `nthFactorial` olur. Bu farklılıklar özyinelemeli algoritmaların yerel işlevler kullanılarak oluşturulması daha kolay hale gelir. Kendisini çağıran bir yerel işlev tanımlayabilir ve tanımlayabilirsiniz. Lambda ifadeleri, aynı lambda ifadesine başvuran bir gövdeye yeniden atanabilmeleri için bildirilmelidir ve varsayılan bir değer atanmalıdır.

Belirli atama kuralları, yerel işlev veya lambda ifadesi tarafından yakalanan tüm değişkenleri de etkiler. Yerel işlev veya lambda ifadesi bir temsilciye dönüştürüldüğünde, her iki yerel işlev ve lambda ifadesi kuralı, yakalanan değişkenlerin herhangi bir noktaya kesinlikle atandığını talep edilir. Fark, lambda ifadelerinin bildirildiği zaman temsilcilere dönüştürülmesidir. Yerel işlevler yalnızca temsilci olarak kullanıldığında temsilcilere dönüştürülür. Yerel bir işlev bildirirseniz ve yalnızca bir yöntem gibi çağırarak buna başvurmanız durumunda, bir temsilciye dönüştürülmez. Bu kural, kapsayan kapsamındaki herhangi bir uygun konumda yerel bir işlev bildirmenize olanak sağlar. Herhangi bir dönüş deyiminden sonra, üst yöntemin sonunda yerel işlevleri bildirmek yaygın bir yöntemdir.

Üçüncü olarak derleyici, yerel işlevlerin kapsayan kapsamda kesin olarak yakalanan değişkenleri atamasını sağlayan statik analiz gerçekleştirebilir. Bu örneği ele alalım:

```csharp
int M()
{
    int y;
    LocalFunction();
    return y;

    void LocalFunction() => y = 0;
}
```

Derleyici, `LocalFunction` çağrıldığında kesinlikle atayıp atamayacağını tespit edebilir `y` . , `LocalFunction` Deyimden önce çağrıldığı için `return` , `y` ifadeye kesin olarak atanır `return` .

Örnek analizine izin veren analiz, dördüncü farkı mümkün kıdır. Yerel işlevler, kullanım amaçlarına bağlı olarak, lambda ifadeleri için her zaman gerekli olan yığın ayırmalara engel olabilir. Yerel bir işlev hiçbir şekilde temsilciye dönüştürülürse ve yerel işlev tarafından yakalanan değişkenlerden hiçbiri, başka Lambdalar veya temsilcilere dönüştürülen yerel işlevler tarafından yakalanmazsa, derleyici yığın ayırmalara engel olabilir.

Bu zaman uyumsuz örneği göz önünde bulundurun:

[!code-csharp[TaskLambdaExample](../../../../samples/snippets/csharp/new-in-7/AsyncWork.cs#36_TaskLambdaExample "Task returning method with lambda expression")]

Bu lambda ifadesinin kapanışı `address` , `index` ve `name` değişkenlerini içerir. Yerel işlevler söz konusu olduğunda, kapanışı uygulayan nesne bir `struct` tür olabilir. Bu yapı türü yerel işleve başvuruya göre geçirilir. Uygulamadaki bu fark bir ayırmaya kaydedilir.

Lambda ifadeleri için gereken örnek oluşturma, zaman açısından kritik kod yollarındaki bir performans faktörü olabilecek fazladan bellek ayırmaları anlamına gelir. Yerel işlevler bu ek yüke neden olmaz. Yukarıdaki örnekte, yerel işlevlerin sürümünde lambda ifadesi sürümünden daha az sayıda ayırma bulunur.

> [!NOTE]
> Bu yöntemin yerel işlev eşdeğeri, kapanış için bir sınıf de kullanır. Yerel bir işlev için Kapanışın bir veya olarak uygulanıp uygulanmadığı bir `class` `struct` uygulama ayrıntısı. Yerel bir işlev bir kullanabilir, `struct` ancak bir lambda her zaman bir kullanır `class` .

[!code-csharp[TaskLocalFunctionExample](../../../../samples/snippets/csharp/new-in-7/AsyncWork.cs#TaskExample "Task returning method with local function")]

Bu örnekte gösterilmeyen bir son avantaj, yerel işlevlerin yineleyiciler olarak uygulanabilmesinin yanı `yield return` sıra bir değer dizisi oluşturmak için söz dizimini kullanmaktır. `yield return`Lambda ifadelerinde ifadeye izin verilmez.

Yerel işlevler Lambda ifadelerinde gereksiz gibi görünse de, bu işlemler aslında farklı amaçlara hizmet eder ve farklı kullanımlar sağlar. Yalnızca başka bir yöntemin bağlamından çağrılan bir işlev yazmak istediğinizde yerel işlevler bu durum için daha etkilidir.

## <a name="see-also"></a>Ayrıca bkz.

- [Yöntemler](methods.md)
