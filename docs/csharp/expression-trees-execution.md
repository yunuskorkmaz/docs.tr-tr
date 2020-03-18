---
title: İfade Ağaçlarını Yürütme
description: Yürütülebilir Ara Dil (IL) yönergelerine dönüştürerek ifade ağaçlarını yürütme hakkında bilgi edinin.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: 109e0ac5-2a9c-48b4-ac68-9b6219cdbccf
ms.openlocfilehash: 802a83f52f9c05a99c3f49f8f6511eff81ef3eaa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146027"
---
# <a name="executing-expression-trees"></a>İfade Ağaçlarını Yürütme

[Önceki -- İfade Ağaçlarını Destekleyen Çerçeve Türleri](expression-classes.md)

*İfade ağacı,* bazı kodları temsil eden bir veri yapısıdır.
Derlenmiş ve çalıştırılabilir kod değildir. Bir ifade ağacı tarafından temsil edilen .NET kodunu yürütmek istiyorsanız, bunu çalıştırılabilir IL yönergelerine dönüştürmeniz gerekir.

## <a name="lambda-expressions-to-functions"></a>Lambda İfadeleri Fonksiyonlara

LambdaExpression'ı veya LambdaExpression'dan türetilen herhangi bir türü çalıştırılabilir IL'ye dönüştürebilirsiniz. Diğer ifade türleri doğrudan koda dönüştürülemez. Bu kısıtlamanın pratikte çok az etkisi vardır. Lambda ifadeleri, yürütülebilir ara dile (IL) dönüştürerek yürütmek istediğiniz tek ifade türleridir. (Doğrudan bir `ConstantExpression`yürütmek için ne anlama geleceğini düşünün . Yararlı bir şey anlamına gelir mi?) Bir , veya `LambdaExpression`türetilen bir tür `LambdaExpression` herhangi bir ifade ağacı IL dönüştürülebilir.
İfade türü `Expression<TDelegate>` .NET Core kitaplıklarında tek somut örnektir. Herhangi bir temsilci türüyle eşleyen bir ifadeyi temsil etmek için kullanılır. Bu tür bir temsilci türüyle eşleşip, .NET ifadeyi inceleyebilir ve lambda ifadesinin imzasıyla eşleşen uygun bir temsilci için IL oluşturabilir.

Çoğu durumda, bu bir ifade ve karşılık gelen temsilcisi arasında basit bir eşleme oluşturur. Örneğin, temsil `Expression<Func<int>>` edilen bir ifade ağacı türünün `Func<int>`bir temsilcisine dönüştürülür. Herhangi bir dönüş türü ve bağımsız değişken listesi olan bir lambda ifadesi için, bu lambda ifadesi tarafından temsil edilen yürütülebilir kodun hedef türü olan bir temsilci türü vardır.

Bir `LambdaExpression` ifade `Compile` `CompileToMethod` ağacını yürütülebilir koda dönüştürmek için kullanacağınız tür ve üyeler. Yöntem `Compile` bir temsilci oluşturur. Yöntem, `CompileToMethod` ifade `MethodBuilder` ağacının derlenmiş çıktısını temsil eden IL ile bir nesneyi güncelleştirir. Sadece `CompileToMethod` masaüstü çerçevesinde kullanılabildiğini, .NET Core'da bulunmadığını unutmayın.

İsteğe bağlı olarak, `DebugInfoGenerator` oluşturulan temsilci nesnesi için simge hata ayıklama bilgilerini alacak bir de sağlayabilirsiniz. Bu, ifade ağacını bir temsilci nesnesine dönüştürmenize ve oluşturulan temsilci hakkında tam hata ayıklama bilgisine sahip yapmanızı sağlar.

Aşağıdaki kodu kullanarak bir ifadeyi temsilciye dönüştürürsunuz:

```csharp
Expression<Func<int>> add = () => 1 + 2;
var func = add.Compile(); // Create Delegate
var answer = func(); // Invoke Delegate
Console.WriteLine(answer);
```

Temsilci türünün ifade türüne dayandığına dikkat edin. Temsilci nesnesini güçlü bir şekilde kullanmak istiyorsanız, iade türünü ve bağımsız değişken listesini bilmeniz gerekir. Yöntem `LambdaExpression.Compile()` türü `Delegate` döndürür. Derleme zamanı araçlarının bağımsız değişken listesini veya dönüş türünü denetlemesi için doğru temsilci türüne dökmeniz gerekir.

## <a name="execution-and-lifetimes"></a>Yürütme ve Ömür Ler

'yi çağırdığınızda `LambdaExpression.Compile()`oluşturulan temsilciyi çağırarak kodu çalıştırMışsınız. Bunu yukarıda bir `add.Compile()` temsilci döndürür. Bu temsilciyi çağırmak, `func()` kodu çağırarak yürütür.

Bu temsilci, ifade ağacındaki kodu temsil eder. Tutamacı bu temsilciye saklayabilir ve daha sonra çağırabilirsiniz. Temsil edilen kodu her yürütmek istediğinizde ifade ağacını derlemeniz gerekmez. (İfade ağaçlarının değişmez olduğunu unutmayın ve aynı ifade ağacını derlemek daha sonra aynı kodu çalıştıran bir temsilci oluşturur.)

Gereksiz derleme çağrılarından kaçınarak performansı artırmak için daha karmaşık önbelleğe alma mekanizmaları oluşturmaya çalışmamanızı konusunda sizi uyaracağım. Aynı algoritmayı temsil edip etmediklerini belirlemek için iki rasgele ifade ağacını karşılaştırmak da yürütmek için zaman alıcı olacaktır. Büyük olasılıkla, fazladan aramadan kaçınmak için `LambdaExpression.Compile()` kaydettiğiniz işlem süresinin, iki farklı ifade ağacının aynı yürütülebilir kodla sonuçlanan kod yürütme süresi tarafından tüketilenden daha fazla olacağını göreceksiniz.

## <a name="caveats"></a>Uyarılar

Bir temsilciye lambda ifadesini derlemek ve bu temsilciyi çağırmak bir ifade ağacıyla gerçekleştirebileceğiniz en basit işlemlerden biridir. Ancak, bu basit operasyon bile, bilmeniz gereken uyarılar vardır.

Lambda İfadeleri, ifadede başvurulan tüm yerel değişkenler üzerinde kapanışlar oluşturur. Temsilcinin bir parçası olacak değişkenlerin, çağırdığınız `Compile`konumda ve ortaya çıkan temsilciyi çalıştırdığınızda kullanılabilir olduğunu garanti etmeniz gerekir.

Genel olarak, derleyici bunun doğru olduğundan emin olacaktır. Ancak, ifadeniz uygulayan bir değişkene `IDisposable`erişirse, kodunuzun ifade ağacı tarafından hala tutulurken nesneyi elden çıkarabilmesi mümkündür.

Örneğin, bu kod iyi `int` çalışır, `IDisposable`çünkü uygulanmaz:

```csharp
private static Func<int, int> CreateBoundFunc()
{
    var constant = 5; // constant is captured by the expression tree
    Expression<Func<int, int>> expression = (b) => constant + b;
    var rVal = expression.Compile();
    return rVal;
}
```

Temsilci yerel değişkene `constant`bir başvuru yakaladı.
Bu değişkene daha sonra, işlev yürütüldüğünde `CreateBoundFunc` erişilir.

Ancak, bu (oldukça contrived) sınıf `IDisposable`uygular düşünün:

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

Aşağıda gösterildiği gibi bir ifadede kullanırsanız, `ObjectDisposedException` `Resource.Argument` özellik tarafından başvurulan kodu çalıştırdığınızda bir

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

Bu yöntemden döndürülen temsilci, `constant` elden çıkarılan nesnenin üzerine kapandı. (Bir `using` açıklamada beyan edildiği için imha edildi.)

Şimdi, bu yöntemden döndürülen temsilciyi çalıştırdığınızda, yürütme noktasında bir `ObjectDisposedException` atma olacak.

Derleme zamanı yapısını temsil eden bir çalışma zamanı hatası olması garip görünüyor, ama ifade ağaçlarıyla çalışırken girdiğimiz dünya bu.

Bu sorunun permütasyon bir yeri vardır, bu yüzden bunu önlemek için genel rehberlik sunmak zor. İfadeleri tanımlarken yerel değişkenlere erişirken dikkatli olun ve genel bir API tarafından `this`döndürülebilen bir ifade ağacı oluştururken geçerli nesnedeki (temsil edilen) duruma erişme konusunda dikkatli olun.

İfadenizdeki kod, diğer derlemelerde yöntemlere veya özelliklere başvurabilir. İfade tanımlandığında, derlendiğinde ve sonuç temsilcisi çağrıldığında bu derlemeye erişilebilir olmalıdır. Mevcut olmayan durumlarda bir `ReferencedAssemblyNotFoundException` ile karşılanacaksınız.

## <a name="summary"></a>Özet

Expression Trees bu ifadeyi temsil eden lambda ifadelerini yürütebileceğiniz bir temsilci oluşturmak için derlenebilir. Bu, bir ifade ağacı tarafından temsil edilen kodu yürütmek için bir mekanizma sağlar.

İfade Ağacı, oluşturduğunuz belirli bir yapı için yürütülecek kodu temsil eder. Kodu derlediğiniz ve yürütdüğünüz ortam, ifadeyi oluşturduğunuz ortamla eşleştiği sürece, her şey beklendiği gibi çalışır. Bu olmadığında, hatalar çok tahmin edilebilir ve ifade ağaçları kullanarak herhangi bir kod ilk testleri yakalanmış olacak.

[Sonraki -- İfadeleri Yorumlama](expression-trees-interpreting.md)
