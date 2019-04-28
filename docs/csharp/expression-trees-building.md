---
title: Yapı ifade ağaçları
description: İfade ağaçları oluşturmaya yönelik teknikleri hakkında bilgi edinin.
ms.date: 06/20/2016
ms.assetid: 542754a9-7f40-4293-b299-b9f80241902c
ms.openlocfilehash: 7751af17aafa8e2d1a14125da43352108b1c1f95
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61646604"
---
# <a name="building-expression-trees"></a>Yapı ifade ağaçları

[Önceki--İfade yorumlama](expression-trees-interpreting.md)

Görmüş kadarki tüm ifade ağaçları tarafından oluşturulan C# derleyici. Tüm yapmanız gerekiyordu edildi olarak yazılmış bir değişkene atanmış bir lambda ifadesi oluşturma bir `Expression<Func<T>>` veya benzer bir tür. İfade ağacı oluşturmak için tek yolu değil. Birçok senaryo için çalışma zamanında bellekte bir ifade oluşturmak gerektiğini fark edebilirsiniz. 

Bu ifade ağaçları sabittir olgusu karmaşık ifade ağaçları oluşturma. Kök kadar leaves ağacından derlemelidir olan sabit anlamına gelir. İfade ağaçları oluşturmak için kullanacağınız API'leri bu olgu yansıtır: Bir düğüm oluşturmak için kullanacağınız yöntemleri, bağımsız tüm alt öğelerini alır. Teknikleri göstermek için bazı örnekler atalım.

## <a name="creating-nodes"></a>Düğümler oluşturma

Görece basit başlayalım yeniden. Bu bölümleri miyim ile çalışmalar ek ifade kullanacağız:

```csharp
Expression<Func<int>> sum = () => 1 + 2;
```

Bu ifade ağacını oluşturmanın için yaprak düğümleri oluşturmalıdır.
Kullanabileceğiniz sabitleri ve yaprak düğümlerin olduğundan `Expression.Constant` düğümleri oluşturma yöntemi:

```csharp
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
```

Ardından, ek ifade oluşturacaksınız:

```csharp
var addition = Expression.Add(one, two);
```

Ek ifade başladıktan sonra lambda ifadesi oluşturabilirsiniz:

```csharp
var lambda = Expression.Lambda(addition);
```

Bağımsız değişken içeren çok basit bir lambda ifadesi, olmasıdır.
Daha sonra bu bölümde, parametreler için bağımsız değişken eşleme ve daha karmaşık ifadeleri oluşturmak nasıl göreceksiniz.

Bu bir basit ifadeler için tek bir deyimde tüm çağırıyor Birleştir:

```csharp
var lambda = Expression.Lambda(
    Expression.Add(
        Expression.Constant(1, typeof(int)),
        Expression.Constant(2, typeof(int))
    )
);
```

## <a name="building-a-tree"></a>Bir ağaç oluşturma

Bellekte bir ifade ağacı oluşturma hakkındaki temel bilgileri olmasıdır. Daha karmaşık ağaçlar genellikle daha fazla düğüm türleri ve daha fazla düğüm ağaçta anlamına gelir. Şimdi aracılığıyla daha fazla örneği çalıştırmak ve ifade ağaçları oluşturduğunuzda, genellikle oluşturacağınız iki daha fazla düğüm türleri göster: bağımsız değişken düğümleri ve yöntem çağrısı düğümleri.

Bu ifade oluşturmak için bir ifade ağacı oluşturalım:

```csharp
Expression<Func<double, double, double>> distanceCalc =
    (x, y) => Math.Sqrt(x * x + y * y);
```
 
Parametresi ifadelerine için oluşturarak başlayacağız `x` ve `y`:

```csharp
var xParameter = Expression.Parameter(typeof(double), "x");
var yParameter = Expression.Parameter(typeof(double), "y");
```

Çarpma ve ayrıca ifadeleri oluşturma gördünüz deseni izler:

```csharp
var xSquared = Expression.Multiply(xParameter, xParameter);
var ySquared = Expression.Multiply(yParameter, yParameter);
var sum = Expression.Add(xSquared, ySquared);
```

Ardından, bir yöntem çağrısı ifadesi için yapılan çağrının oluşturmak için ihtiyacınız `Math.Sqrt`.

```csharp
var sqrtMethod = typeof(Math).GetMethod("Sqrt", new[] { typeof(double) });
var distance = Expression.Call(sqrtMethod, sum);
```

Ve son olarak, yöntem çağrısının bir lambda ifadesine yerleştirin, lambda ifadesine bağımsız değişkenler tanımladığınızdan emin olun:

```csharp
var distanceLambda = Expression.Lambda(
    distance,
    xParameter,
    yParameter);
```

Bu daha karmaşık bir örnekte, ifade ağacı oluşturmak için genellikle gereken birkaç daha fazla teknikleri bakın.

İlk olarak, kullanmadan önce parametrelerin veya yerel değişkenleri temsil eden nesneleri oluşturmanız gerekir. Bu nesneler oluşturduktan sonra istediğiniz yerden onları, ifade ağacında kullanabilirsiniz.

İkinci olarak, yansıma API kümesini oluşturmak için kullanılacak ihtiyacınız bir `MethodInfo` bu yönteme erişmek için bir ifade ağacı oluşturabilmesi nesne. Kendiniz bir .NET Core platformda kullanılabilir yansıma API'lerden alt sınırı, gerekir. Yeniden, bu teknikler diğer ifade ağaçlarına genişletilir.

## <a name="building-code-in-depth"></a>Derinlemesine kod oluşturma

Şunları yapabilirsiniz sınırlı olmayan bu API'leri kullanarak oluşturun. Ancak, daha zordur yönetmek ve okuma için kodudur, oluşturmak istediğiniz bir ifade ağacı çok karmaşık. 

Bu kod eşdeğerdir bir ifade ağacı oluşturalım:

```csharp
Func<int, int> factorialFunc = (n) =>
{
    var res = 1;
    while (n > 1)
    {
        res = res * n;
        n--;
    }
    return res;
};
```

Yukarıda miyim ifade ağacı, ancak yalnızca temsilci derlenmedi, dikkat edin. Kullanarak `Expression` sınıfı, deyim lambdaları oluşturamıyor. Aynı işlevselliği oluşturmak için gereken kod aşağıdaki gibidir. Bir API oluşturmak için hiç olgusu karmaşık bir `while` döngü, bunun yerine bir koşul testi ve etiket hedefi döngüden içeren bir döngü oluşturmak için ihtiyacınız. 

```csharp
var nArgument = Expression.Parameter(typeof(int), "n");
var result = Expression.Variable(typeof(int), "result");

// Creating a label that represents the return value
LabelTarget label = Expression.Label(typeof(int));

var initializeResult = Expression.Assign(result, Expression.Constant(1));

// This is the inner block that performs the multiplication,
// and decrements the value of 'n'
var block = Expression.Block(
    Expression.Assign(result,
        Expression.Multiply(result, nArgument)),
    Expression.PostDecrementAssign(nArgument)
);

// Creating a method body.
BlockExpression body = Expression.Block(
    new[] { result },
    initializeResult,
    Expression.Loop(
        Expression.IfThenElse(
            Expression.GreaterThan(nArgument, Expression.Constant(1)),
            block,
            Expression.Break(label, result)
        ),
        label
    )
);
```

İfade ağacı Faktöriyel işlevi oluşturmak için kodu daha karmaşık, oldukça biraz daha uzun ve etiketleri kesme deyimleri ve diğer öğeleri önlemek için kodlama görevleri, her gün içinde istiyoruz riddled. 

Bu bölüm için miyim ziyaretçi kod, her düğüm bu ifade ağacı ziyaret edin ve bu örnekte oluşturulan düğümleri hakkında bilgi yazmak için de güncelleştirdik. Yapabilecekleriniz [görüntülemek veya örnek kodu indirdikten](https://github.com/dotnet/samples/tree/master/csharp/expression-trees) dotnet/docs GitHub deposunda bulabilirsiniz. Oluşturma ve örnekleri çalıştırmaya kendiniz denemeler yapın. Yükleme yönergeleri için bkz: [örnekler ve öğreticiler](../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="examining-the-apis"></a>API'leri İnceleme

İfade ağacı API'leri de .NET Core giderek daha zor bazıları, ancak, bir sakınca yoktur. Bunların amacı yerine karmaşık bir iştir: çalışma zamanında kodu oluşturan kod yazma. Kullanılabilir tüm denetim yapıları destekleyen arasında bir denge sağlamak mutlaka karmaşık oldukları C# dil ve yüzey alanını olabildiğince küçük API'leri gibi makul tutma. Birçok denetim yapıları tarafından temsil edilen bu dengeyi anlamına gelir, C# oluşturur, ancak bu daha yüksek bir düzeyinden derleyici oluşturan temel mantığı göstermek yapıları tarafından oluşturur. 

Ayrıca, şu anda vardır C# kullanarak doğrudan oluşturulamıyor ifadeleri `Expression` sınıfı yöntemleri. Genel olarak, bunlar yeni işleçleri olacaktır ve ifadeleri eklenen içinde C# 5 ve C# 6. (Örneğin, `async` ifadeleri yerleşik olamaz ve yeni `?.` işleci doğrudan oluşturulamıyor.)

[Sonraki--İfade çevirme](expression-trees-translating.md)
