---
title: Yerel işlevler - C# Programlama Kılavuzu
ms.date: 06/14/2017
helpviewer_keywords:
- local functions [C#]
ms.openlocfilehash: 200fbd097b7c71a1cd392d62622955528a80fd66
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102950"
---
# <a name="local-functions-c-programming-guide"></a>Yerel işlevler (C# Programlama Kılavuzu)

C# 7.0 ile başlayarak, C# *yerel işlevleri*destekler. Yerel işlevler, başka bir üyede iç içe olan bir türdeki özel yöntemlerdir. Yalnızca kendi üyelerinden çağrılabilirler. Yerel işlevler bildirilebilir ve şu andan itibaren çağrılabilir:

- Yöntemler, özellikle reeratör yöntemleri ve async yöntemleri
- Oluşturucular
- Özellik erişime girenler
- Etkinlik erişime girenler
- Anonim yöntemler
- Lambda ifadeleri
- Sonlandırıcılar
- Diğer yerel işlevler

Ancak, yerel işlevler ifade gövdeli bir üye içinde bildirilemez.

> [!NOTE]
> Bazı durumlarda, yerel bir işlev tarafından da desteklenen işlevselliği uygulamak için bir lambda ifadesi kullanabilirsiniz. Karşılaştırma için, [yerel işlevler vs lambda ifadeler](#local-functions-vs-lambda-expressions)bakın.

Yerel işlevler, kodunuzu açıkça ortaya kovar. Kodunuzu okuyan herkes, içeren yöntem dışında yöntemin çağrılabilir olmadığını görebilir. Takım projeleri için, başka bir geliştiricinin yöntemi yanlışlıkla sınıfın veya yapının başka bir yerinden yanlışlıkla aramasını da imkansız hale getirir.

## <a name="local-function-syntax"></a>Yerel işlev sözdizimi

Yerel bir işlev, iç içe bir üyenin içinde iç içe bir yöntem olarak tanımlanır. Tanımıaşağıdaki sözdizimine sahiptir:

```csharp
<modifiers: async | unsafe> <return-type> <method-name> <parameter-list>
```

Yerel işlevler [async](../../language-reference/keywords/async.md) ve [güvensiz](../../language-reference/keywords/unsafe.md) değiştiriciler kullanabilirsiniz.

Yöntem parametreleri de dahil olmak üzere, ilgili üyede tanımlanan tüm yerel değişkenlere yerel işlevde erişilebilir olduğunu unutmayın.

Yöntem tanımının aksine, yerel işlev tanımı üye erişim değiştiriciyi içeremez. `private` Anahtar kelime gibi bir erişim değiştirici de dahil olmak üzere tüm yerel işlevler özel olduğundan, cs0106 derleyici hatası oluşturur, "Değiştirici 'özel' bu öğe için geçerli değildir."

> [!NOTE]
> C# 8.0'dan önce yerel `static` işlevler değiştiriciyi içeremez. `static` Anahtar kelime de dahil olmak üzere derleyici hatası CS0106 oluşturur, "Değiştirici 'statik' bu öğe için geçerli değildir."

Ayrıca, öznitelikler yerel işleve veya parametrelerine ve tür parametrelerine uygulanamaz.

Aşağıdaki örnek, adlı bir `AppendPathSeparator` yönteme özel olan `GetText`yerel bir işlev tanımlar:

[!code-csharp[LocalFunctionExample](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions1.cs)]  

## <a name="local-functions-and-exceptions"></a>Yerel işlevler ve özel durumlar

Yerel işlevlerin yararlı özelliklerinden biri, özel durumların hemen yüzeye çıkmasına izin verebilmeleridir. Yöntem yineleyicileri için, özel durumlar yalnızca döndürülen sıra numaralandırıldığında su yüzüne çıkar, yineleyici alındığında değil. Async yöntemleri için, döndürülen görev bekleniyor zaman bir async yöntemi atılan tüm özel durumlar gözlenir.

Aşağıdaki örnek, belirli `OddSequence` bir aralık arasında tek sayılar numaralandırmak bir yöntem tanımlar. Numaralandırma yöntemine 100'den `OddSequence` büyük bir sayı geçtiği için, yöntem <xref:System.ArgumentOutOfRangeException>bir . Örnekteki çıktının gösterdiği gibi, özel durum yalnızca sayıyı kaydettiğinizde değil, sayıları yinelediğinizde ortaya çıkar.

[!code-csharp[LocalFunctionIterator1](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator1.cs)]

Bunun yerine, doğrulama gerçekleştirirken ve aşağıdaki örnekte görüldüğü gibi, yineleyiciyi yerel bir işlevden döndürerek yineleyiciyi almadan önce bir özel durum atabilirsiniz.

[!code-csharp[LocalFunctionIterator2](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator2.cs)]

Yerel işlevler, asynchronous işleminin dışındaki özel durumları işlemek için benzer bir şekilde kullanılabilir. Normalde, async yönteminde atılan özel durumlar, bir <xref:System.AggregateException>. Yerel işlevler, kodunuzun hızlı bir şekilde başarısız olmasını ve özel durumlarınızın hem atılmasına hem de eşzamanlı olarak gözlenmesine izin verir.

Aşağıdaki örnek, belirli bir saniye `GetMultipleAsync` sayısı için duraklatmak ve bu saniye sayısının rasgele bir katını döndürecek bir değer döndürmek için adlandırılmış bir eşzamanlı yöntem kullanır. Maksimum gecikme 5 saniyedir; değeri <xref:System.ArgumentOutOfRangeException> 5'ten büyükse sonuç verir. Aşağıdaki örnekte de görüldüğü gibi, `GetMultipleAsync` <xref:System.AggregateException> `GetMultipleAsync` yönteme 6 değeri geçirildiğinde atılan özel durum, yöntem yürütmeye başladıktan sonra bir şekilde sarılır.

[!code-csharp[LocalFunctionAsync](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async1.cs)]

Yöntem yineleyicide yaptığımız gibi, asynchronous yöntemini aramadan önce doğrulamayı gerçekleştirmek için bu örnekteki kodu yeniden değerlendirebiliriz. Aşağıdaki örnekteki çıktının gösterdiği <xref:System.ArgumentOutOfRangeException> gibi, bir <xref:System.AggregateException>.

[!code-csharp[LocalFunctionAsync](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async2.cs)]

## <a name="local-functions-vs-lambda-expressions"></a>Yerel işlevler vs lambda ifadeler

İlk bakışta, yerel [fonksiyonlar](../statements-expressions-operators/lambda-expressions.md) ve lambda ifadeler çok benzer. Birçok durumda, lambda ifadeleri ve yerel işlevleri kullanarak arasındaki seçim tarzı ve kişisel tercih meselesidir. Ancak, farkında olması gereken birini veya diğerini kullanabileceğiniz gerçek farklılıklar vardır.

Faktöriyel algoritmanın yerel fonksiyon ve lambda ifade uygulamaları arasındaki farkları inceleyelim. Önce yerel bir işlev kullanarak sürümü:

[!code-csharp[LocalFunctionFactorial](../../../../samples/snippets/csharp/new-in-7/MathUtilities.cs#37_LocalFunctionFactorial "Recursive factorial using local function")]

Bu uygulamanın lambda ifadelerini kullanan bir sürümle karşılatılması:

[!code-csharp[26_LambdaFactorial](../../../../samples/snippets/csharp/new-in-7/MathUtilities.cs#38_LambdaFactorial "Recursive factorial using lambda expressions")]

Yerel işlevlerin adları vardır. Lambda ifadeleri, türdeki değişkenlere atanan anonim `Func` yöntemlerdir. `Action` Yerel bir işlev bildirdiğinizde, bağımsız değişken türleri ve iade türü işlev bildiriminin bir parçasıdır. Lambda ifadesinin gövdesinin bir parçası olmak yerine, argüman türleri ve dönüş türü lambda ifadesinin değişken türü deyiminin bir parçasıdır. Bu iki fark daha net kod neden olabilir.

Yerel işlevlerin kesin atama için lambda ifadelerinden farklı kuralları vardır. Yerel işlev bildirimi, kapsamda olduğu herhangi bir kod konumundan başvurulabilir. Bir lambda ifadesine erişilebilmek için önce bir temsilci değişkenine atanmalıdır (veya lambda ifadesine başvuran temsilci aracılığıyla çağrılanmalıdır). Lambda ifadesini kullanan sürümü tanımlamadan önce lambda ifadesini `nthFactorial` beyan etmesi ve başlatması gerektiğine dikkat edin. Bunu yapmamak, atamadan önce başvurmak `nthFactorial` için bir derleme zaman hatasına neden olur. Bu farklar, özyinelemeli algoritmaların yerel işlevleri kullanarak oluşturulmasının daha kolay olduğu anlamına gelir. Kendisini çağıran yerel bir işlev bildirebilir ve tanımlayabilirsiniz. Lambda ifadeleri beyan edilmeli ve aynı lambda ifadesine başvuran bir gövdeye yeniden atanabilmeleri için varsayılan bir değer atanmalıdır.

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

Örnek çözümlemesini sağlayan çözümleme dördüncü farkı sağlar. Kullanımlarına bağlı olarak, yerel işlevler lambda ifadeleri için her zaman gerekli olan yığın ayırmalarından kaçınabilir. Yerel bir işlev hiçbir zaman temsilciye dönüştürülmezse ve yerel işlev tarafından yakalanan değişkenlerin hiçbiri diğer lambda'lar veya temsilciye dönüştürülen yerel işlevler tarafından yakalanırsa, derleyici yığın ayırmalarından kaçınabilir.

Bu async örneğini göz önünde bulundurun:

[!code-csharp[TaskLambdaExample](../../../../samples/snippets/csharp/new-in-7/AsyncWork.cs#36_TaskLambdaExample "Task returning method with lambda expression")]

Bu lambda ifadesinin `address`kapanışı `index` `name` , ve değişkenleri içerir. Yerel işlevler söz konusu olduğunda, kapatmayı uygulayan `struct` nesne bir tür olabilir. Bu yapı türü yerel işleve atıfta bulunularak geçirilir. Uygulamadaki bu fark bir ayırmada tasarruf sağlar.

Lambda ifadeleri için gerekli anlık algılama, zaman açısından kritik kod yollarında bir performans faktörü olabilecek ekstra bellek ayırmaları anlamına gelir. Yerel işlevler bu ek yükü tabi değildir. Yukarıdaki örnekte, yerel işlevler sürümü lambda ifade sürümünden 2 daha az ayırmaya sahiptir.

> [!NOTE]
> Bu yöntemin yerel işlev eşdeğeri de kapatma için bir sınıf kullanır. Yerel bir işlevin kapatılmasının a `class` veya `struct` a olarak uygulanıp uygulanmadığı bir uygulama ayrıntısýr. Yerel bir `struct` fonksiyon bir lambda her zaman `class`bir .

[!code-csharp[TaskLocalFunctionExample](../../../../samples/snippets/csharp/new-in-7/AsyncWork.cs#TaskExample "Task returning method with local function")]

Bu örnekte gösterilmemiş son bir avantaj, yerel işlevlerin bir değer `yield return` dizisi oluşturmak için sözdizimini kullanarak yineleyici olarak uygulanabiliyor olmasıdır. Lambda `yield return` ifadelerinde ifadeye izin verilmez.

Yerel işlevler lambda ifadeleri için gereksiz görünse de, aslında farklı amaçlara hizmet ve farklı kullanımları vardır. Yerel işlevler, yalnızca başka bir yöntemin bağlamından çağrılan bir işlev yazmak istediğinizde, servis talebi için daha verimlidir.

## <a name="see-also"></a>Ayrıca bkz.

- [Yöntemler](methods.md)
