---
title: Lambda ifadeleri ve yerel işlevler
description: Lambda ifadeleri daha iyi bir seçim yerel işlevler neden olabilecek bilgi edinin.
ms.date: 06/27/2016
ms.assetid: 368d1752-3659-489a-97b4-f15d87e49ae3
ms.openlocfilehash: 0dfd34c5637bb4b8ae64a66e1ca1164fddec2cd7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="local-functions-compared-to-lambda-expressions"></a>Lambda ifadeleri karşılaştırma yerel işlevler

İlk bakışta, [yerel işlevler](programming-guide/classes-and-structs/local-functions.md) ve [lambda ifadeleri](lambda-expressions.md) çok benzer. Çoğu durumda, lambda ifadeleri ve yerel işlevlerini kullanma arasında seçim, stil ve kişisel tercih bir konudur. Ancak, burada birini veya diğerini farkında olmanız gereken kullanabilirsiniz gerçek farklar vardır.

Lambda ifadesi uygulamaları Faktöriyel algoritmasının ve yerel işlevi arasındaki farkları inceleyelim. İlk yerel işlevini kullanarak sürüm:

[!code-csharp[LocalFunctionFactorial](../../samples/snippets/csharp/new-in-7/MathUtilities.cs#37_LocalFunctionFactorial "Recursive factorial using local function")]

Bu uygulama lambda ifadeleri kullanan bir sürüm ile karşılaştırın.

[!code-csharp[26_LambdaFactorial](../../samples/snippets/csharp/new-in-7/MathUtilities.cs#38_LambdaFactorial "Recursive factorial using lambda expressions")]

Yerel işlevler adlara sahip. Lambda ifadeleri değişkenler için atanan anonim yöntemlerdir `Func` veya `Action` türleri. Yerel bir işlev bildirirken bağımsız değişken türleri ve dönüş türü, işlev bildirimi parçasıdır. Lambda gövde bölümü yerine ifadesi, bağımsız değişken türleri ve dönüş türü, lambda ifadenin değişken türü bildirimi parçasıdır. Bu iki fark daha anlaşılır kod oluşturulmasına neden olabilir.

Yerel işlevler lambda ifadeleri daha kesin atamaya ilişkin farklı kuralları vardır. Yerel işlev bildirimi kapsamında olduğu herhangi bir kod konumdan başvurulabilir. Bunu erişileceği (veya lambda ifadesi başvuran delgate adlı önce.) bir lambda ifadesi bir temsilci değişkenine atanan gerekir Lambda ifadesi kullanarak sürüm bildirme gerekir ve lambda ifadesi başlatma Uyarısı `nthFactorial` kendisini tanımlayan önce. Bunu yapmazsanız sonuçlanıyor başvuran bir derleme zamanı hatası `nthFactorial` atayarak önce.
Bu farklılıklar, yinelemeli algoritmalar yerel işlevler kullanılarak oluşturmak kolaydır anlamına gelir. Bildirme ve kendi kendini çağıran yerel bir işlev tanımlayın. Lambda ifadeleri gerekir bildirilen ve aynı lambda ifadesi başvuruda bulunan bir gövde yeniden atandığında kullanılabilmesi için öncelikle bir varsayılan değer atanmış.

Kesin atama kurallarının yerel işlevi veya lamdba epression tarafından yakalanan tüm değişkenleri de etkiler. Yerel işlevler ve lambda ifadesi kuralları yerel işlevi veya lambda ifadesi bir temsilciye dönüştürüldüğünde yakalanan değişkenlerin kesinlikle bir noktada atanan talep. Bunlar bildirirken lambda ifadeleri temsilcileri dönüştürülür farktır. Yerel işlevler yalnızca bir temsilci olarak kullanıldığında temsilciler dönüştürülür. Yerel bir işlev bildirme ve yalnızca gibi bir yöntemini çağırarak başvuru, bir temsilci dönüştürülmez. Bu kural, yerel bir işlev kapsayan kapsamı uygun bir konumda bildirmek sağlar. Tüm return deyimlerinde sonra yerel işlevler üst yöntemi sonunda bildirmek için yaygın bir durumdur.

Üçüncü derleyici kesinlikle yakalanan değişkenleri çevreleyen kapsamdaki atamak yerel işlevler sağlayan statik çözümleme gerçekleştirebilirsiniz. Bu örneği göz önünde bulundurun:

```csharp
int M()
{
    int y;
    LocalFunction();
    return y;

    void LocalFunction() => y = 0;
}
```

Derleyici, belirleyebilirsiniz `LocalFunction` kesinlikle atar `y` çağrıldığında. Çünkü `LocalFunction` önce adlı `return` deyimi, `y` definitiely atanmıştır `return` deyimi.

Örnek analiz etkinleştirir analiz dördüncü fark sağlar.
Kullanımlarını bağlı olarak, her zaman lambda ifadeleri için gerekli olan yığın ayırmaları yerel işlevler önleyebilirsiniz. Yerel bir işlev hiçbir zaman bir temsilciye dönüştürülür ve yerel işlevi tarafından yakalanan değişkenleri hiçbiri diğer Lambda'lar veya temsilcileri dönüştürülür yerel işlevler tarafından yakalanır, derleyici yığın ayırmaları önleyebilirsiniz. 

Bu zaman uyumsuz örneği göz önünde bulundurun:

[!code-csharp[TaskLambdaExample](../../samples/snippets/csharp/new-in-7/AsyncWork.cs#36_TaskLambdaExample "Task returning method with lambda expression")]

Kapatılmak üzere bu lambda ifadesi içeriyor `address`, `index` ve `name` değişkenleri. Yerel işlevler söz konusu olduğunda, kapatma uygulayan nesnenin olabilir bir `struct` türü. Bu yapı türü, yerel işlev başvurusunu tarafından aktarılabilecek. Uygulamasında bu farkı bir ayırma işleminde kaydeder.

Lambda ifadeleri için gerekli örneklemesi performans faktörü zaman açısından kritik kod yollarda olabilir ek bellek ayırmaları anlamına gelir.
Yerel işlevler bu zahmetine değil. Yukarıdaki örnekte, yerel işlevler sürüm 2 daha az ayırmaları lambda ifadesi sürümden sahiptir.

> [!NOTE]
> Bu yöntem yerel işlevi denk bir sınıf Kapatılmak üzere de kullanır. Kapatılmak üzere yerel bir işlev olarak uygulanıp bir `class` veya `struct` bir uygulama ayrıntısı. Yerel bir işlev kullanabilir bir `struct` bir lambda her zaman kullanır ancak bir `class`.

[!code-csharp[TaskLocalFunctionExample](../../samples/snippets/csharp/new-in-7/AsyncWork.cs#29_TaskExample "Task returning method with local function")]

Bu örnekte gösterilmez son avantajlarından biri yerel işlevler kullanılarak yineleyiciler uygulanabilir `yield return` sözdizimi değerleri dizisi üretir. `yield return` Deyimi lambda ifadelerde izin verilmez.

Yerel işlevler lambda ifadeleri yedekli görünebilir, ancak bunlar aslında farklı amaçlara hizmet ve farklı kullanımlar sahip.
Yalnızca başka bir yöntem bağlamından adlı bir işlev yazdığınızda istediğinizde yerel işlevler söz konusu daha verimlidir.
