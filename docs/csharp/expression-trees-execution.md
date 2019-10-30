---
title: Ifade ağaçları yürütülüyor
description: Onları yürütülebilir ara dil (IL) yönergelerine dönüştürerek, ifade ağaçları yürütme hakkında bilgi edinin.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: 109e0ac5-2a9c-48b4-ac68-9b6219cdbccf
ms.openlocfilehash: 9af4b346962cb743daddf774e8b3c1f8fa722ae4
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73037109"
---
# <a name="executing-expression-trees"></a>Ifade ağaçları yürütülüyor

[Ifade ağaçlarını destekleyen önceki Framework türleri](expression-classes.md)

*İfade ağacı* , bazı kodları temsil eden bir veri yapısıdır.
Derlenmez ve çalıştırılabilir kod değildir. Bir ifade ağacı tarafından temsil edilen .NET kodunu yürütmek istiyorsanız, onu yürütülebilir Il yönergelerine dönüştürmeniz gerekir.

## <a name="lambda-expressions-to-functions"></a>IŞLEVLERE lambda Ifadeleri

Herhangi bir Lambdavexpression veya Lambdavexpression 'dan türetilmiş herhangi bir tür çalıştırılabilir Il 'ye dönüştürebilirsiniz. Diğer ifade türleri doğrudan koda dönüştürülemez. Bu kısıtlama pratikte çok daha etkilidir. Lambda ifadeleri, yürütülebilir ara dile (IL) dönüştürerek yürütmek istediğiniz tek ifade türleridir. (Bir `ConstantExpression`doğrudan yürütmek için ne anlama geldiğini düşünün. Herhangi bir şey yararlı mı?) `LambdaExpression`olan herhangi bir ifade ağacı veya `LambdaExpression` türetilmiş bir tür Il 'ye dönüştürülebilir.
`Expression<TDelegate>` ifade türü, .NET Core kitaplıklarında tek somut örnektir. Herhangi bir temsilci türüyle eşleşen bir ifadeyi temsil etmek için kullanılır. Bu tür bir temsilci türüne eşlendiğinden, .NET ifadeyi inceleyebilir ve lambda ifadesinin imzasıyla eşleşen uygun bir temsilci için Il oluşturabilir. 

Çoğu durumda bu, bir ifade ve onun karşılık gelen temsilcisi arasında basit bir eşleme oluşturur. Örneğin, `Expression<Func<int>>` tarafından temsil edilen bir ifade ağacı `Func<int>`türünün bir temsilcisine dönüştürülür. Herhangi bir dönüş türü ve bağımsız değişken listesi olan bir lambda ifadesinde, bu lambda ifadesi tarafından temsil edilen çalıştırılabilir kodun hedef türü olan bir temsilci türü vardır.

`LambdaExpression` türü, bir ifade ağacını çalıştırılabilir koda dönüştürmek için kullanacağınız `Compile` ve `CompileToMethod` üyelerini içerir. `Compile` yöntemi bir temsilci oluşturur. `CompileToMethod` yöntemi, ifade ağacının derlenmiş çıkışını temsil eden Il ile bir `MethodBuilder` nesnesini günceller. `CompileToMethod`, .NET Core 'da değil, yalnızca tam masaüstü çerçevesinde kullanılabilir olduğunu unutmayın.

İsteğe bağlı olarak, oluşturulan temsilci nesnesi için simge hata ayıklama bilgilerini alacak bir `DebugInfoGenerator` de sağlayabilirsiniz. Bu, ifade ağacını bir temsilci nesnesine dönüştürmenize ve oluşturulan temsilciyle ilgili tam hata ayıklama bilgilerine sahip etmenize olanak sağlar.

Aşağıdaki kodu kullanarak bir ifadeyi temsilciye dönüştürürsünüz:

```csharp
Expression<Func<int>> add = () => 1 + 2;
var func = add.Compile(); // Create Delegate
var answer = func(); // Invoke Delegate
Console.WriteLine(answer);
```

Temsilci türünün ifade türüne göre olduğuna dikkat edin. Temsilci nesnesini kesin olarak belirlenmiş bir şekilde kullanmak istiyorsanız, dönüş türünü ve bağımsız değişken listesini bilmeniz gerekir. `LambdaExpression.Compile()` yöntemi `Delegate` türünü döndürür. Herhangi bir derleme zamanı aracının bağımsız değişken listesini veya dönüş türünü denetlemesini sağlamak için onu doğru temsilci türüne atamalısınız.

## <a name="execution-and-lifetimes"></a>Yürütme ve yaşam süreleri

Kodu, `LambdaExpression.Compile()`çağrıldığında oluşturulan temsilciyi çağırarak yürütün. Bunu, `add.Compile()` bir temsilci döndürdüğü yerde görebilirsiniz. Bu temsilciyi çağırmak `func()` çağırarak kodu yürütür.

Bu temsilci, ifade ağacındaki kodu temsil eder. Bu temsilciye yönelik tanıtıcıyı koruyabilir ve daha sonra çağırabilirsiniz. Temsil ettiği kodu yürütmek istediğiniz her seferinde ifade ağacını derlemeniz gerekmez. (İfade ağaçlarının sabit olduğunu unutmayın ve aynı ifade ağacını daha sonra derlemek aynı kodu çalıştıran bir temsilci oluşturur.)

Gereksiz derleme çağrılarını önleyerek performansı artırmak için daha gelişmiş bir önbelleğe alma mekanizması oluşturmaya çalışırken dikkatli olunacaktır. İki rastgele ifade ağacının karşılaştırılması, aynı algoritmanın aynı algoritmayı temsil ettiğini tespit etmek için zaman alıcı olarak da kullanılır. Büyük olasılıkla, `LambdaExpression.Compile()` ek çağrılarından kaçınmaktan kaynaklanan işlem zamanının, aynı çalıştırılabilir kodun sonucu olan iki farklı ifade ağacının sonucunu belirleyen kod yürütme sırasında tüketildiğinden daha fazla olacağını fark edeceksiniz.

## <a name="caveats"></a>Uyarılar

Bir lambda ifadesini bir temsilciye derlemek ve bu temsilciyi çağırmak, bir ifade ağacı ile gerçekleştirebileceğiniz en basit işlemlerden biridir. Ancak, bu basit işlemle birlikte, bilmeniz gereken uyarılar da vardır. 

Lambda Ifadeleri, ifadede başvurulan herhangi bir yerel değişken üzerinde kapanışları oluşturur. Temsilcinin parçası olacak tüm değişkenlerin `Compile`çağırdığınız konumda kullanılabilir olduğunu ve elde edilen temsilciyi yürüttüğünüzde emin olmanız gerekir.

Genel olarak, derleyici bunun doğru olduğundan emin olur. Ancak, ifadeniz `IDisposable`uygulayan bir değişkene eriştiğinde, kodunuzun nesneyi hala ifade ağacı tarafından tutulurken atma olasılığı vardır.

Örneğin, `int` `IDisposable`uygulamadığından, bu kod düzgün çalışıyor:

```csharp
private static Func<int, int> CreateBoundFunc()
{
    var constant = 5; // constant is captured by the expression tree
    Expression<Func<int, int>> expression = (b) => constant + b;
    var rVal = expression.Compile();
    return rVal;
}
```

Temsilci `constant`yerel değişkenine bir başvuru yakalamıştır.
Bu değişkene, daha sonra `CreateBoundFunc` tarafından döndürülen işlev çalıştırıldığında her zaman erişilir.

Ancak, `IDisposable`uygulayan (Bunun yerine contrived) sınıfını göz önünde bulundurun:

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

Bunu aşağıda gösterildiği gibi bir ifadede kullanırsanız, `Resource.Argument` özelliği tarafından başvurulan kodu yürüttüğünüzde `ObjectDisposedException` alırsınız:

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

Bu yöntemden döndürülen temsilci, atılmış olan `constant` nesnesi üzerinde kapandı. (Bir `using` bildiriminde bildirildiği için atılmış.) 

Artık bu yöntemden döndürülen temsilciyi yürüttüğünüzde, yürütme noktasında bir `ObjectDisposedException` oluşturulur.

Derleme zamanı yapısını temsil eden bir çalışma zamanı hatası olması garip görünür, ancak bu, ifade ağaçları ile çalışırken girdiğimiz dünya.

Bu sorunun birçok permütasyon vardır. bu nedenle, bunu önlemek için genel rehberlik sunmak zordur. İfadeleri tanımlarken yerel değişkenlere erişmede dikkatli olun ve genel bir API tarafından döndürülebilecek bir ifade ağacı oluştururken geçerli nesnedeki duruma (`this`göre gösterilen) erişme konusunda dikkatli olun.

Deyiminizdeki kod, diğer derlemelerdeki yöntemlere veya özelliklere başvurabilir. İfade tanımlandığında ve derlendikten sonra ve elde edilen temsilci çağrıldığında bu derlemeye erişilebilir olması gerekir. Mevcut olmadığı durumlarda `ReferencedAssemblyNotFoundException` karşılanır.

## <a name="summary"></a>Özet

Lambda ifadelerini temsil eden ifade ağaçları, yürütebilmeniz için bir temsilci oluşturmak üzere derlenebilir. Bu, bir ifade ağacı tarafından temsil edilen kodu yürütmek için bir mekanizma sağlar.

Ifade ağacı, oluşturduğunuz herhangi bir yapı için yürütülecek kodu temsil eder. Kodu derlemek ve yürütmek istediğiniz ortam, ifadeyi oluşturduğunuz ortamla eşleşiyorsa, her şey beklendiği gibi çalışmaktadır. Bu durum gerçekleşmezse, hatalar çok öngörülebilir olur ve ifade ağaçları kullanılarak herhangi bir kodun ilk testlerinizde yakalanacaktır.

[Sonraki--Ifadeleri yorumlama](expression-trees-interpreting.md)
