---
title: İfade ağaçlarını yürütme
description: Yürütülebilir Ara dil (IL) talimatları dönüştürerek ifade ağaçlarını yürütme hakkında bilgi edinin.
ms.date: 06/20/2016
ms.assetid: 109e0ac5-2a9c-48b4-ac68-9b6219cdbccf
ms.openlocfilehash: f6dca5a3965924e8eb6e1c04fe7ffc3c78c7df93
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57201852"
---
# <a name="executing-expression-trees"></a>İfade ağaçlarını yürütme

[Önceki--İfade ağaçlarını destekleyen çerçeve türleri](expression-classes.md)

Bir *ifade ağacı* bazı kod temsil eden bir veri yapısıdır.
Derlenmiş ve yürütülebilir kodu değil. Bir ifade ağacı tarafından temsil edilen .NET kodu çalıştırmak istiyorsanız, bunu yürütülebilir IL yönergelerinden dönüştürmeniz gerekir.

## <a name="lambda-expressions-to-functions"></a>Lambda ifadeleri işlevleri

Tüm LambdaExpression veya yürütülebilir IL LambdaExpression türetilmiş herhangi bir tür dönüştürme yapabilirsiniz. Diğer ifade türleri, doğrudan koda dönüştürülemez. Bu kısıtlama, uygulamada çok az etkisi yoktur. Lambda ifadeleri, yalnızca yürütülebilir Ara dil (IL) dönüştürerek yürütmek istediğiniz ifadeleri türleridir. (Doğrudan çalıştırmak bunun ne anlama düşündüğünüz bir `ConstantExpression`. Bu faydalı bir şey anlamına gelir?) Olan herhangi bir ifade ağacı bir `LambdaExpression`, veya türetilmiş bir tür `LambdaExpression` için IL dönüştürülebilir.
İfade türü `Expression<TDelegate>` .NET Core kitaplıklarında yalnızca somut bir örnektir. Bu, tüm temsilci türüyle eşleyen bir ifade temsil etmek için kullanılır. Bu tür bir temsilci türüne eşlediğinden, .NET ifade inceleyin ve lambda ifadesinin imzayla eşleşen uygun bir temsilci için IL oluşturur. 

Çoğu durumda, bu ifade, karşılık gelen temsilci arasında basit bir eşleme oluşturur. Örneğin, tarafından temsil edilen bir ifade ağacı `Expression<Func<int>>` türden bir temsilciye dönüştürülmüş `Func<int>`. Herhangi bir dönüş türü ve bağımsız değişken listesi ile bir lambda ifadesi için yürütülebilir kodu bu lambda ifadesi tarafından temsil edilen hedef türü bir temsilci türü vardır.

`LambdaExpression` Türünü içeren `Compile` ve `CompileToMethod` yürütülebilir kodu bir ifade ağacı dönüştürmek için kullanacağınız üyeleri. `Compile` Yöntemi, bir temsilci oluşturur. `CompileToMethod` Yöntemi güncelleştirmeleri bir `MethodBuilder` derlenen Çıkışta ifade ağacı temsil eden IL nesne. Unutmayın `CompileToMethod` yalnızca tam masaüstü Framework, .NET Core de kullanılabilir.

İsteğe bağlı olarak, sağlayabilirsiniz bir `DebugInfoGenerator` oluşturulan temsilci nesne için hata ayıklama bilgisi sembol alırsınız. İfade ağacı bir temsilci nesnesine dönüştürmek ve oluşturulan temsilci tam hata ayıklama bilgilerini sağlar.

Bir ifade aşağıdaki kodu kullanarak bir temsilciye dönüştürmeniz:

```csharp
Expression<Func<int>> add = () => 1 + 2;
var func = add.Compile(); // Create Delegate
var answer = func(); // Invoke Delegate
Console.WriteLine(answer);
```

Bu ifade türünde temsilci türüne dayalı olduğunu dikkat edin. Temsilci nesne türü kesin belirlenmiş bir şekilde kullanmak istiyorsanız, dönüş türü ve bağımsız değişken listesi bilmeniz gerekir. `LambdaExpression.Compile()` Yöntemi döndürür `Delegate` türü. Bağımsız değişken listesini kontrol edin veya dönüş türü herhangi bir derleme zamanı aracı için doğru temsilci türüne dönüştürme gerekecektir.

## <a name="execution-and-lifetimes"></a>Yürütme ve yaşam süresi yok

Temsilci çağrıldığında, oluşturulan harekete geçirerek siz kodu yürütürken `LambdaExpression.Compile()`. Bunu yeri görebilirsiniz `add.Compile()` temsilci döndürür. Çağırarak bu temsilci çağırma `func()` kodu yürütür.

Bu temsilci kodda bir ifade ağacı temsil eder. Bu temsilci tanıtıcısını korumak ve daha sonra çağırma. İfade ağacı her zaman temsil ettiği kod yürütmek istediğiniz derleme gerek yoktur. (İfade ağaçları sabittir ve daha sonra aynı ifade ağacı derleme, aynı kodu yürüten bir temsilci oluşturur unutmayın.)

Ben gereksiz derleme çağrıları önleyerek performansı artırmak için daha karmaşık bir önbelleğe alma mekanizmasını oluşturulmaya çalışılırken karşı dikkat. Bunlar aynı algoritmayı temsil ediyorsa belirlemek için iki rastgele ifade ağaçları karşılaştırma ayrıca zaman yürütmek için alabilir. İşlem süresi, ek çağrıları kaydederken, büyük olasılıkla bulabilirsiniz `LambdaExpression.Compile()` birden fazla ifade ağaçları neden aynı yürütülebilir kodu tanımlayan iki farklı kod yürütme zamanına göre tüketilir.

## <a name="caveats"></a>Uyarılar

Bir lambda ifadesi, bir temsilci derleme ve bu temsilciyi çağrılırken bir ifade ağacı ile gerçekleştirebileceğiniz en basit işlemler biridir. Ancak, basit işlemle bile bu farkında olması gereken uyarılar vardır. 

Lambda ifadeleri, ifade başvurulmayan yerel değişkenlerin üzerine kapanışlar oluşturun. Temsilci bir parçası olan tüm değişkenler çağırdığınız konumda kullanılabilir olduğunu garanti gerekir `Compile`, ve sonuç olarak oluşan temsilci yürüttüğünüzde.

Genel olarak, derleyici bu doğru olduğundan emin olmanızı sağlar. Ancak, ifadeniz uygulayan bir değişkenine erişiyorsa `IDisposable`, ifade ağacına tarafından hala açık tutulduğu sürece kodunuzun nesnesini atmak mümkündür.

Örneğin, bu kod düzgün, çünkü çalışır `int` uygulamıyor `IDisposable`:

```csharp
private static Func<int, int> CreateBoundFunc()
{
    var constant = 5; // constant is captured by the expression tree
    Expression<Func<int, int>> expression = (b) => constant + b;
    var rVal = expression.Compile();
    return rVal;
}
```

Temsilci bir başvuru yerel değişkene yakalandı `constant`.
İşlev tarafından döndürülen daha sonra istediğiniz zaman bu değişken erişilir `CreateBoundFunc` yürütür.

Ancak, bu (Bunun yerine contrived) uygulayan sınıf göz önünde bulundurun `IDisposable`:

```csharp
public class Resource : IDisposable
{
    private bool isDisposed = false;
    public int Argument
    {
        get
        {
            if (!isDisposed)
                return 5;
            else throw new ObjectDisposedException("Resource");
        }
    }

    public void Dispose()
    {
        isDisposed = true;
    }
}
```

Bir ifadede aşağıda gösterildiği gibi kullanırsanız, elde edecekleriniz bir `ObjectDisposedException` tarafından başvurulan kodu yürüttüğünüzde `Resource.Argument` özelliği:

```csharp
private static Func<int, int> CreateBoundResource()
{
    using (var constant = new Resource()) // constant is captured by the expression tree
    {
        Expression<Func<int, int>> expression = (b) => constant.Argument + b;
        var rVal = expression.Compile();
        return rVal;
    }
}
```

Bu yöntemin döndürdüğü temsilci üzerinden kapattı `constant` , atıldı nesnesidir. (Olarak bildirildiğinden, atılmış olan bir `using` deyimi.) 

Bu yöntemin döndürdüğü temsilci yürüttüğünüzde, şimdi gerekir bir `ObjectDisposedException` yürütme noktasında oluşturulur.

Bir derleme zamanı yapısı temsil eden bir çalışma zamanı hatası için ilginç görünüyor, ancak bu ifade ağaçları ile çalıştığımız biz geçilmesidir dünya.

Bunu önlemek için genel rehberlik sunmak zor, bu nedenle bu sorunun permütasyon çok fazla vardır. İfadeleri tanımlarken yerel değişkenlere erişme hakkında dikkatli olun ve durumunda geçerli nesneye erişme hakkında dikkatli olun (tarafından temsil edilen `this`) ne zaman bir ifade ağacı oluşturma döndürülen bir genel API tarafından.

İfadeniz kodda yöntemleri veya özellikleri diğer derlemelerdeki başvurabilir. Bu derleme ne zaman ifade tanımlanır ve ne zaman derlenir ve sonuç olarak oluşan temsilci zaman çağrılır erişilebilir olması gerekir. İle karşılanması bir `ReferencedAssemblyNotFoundException` durumlarda burada da mevcut değil.

## <a name="summary"></a>Özet

Lambda ifadeleri temsil eden ifade ağaçları yürütebilirsiniz temsilci oluşturmak için derlenebilir. Bu, bir ifade ağacı tarafından temsil edilen kod yürütmek için bir mekanizma sağlar.

İfade ağacı, oluşturduğunuz belirli yapısı için yürütmek kodu temsil eder. İfade oluşturduğunuz ortamı, derleme ve kod yürütme ortamı eşleşmesi şartıyla, her şeyin beklendiği gibi çalışır. Gerçekleşen değil, hatalar, öngörülebilir ve ilk ifade ağaçları kullanma herhangi bir kod testlerinizde yakalanır.

[Sonraki--İfade yorumlama](expression-trees-interpreting.md)
