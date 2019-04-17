---
title: Lambda ifadeleri ve yerel işlevler
description: Yerel işlevler lambda ifadeleri daha iyi bir seçim neden olabiliyor öğrenin.
ms.date: 06/27/2016
ms.assetid: 368d1752-3659-489a-97b4-f15d87e49ae3
ms.openlocfilehash: 7577950314f8c57fba635db8b2bcd69e8d427dc3
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2019
ms.locfileid: "59611451"
---
# <a name="local-functions-compared-to-lambda-expressions"></a>Lambda ifadeleri karşılaştırma yerel işlevler

İlk bakışta [yerel işlevler](programming-guide/classes-and-structs/local-functions.md) ve [lambda ifadeleri](./programming-guide/statements-expressions-operators/lambda-expressions.md) çok benzer. Çoğu durumda, lambda ifadeleri ve yerel işlevleri kullanma arasında seçim, stil ve kişisel tercihinize bir konudur. Ancak, birini veya diğerini farkında olmanız gereken kullanabileceğiniz gerçek farklar vardır.

Yerel işlev ve lambda ifadesi uygulamaları Faktöriyel algoritmasının arasındaki farklar inceleyelim. İlk yerel bir işlevi kullanarak sürüm:

[!code-csharp[LocalFunctionFactorial](../../samples/snippets/csharp/new-in-7/MathUtilities.cs#37_LocalFunctionFactorial "Recursive factorial using local function")]

Bu uygulamayı lambda ifadelerini kullanan bir sürüm ile karşılaştırın.

[!code-csharp[26_LambdaFactorial](../../samples/snippets/csharp/new-in-7/MathUtilities.cs#38_LambdaFactorial "Recursive factorial using lambda expressions")]

Yerel işlevler adlarına sahip. Lambda ifadeleri olan değişkenlere eklendiklerinde anonim yöntemler olan `Func` veya `Action` türleri. Yerel bir işlev bildirdiğinizde, bağımsız değişken türleri ve dönüş türü, işlev bildirimi parçasıdır. Lambda gövdesi bir parçası olmak yerine ifade, bağımsız değişken türleri ve dönüş türü, lambda ifadesinin değişken türü bildirimi parçasıdır. Bu iki fark NET kod oluşturulmasına neden olabilir.

Yerel İşlevler, lambda ifadeleri daha kesin atama için farklı kuralları vardır. Yerel işlev bildirimi kapsam içinde olduğu herhangi bir kod konumdan başvurulabilir. Bir temsilci değişkenine bir lambda ifadesi bu erişileceği (veya lambda ifadesi başvuran temsilci adlı önce.) atanmalıdır Lambda ifadesi kullanarak sürüm bildirmeli ve lambda ifadesi başlatmak, bildirim `nthFactorial` kendisini tanımlayan önce. Bunu yapmazsanız sonuçlanıyor başvuran bir derleme zamanı hatası `nthFactorial` atayarak önce.
Bu farklılıklar, yinelemeli algoritmalar yerel işlevler kullanarak oluşturmak daha kolay anlamına gelir. Bildirme ve kendi kendini çağıran yerel bir fonksiyon tanımlayın. Lambda ifadeleri gerekir bildirilmiş ve aynı lambda ifadesi başvuran bir gövde yeniden atanan kullanılabilmesi için öncelikle bir varsayılan değer atanır.

Belirli atama onayına kuralları, yerel bir işlev veya lambda ifadesi tarafından yakalanan tüm değişkenleri de etkiler. Hem yerel işlevler hem de lambda ifadesi kuralları isteğe bağlı yerel işlev veya lambda ifadesi bir temsilciye dönüştürüldüğünde yakalanan tüm değişkenlere kesinlikle noktada atanır. Lambda ifadeleri, bildirildikleri temsilcileri dönüştürülür farktır. Yerel işlevler yalnızca temsilci olarak kullanıldığında temsilciler dönüştürülür. Yerel bir işlevi bildirmek ve gibi bir yöntem çağırarak yalnızca başvuru, bir temsilciye dönüştürülmez. Bu kural, kapsayan kapsamı uygun bir konumda yerel bir işlevi bildirmek sağlar. Yerel işlevler üst yönteminin sonunda tüm dönüş deyimleri sonra bildirmek için yaygındır.

Üçüncü olarak, derleyici kesinlikle kapsayan kapsam içinde yakalanan değişkenlere atamak yerel işlevler sağlayan statik analiz gerçekleştirebilirsiniz. Bu örneği göz önünde bulundurun:

```csharp
int M()
{
    int y;
    LocalFunction();
    return y;

    void LocalFunction() => y = 0;
}
```

Derleyici, belirleyebilirsiniz `LocalFunction` kesinlikle atar `y` çağrıldığında. Çünkü `LocalFunction` önce çağrılır `return` deyimi `y` kesinlikle atanmıştır `return` deyimi.

Örnek analysis sağlayan analiz dördüncü fark sağlar.
Kullanımları bağlı olarak, her zaman lambda ifadeleri için gerekli olan yığın ayırmaları yerel işlevler önleyebilirsiniz. Yerel bir işlev hiçbir zaman bir temsilciye dönüştürülmüş ve diğer lambdalar veya temsilciye dönüştürülmüş yerel işlevler tarafından yakalanan yerel işlev tarafından yakalanan değişkenler hiçbiri, derleyicinin yığın ayırmaları önleyebilirsiniz. 

Bu zaman uyumsuz örneği göz önünde bulundurun:

[!code-csharp[TaskLambdaExample](../../samples/snippets/csharp/new-in-7/AsyncWork.cs#36_TaskLambdaExample "Task returning method with lambda expression")]

Bu bir lambda ifadesi için kapatma içeren `address`, `index` ve `name` değişkenleri. Yerel işlevler söz konusu olduğunda, kapanış uygulayan nesnenin olabilir bir `struct` türü. Bu yapı türü, yerel bir işlev başvurusu tarafından geçirilir. Bu fark, uygulama üzerinde bir ayırma kaydeder.

Lambda ifadeleri için gerekli örnek oluşturma, zaman açısından kritik kod yolları bir performans faktör olabilecek ek bellek ayırmaları anlamına gelir.
Yerel işlevler bu yüküne tabi değildir. Yukarıdaki örnekte, 2, lambda ifadesi sürümden daha az ayırmaları yerel işlevler sürümüyle vardır.

> [!NOTE]
> Bu yöntem yerel işlev denk bir sınıf Kapatılmak üzere de kullanır. Bir yerel işlevin kabini olarak uygulanıp bir `class` veya `struct` bir uygulama ayrıntısı olduğunu. Yerel bir işlev kullanabilir bir `struct` bir lambda her zaman kullanır ancak bir `class`.

[!code-csharp[TaskLocalFunctionExample](../../samples/snippets/csharp/new-in-7/AsyncWork.cs#TaskExample "Task returning method with local function")]

Bu örnekte gösterilmiştir değil son avantajlarından biri yerel işlevler kullanarak yineleyiciler uygulanabilir `yield return` değerler üretmek için söz dizimi. `yield return` Deyimi lambda ifadelerine izin verilmez.

Yerel işlevler lambda ifadeleri için yedekli olarak görünebilir, ancak bunlar gerçekten farklı amaçlara hizmet eder ve sahip farklı kullanır.
Yalnızca başka bir yöntem bağlamından çağrılan bir işlev yazmak istediğiniz zaman yerel işlevler çalışması için daha verimlidir.
