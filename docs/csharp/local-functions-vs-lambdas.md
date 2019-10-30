---
title: Yerel işlevler ve lambda ifadeleri karşılaştırması
description: Yerel işlevlerin neden lambda ifadelerinden daha iyi bir seçim olabileceğini öğrenin.
ms.date: 06/27/2016
ms.technology: csharp-advanced-concepts
ms.assetid: 368d1752-3659-489a-97b4-f15d87e49ae3
ms.openlocfilehash: a644b6868a37b3d6231a514dc37030cae062785a
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73038807"
---
# <a name="local-functions-compared-to-lambda-expressions"></a>Yerel işlevler lambda ifadeleriyle karşılaştırılır

İlk bakışta, [yerel işlevler](programming-guide/classes-and-structs/local-functions.md) ve [lambda ifadeleri](./programming-guide/statements-expressions-operators/lambda-expressions.md) çok benzerdir. Birçok durumda, lambda ifadeleri ve yerel işlevler kullanma arasında seçim stili ve kişisel tercihlerden bağımsız olur. Ancak, dikkat etmeniz gereken bir veya diğerini kullanabileceğiniz gerçek farklılıklar vardır.

Bu, yerel işlev ve çarpınımı algoritmasının lambda ifadesi uygulamaları arasındaki farkları inceleyelim. Yerel bir işlev kullanan ilk sürüm:

[!code-csharp[LocalFunctionFactorial](../../samples/snippets/csharp/new-in-7/MathUtilities.cs#37_LocalFunctionFactorial "Recursive factorial using local function")]

Bu uygulamayı lambda ifadeleri kullanan bir sürümle karşıtlık:

[!code-csharp[26_LambdaFactorial](../../samples/snippets/csharp/new-in-7/MathUtilities.cs#38_LambdaFactorial "Recursive factorial using lambda expressions")]

Yerel işlevlerin adları vardır. Lambda ifadeleri `Func` veya `Action` türler olan değişkenlere atanan anonim yöntemlerdir. Yerel bir işlev bildirdiğinizde, bağımsız değişken türleri ve dönüş türü, işlev bildiriminin bir parçasıdır. Lambda ifadesinin gövdesi bir parçası olmak yerine, bağımsız değişken türleri ve dönüş türü, lambda ifadesinin değişken türü bildiriminin bir parçasıdır. Bu iki fark kodun daha net bir şekilde oluşmasına neden olabilir.

Yerel işlevler, lambda ifadelerinden kesin atama için farklı kurallara sahiptir. Bir yerel işlev bildirimine, kapsamdaki herhangi bir kod konumundan başvurulabilir. Bir lambda ifadesi, erişilebilmesi için bir temsilci değişkenine atanmalıdır (veya lambda ifadesine başvuran temsilci aracılığıyla çağrılabilir.) Lambda ifadesini kullanan sürümün lambda ifadesini bildirmelidir ve başlatması gerektiğini, `nthFactorial` tanımlamadan önce dikkat edin. Bu nedenle, atamadan önce `nthFactorial` başvurmak için derleme zamanı hatasına neden olur.
Bu farklılıklar özyinelemeli algoritmaların yerel işlevler kullanılarak oluşturulması daha kolay hale gelir. Kendisini çağıran bir yerel işlev tanımlayabilir ve tanımlayabilirsiniz. Lambda ifadeleri, aynı lambda ifadesine başvuran bir gövdeye yeniden atanabilmeleri için bildirilmelidir ve varsayılan bir değer atanmalıdır.

Belirli atama kuralları, yerel işlev veya lambda ifadesi tarafından yakalanan tüm değişkenleri de etkiler. Yerel işlev veya lambda ifadesi bir temsilciye dönüştürüldüğünde, her iki yerel işlev ve lambda ifadesi kuralı, yakalanan değişkenlerin herhangi bir noktaya kesinlikle atandığını talep edilir. Fark, lambda ifadelerinin bildirildiği zaman temsilcilere dönüştürülmesidir. Yerel işlevler yalnızca temsilci olarak kullanıldığında temsilcilere dönüştürülür. Yerel bir işlev bildirirseniz ve yalnızca bir yöntem gibi çağırarak buna başvurmanız durumunda, bir temsilciye dönüştürülmez. Bu kural, kapsayan kapsamındaki herhangi bir uygun konumda yerel bir işlev bildirmenize olanak sağlar. Herhangi bir dönüş deyiminden sonra, üst yöntemin sonunda yerel işlevleri bildirmek yaygın bir yöntemdir.

Üçüncü olarak derleyici, yerel işlevlerin kapsayan kapsamda kesin olarak yakalanan değişkenleri atamasını sağlayan statik analiz gerçekleştirebilir. Şu örneği göz önünde bulundurun:

```csharp
int M()
{
    int y;
    LocalFunction();
    return y;

    void LocalFunction() => y = 0;
}
```

Derleyici, çağrıldığında `LocalFunction` kesinlikle `y` atayıp atamayacağını tespit edebilir. `LocalFunction` `return` deyimden önce çağrıldığından `y`, `return` bildiriminde kesin olarak atanır.

Örnek analizine izin veren analiz, dördüncü farkı mümkün kıdır.
Yerel işlevler, kullanım amaçlarına bağlı olarak, lambda ifadeleri için her zaman gerekli olan yığın ayırmalara engel olabilir. Yerel bir işlev hiçbir şekilde temsilciye dönüştürülürse ve yerel işlev tarafından yakalanan değişkenlerden hiçbiri, başka Lambdalar veya temsilcilere dönüştürülen yerel işlevler tarafından yakalanmazsa, derleyici yığın ayırmalara engel olabilir. 

Bu zaman uyumsuz örneği göz önünde bulundurun:

[!code-csharp[TaskLambdaExample](../../samples/snippets/csharp/new-in-7/AsyncWork.cs#36_TaskLambdaExample "Task returning method with lambda expression")]

Bu lambda ifadesinin kapanışı `address`, `index` ve `name` değişkenlerini içerir. Yerel işlevler söz konusu olduğunda, kapanışı uygulayan nesne `struct` bir tür olabilir. Bu yapı türü yerel işleve başvuruya göre geçirilir. Uygulamadaki bu fark bir ayırmaya kaydedilir.

Lambda ifadeleri için gereken örnek oluşturma, zaman açısından kritik kod yollarındaki bir performans faktörü olabilecek fazladan bellek ayırmaları anlamına gelir.
Yerel işlevler bu ek yüke neden olmaz. Yukarıdaki örnekte, yerel işlevlerin sürümünde lambda ifadesi sürümünden daha az sayıda ayırma bulunur.

> [!NOTE]
> Bu yöntemin yerel işlev eşdeğeri, kapanış için bir sınıf de kullanır. Yerel işleve yönelik kapanışın `class` olarak uygulanıp uygulanmadığı veya bir `struct` uygulama ayrıntısı olup olmadığı. Bir lambda, her zaman bir `class`kullanacak şekilde, yerel bir işlev `struct` kullanabilir.

[!code-csharp[TaskLocalFunctionExample](../../samples/snippets/csharp/new-in-7/AsyncWork.cs#TaskExample "Task returning method with local function")]

Bu örnekte gösterilmeyen bir son avantaj, yerel işlevlerin yineleyiciler olarak uygulanabilmesinin yanı sıra bir değer dizisi oluşturmak için `yield return` sözdizimini kullanmaktır. Lambda ifadelerinde `yield return` ifadeye izin verilmez.

Yerel işlevler Lambda ifadelerinde gereksiz gibi görünse de, bu işlemler aslında farklı amaçlara hizmet eder ve farklı kullanımlar sağlar.
Yalnızca başka bir yöntemin bağlamından çağrılan bir işlev yazmak istediğinizde yerel işlevler bu durum için daha etkilidir.
