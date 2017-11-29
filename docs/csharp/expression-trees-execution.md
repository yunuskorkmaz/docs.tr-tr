---
title: "İfade ağaçlarını yürütme"
description: "İfade ağaçları yürütülebilir Ara dile (IL) talimatları dönüştürerek çalıştırma hakkında bilgi edinin."
keywords: .NET, .NET core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 109e0ac5-2a9c-48b4-ac68-9b6219cdbccf
ms.openlocfilehash: 4ca87c8410a04e9198e9dd6c379760e7b6596585
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="executing-expression-trees"></a>İfade ağaçlarını yürütme

[Önceki--Framework destekleyen ifade ağaçları türleri](expression-classes.md)

Bir *ifade ağacına* biraz kod temsil eden bir veri yapısıdır.
Derlenmiş ve yürütülebilir kodu değil. Bir ifade ağacına tarafından temsil edilen .NET kodu çalıştırmak istiyorsanız, yürütülebilir IL talimatları dönüştürmeniz gerekir. 
## <a name="lambda-expressions-to-functions"></a>Lambda ifadeleri İşlevler
Tüm LambdaExpression veya yürütülebilir IL LambdaExpression türetilmiş herhangi bir tür dönüştürebilirsiniz. Diğer ifade türleri doğrudan koda dönüştürülemiyor. Bu kısıtlama, uygulamada çok az etkisi yoktur. Lambda ifadeleri yürütülebilir Ara dile (IL) dönüştürerek yürütmek istediğiniz ifadeleri yalnızca türleridir. (Hakkında BT'nin doğrudan yürütmek anlamına gelir düşündüğünüz bir `ConstantExpression`. Bu yararlı bir şey anlamına gelir?) Olan herhangi bir ifade ağacına bir `LamdbaExpression`, veya türetilmiş bir tür `LambdaExpression` için IL dönüştürülebilir.
İfade türü `Expression<TDelegate>` .NET Core kitaplıklarında yalnızca somut bir örnektir. Bir temsilci türüyle eşleşen bir ifade göstermek için kullanılır. Bu tür bir temsilci türüyle eşleyen çünkü .NET ifade inceleyin ve lambda ifadesi imza eşleşen uygun bir temsilci için IL oluşturur. 

Çoğu durumda, bu deyim ve karşılık gelen temsilci arasında basit bir eşleme oluşturur. Örneğin, tarafından temsil edilen bir ifade ağacına `Expression<Func<int>>` türü temsilciye dönüştürülür `Func<int>`. Dönüş türü ve bağımsız değişken listesi lambda ifadesi için bu lamdba ifade tarafından temsil edilen yürütülebilir kod hedef türü olan bir temsilci türü vardır.

`LamdbaExpression` Türünü içeren `Compile` ve `CompileToMethod` bir ifade ağacına yürütülebilir koduna dönüştürmek için kullanacağınız üyeleri. `Compile` Yöntemi, bir temsilci oluşturur. `ConmpileToMethod` Yöntemi güncelleştirmeleri bir `MethodBuilder` ifade ağacına derlenmiş çıktısını gösterir IL nesnesiyle. Unutmayın `CompileToMethod` yalnızca tam masaüstü çerçevesi, .NET Core framework üzerinde kullanılabilir.

İsteğe bağlı olarak, ayrıca sağlayabilirsiniz bir `DebugInfoGenerator` bilgi oluşturulan temsilci nesne için hata ayıklama simgesi alırsınız. Bu, ifade ağacına bir temsilci nesnesine dönüştürmek ve oluşturulan temsilci hakkında tam hata ayıklama bilgileri sağlar.

Aşağıdaki kodu kullanarak temsilci bir ifade dönüştürecektir:

```csharp
Expression<Func<int>> add = () => 1 + 2;
var func = add.Compile(); // Create Delegate
var answer = func(); // Invoke Delegate
Console.WriteLine(answer);
```

Temsilci türü ifade türüne dayalıdır dikkat edin. Kesin türü belirtilmiş bir biçimde temsilci nesnesini kullanmak istiyorsanız, dönüş türü ve bağımsız değişken listesi bilmeniz gerekir. `LambdaExpression.Compile()` Yöntemi döndürür `Delegate` türü. Dönüş türü bağımsız değişken listesini kontrol edin herhangi bir derleme zamanı aracı için doğru temsilci türüne dönüştürmeniz gerekir.

## <a name="execution-and-lifetimes"></a>Yürütme ve yaşam süresi

Çağırdığınızda oluşturulan temsilci çağırarak kod yürütmek `LamdbaExpression.Compile()`. Bu where gördüğünüz `add.Compile()` temsilci döndürür. Bu temsilci çağırarak çağırma `func()` kodu yürütür.

Bu temsilci ifade ağacına kodda temsil eder. Bu temsilci tanıtıcısını korumak ve daha sonra çağırma. İfade ağacına temsil ettiği kod yürütmek istediğiniz her seferinde derleme gerekmez. (İfade ağaçları sabittir ve daha sonra aynı ifade ağacına derleme aynı kodu yürütür bir temsilci oluşturacak unutmayın.)

I gereksiz derleme çağrıları önleyerek performansı artırmak için daha karmaşık bir önbelleğe alma mekanizmasını oluşturulmaya çalışılırken karşı dikkat. Aynı algoritmayı temsil ediyorsa belirlemek için iki rastgele ifade ağaçları karşılaştırma de yürütmek için zun. İşlem süresi, hiçbir ek çağrı önleme kaydetmeniz olasılıkla bulacaksınız `LambdaExpression.Compile()` birden çok farklı iki ifade ağaçları neden aynı yürütülebilir kod belirler kodu yürütme süresi tarafından kullanılır.

## <a name="caveats"></a>Uyarılar

Lambda ifadesi bir temsilci derleme ve bu temsilciyi çağrılırken bir ifade ağacına ile gerçekleştirebileceğiniz en basit işlemler biridir. Ancak, basit işlemiyle bile bu farkında olması gereken uyarılar vardır. 

Lambda ifadeleri kapanışlar ifadesinde başvurulan tüm yerel değişkenler üzerinden oluşturun. Burada, çağrı konumda temsilci parçası olacak tüm değişkenler kullanılabilir güvence altına almalıdır `Compile`, ve sonuçta elde edilen temsilci yürütülürken.

Genel olarak, derleyici doğru olduğundan emin. Ancak, İfadenizde uygulayan bir değişken erişirse `IDisposable`, ifade ağacına tarafından tutulan işlemi hala durumdayken kodunuzu nesnesinin dispose mümkündür.

Örneğin, bu kod düzgün, çünkü çalışır `int` uygulamayan `IDisposable`:

```csharp
private static Func<int, int> CreateBoundFunc()
{
    var constant = 5; // constant is captured by the expression tree
    Expression<Func<int, int>> expression = (b) => constant + b;
    var rVal = expression.Compile();
    return rVal;
}
```

Temsilci yerel değişken başvuru yakalandı `constant`.
İşlevi tarafından döndürülen zaman dilediğiniz zaman daha sonra bu değişken erişilen `CreateBoundFunc` yürütür.

Ancak, uygular (yerine contrived) Bu sınıf göz önünde bulundurun `IDisposable`:

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

Bir ifadeyi aşağıda gösterildiği gibi kullanırsanız, elde edersiniz bir `ObjectDisposedException` başvurduğu kod yürütülürken `Resource.Argument` özelliği:

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

Bu yöntemin döndürdüğü temsilci üzerinden kapattı `constant` , atıldı nesnesi. (Olarak bildirildi çünkü bu, atılmış olan bir `using` deyimi.) 

Bu yöntemin döndürdüğü temsilci yürüttüğünüzde, şimdi gerekir bir `ObjecctDisposedException` yürütme noktasında oluşturulur.

Derleme zamanı yapısını temsil eden bir çalışma zamanı hata garip görünüyor, ancak biz ifade ağaçları ile çalışırken biz girin world olmasıdır.

Bunu önlemek için genel rehberlik sunma sabit olması için çok sayıda permütasyon bu sorunun vardır. İfadeler tanımlarken yerel değişkenler erişme hakkında dikkatli olun ve geçerli nesne durumda erişme hakkında dikkatli olun (tarafından temsil edilen `this`) ne zaman bir ifade ağacına oluşturma döndürülmesi ortak API'si tarafından.

İfadeniz kodda yöntemleri veya diğer derlemelerden özelliklerinde başvurabilir. Bu derleme ifade zaman tanımlanmış ve ne zaman derlenir ve ne zaman ortaya çıkan temsilci çağrılır erişilebilir olması gerekir. İle karşılanması bir `ReferencedAssemblyNotFoundException` durumlarda burada da mevcut değil.

## <a name="summary"></a>Özet

Lambda ifadeleri temsil ifade ağaçları yürütebilirsiniz bir temsilci oluşturmak için derlenebilir. Bu, bir ifade ağacına tarafından temsil edilen kod yürütmek için bir mekanizma sağlar.

İfade ağacına oluşturduğunuz belirli yapı için yürütülür kodunu temsil etmiyor. Burada derlemek ve kod yürütmek ortamı ifade oluşturduğunuz ortamı eşleştiği sürece her şeyin beklendiği gibi çalışır. Gerçekleşen değil, hataları çok tahmin edilebilir ve ilk ifade ağaçları kullanma herhangi bir kod testlerinizde yakalanan.

[Sonraki--İfadeleri yorumlama](expression-trees-interpreting.md)
