---
title: Yerel işlevler vs lambda ifadeler
description: Yerel işlevlerin neden lambda ifadelerinden daha iyi bir seçim olabileceğini öğrenin.
ms.date: 06/27/2016
ms.technology: csharp-advanced-concepts
ms.assetid: 368d1752-3659-489a-97b4-f15d87e49ae3
ms.openlocfilehash: 13cc3fe47bbcd6a465347a6c991b2006586c78fa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173347"
---
# <a name="local-functions-compared-to-lambda-expressions"></a>Lambda ifadeleri ile karşılaştırıldığında yerel fonksiyonlar

İlk bakışta, [yerel fonksiyonlar](programming-guide/classes-and-structs/local-functions.md) ve [lambda ifadeler](./programming-guide/statements-expressions-operators/lambda-expressions.md) çok benzer. Birçok durumda, lambda ifadeleri ve yerel işlevleri kullanarak arasındaki seçim tarzı ve kişisel tercih meselesidir. Ancak, farkında olması gereken birini veya diğerini kullanabileceğiniz gerçek farklılıklar vardır.

Faktöriyel algoritmanın yerel fonksiyon ve lambda ifade uygulamaları arasındaki farkları inceleyelim. Önce yerel bir işlev kullanarak sürümü:

[!code-csharp[LocalFunctionFactorial](../../samples/snippets/csharp/new-in-7/MathUtilities.cs#37_LocalFunctionFactorial "Recursive factorial using local function")]

Bu uygulamanın lambda ifadelerini kullanan bir sürümle karşılatılması:

[!code-csharp[26_LambdaFactorial](../../samples/snippets/csharp/new-in-7/MathUtilities.cs#38_LambdaFactorial "Recursive factorial using lambda expressions")]

Yerel işlevlerin adları vardır. Lambda ifadeleri, türdeki değişkenlere atanan anonim `Func` yöntemlerdir. `Action` Yerel bir işlev bildirdiğinizde, bağımsız değişken türleri ve iade türü işlev bildiriminin bir parçasıdır. Lambda ifadesinin gövdesinin bir parçası olmak yerine, argüman türleri ve dönüş türü lambda ifadesinin değişken türü deyiminin bir parçasıdır. Bu iki fark daha net kod neden olabilir.

Yerel işlevlerin kesin atama için lambda ifadelerinden farklı kuralları vardır. Yerel işlev bildirimi, kapsamda olduğu herhangi bir kod konumundan başvurulabilir. Bir lambda ifadesine erişilebilmek için bir temsilci değişkenine atanmalıdır (veya lambda ifadesine başvuran temsilci aracılığıyla çağrılanmalıdır.) Lambda ifadesini kullanan sürümün lambda ifadesini tanımlamadan `nthFactorial` önce beyan etmesi ve başlatması gerektiğine dikkat edin. Bunu yapmamak, atamadan önce başvurmak `nthFactorial` için bir derleme zaman hatasına neden olur.
Bu farklar, özyinelemeli algoritmaların yerel işlevleri kullanarak oluşturulmasının daha kolay olduğu anlamına gelir. Kendisini çağıran yerel bir işlev bildirebilir ve tanımlayabilirsiniz. Lambda ifadeleri beyan edilmeli ve aynı lambda ifadesine başvuran bir gövdeye yeniden atanabilmeleri için varsayılan bir değer atanmalıdır.

Kesin atama kuralları, yerel işlev veya lambda ifadesi tarafından yakalanan değişkenleri de etkiler. Hem yerel işlevler hem de lambda ifade kuralları, yakalanan değişkenlerin, yerel işlevin veya lambda ifadesinin bir temsilciye dönüştürüldüğü noktada kesinlikle atanmasını ister. Aradaki fark, lambda ifadeleri beyan edildiğinde delegelere dönüştürülür. Yerel işlevler yalnızca temsilci olarak kullanıldığında temsilciye dönüştürülür. Yerel bir işlev bildirir ve yalnızca bir yöntem gibi çağırarak başvurursanız, bu işlev bir temsilciye dönüştürülmez. Bu kural, yerel bir işlevi ekkapsamına giren herhangi bir uygun konumda bildirmenize olanak tanır. İade bildirimlerinden sonra, ana yöntemin sonunda yerel işlevleri bildirmek yaygındır.

Üçüncü olarak, derleyici, yerel işlevlerin yakalanan değişkenleri kesinlikle çevreleyen kapsamda atamasını sağlayan statik çözümleme gerçekleştirebilir. Bu örneği göz önünde bulundurun:

```csharp
int M()
{
    int y;
    LocalFunction();
    return y;

    void LocalFunction() => y = 0;
}
```

Derleyici çağrıldığında `LocalFunction` kesinlikle `y` atadığını belirleyebilir. Çünkü `LocalFunction` ifadeden `return` önce `y` çağrılır, `return` kesinlikle deyimde atanır.

Örnek çözümlemesini sağlayan çözümleme dördüncü farkı sağlar.
Kullanımlarına bağlı olarak, yerel işlevler lambda ifadeleri için her zaman gerekli olan yığın ayırmalarından kaçınabilir. Yerel bir işlev hiçbir zaman temsilciye dönüştürülmezse ve yerel işlev tarafından yakalanan değişkenlerin hiçbiri diğer lambda'lar veya temsilciye dönüştürülen yerel işlevler tarafından yakalanırsa, derleyici yığın ayırmalarından kaçınabilir.

Bu async örneğini göz önünde bulundurun:

[!code-csharp[TaskLambdaExample](../../samples/snippets/csharp/new-in-7/AsyncWork.cs#36_TaskLambdaExample "Task returning method with lambda expression")]

Bu lambda ifadesinin `address`kapanışı `index` `name` , ve değişkenleri içerir. Yerel işlevler söz konusu olduğunda, kapatmayı uygulayan `struct` nesne bir tür olabilir. Bu yapı türü yerel işleve atıfta bulunularak geçirilir. Uygulamadaki bu fark bir ayırmada tasarruf sağlar.

Lambda ifadeleri için gerekli anlık algılama, zaman açısından kritik kod yollarında bir performans faktörü olabilecek ekstra bellek ayırmaları anlamına gelir.
Yerel işlevler bu ek yükü tabi değildir. Yukarıdaki örnekte, yerel işlevler sürümü lambda ifade sürümünden 2 daha az ayırmaya sahiptir.

> [!NOTE]
> Bu yöntemin yerel işlev eşdeğeri de kapatma için bir sınıf kullanır. Yerel bir işlevin kapatılmasının a `class` veya `struct` a olarak uygulanıp uygulanmadığı bir uygulama ayrıntısýr. Yerel bir `struct` fonksiyon bir lambda her zaman `class`bir .

[!code-csharp[TaskLocalFunctionExample](../../samples/snippets/csharp/new-in-7/AsyncWork.cs#TaskExample "Task returning method with local function")]

Bu örnekte gösterilmemiş son bir avantaj, yerel işlevlerin bir değer `yield return` dizisi oluşturmak için sözdizimini kullanarak yineleyici olarak uygulanabiliyor olmasıdır. Lambda `yield return` ifadelerinde ifadeye izin verilmez.

Yerel işlevler lambda ifadeleri için gereksiz görünse de, aslında farklı amaçlara hizmet ve farklı kullanımları vardır.
Yerel işlevler, yalnızca başka bir yöntemin bağlamından çağrılan bir işlev yazmak istediğinizde, servis talebi için daha verimlidir.
