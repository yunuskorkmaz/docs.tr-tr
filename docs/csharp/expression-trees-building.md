---
title: Bina İfade Ağaçları
description: İfade ağaçları oluşturma teknikleri hakkında bilgi edinin.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: 542754a9-7f40-4293-b299-b9f80241902c
ms.openlocfilehash: c93eb16ebf2ff66dc0162afb6841f2cadfce174e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146053"
---
# <a name="building-expression-trees"></a>Bina İfade Ağaçları

[Önceki -- İfadeleri Yorumlama](expression-trees-interpreting.md)

Şimdiye kadar gördüğünüz tüm ifade ağaçları C# derleyicisi tarafından oluşturuldu. Yapmanız gereken tek şey bir veya benzer tür olarak yazılan bir `Expression<Func<T>>` değişkene atanan bir lambda ifadesi oluşturmaktı. İfade ağacı oluşturmanın tek yolu bu değil. Birçok senaryo için, çalışma zamanında bellekte bir ifade oluşturmanız gerektiğini görebilirsiniz.

Bina İfade Ağaçları bu ifade ağaçları değişmez olması ile karmaşıktır. Değişmez olmak, ağacı yapraklardan köküne kadar oluşturmanız gerektiği anlamına gelir. İfade ağaçları oluşturmak için kullanacağınız API'ler şu gerçeği yansıtır: Düğüm oluşturmak için kullanacağınız yöntemler tüm çocuklarını bağımsız değişken olarak alır. Size teknikleri göstermek için birkaç örnek üzerinden yürüyelim.

## <a name="creating-nodes"></a>Düğüm oluşturma

Göreceli olarak tekrar başlayalım. Bu bölümlerboyunca üzerinde çalıştığım ek ifadeyi kullanacağız:

```csharp
Expression<Func<int>> sum = () => 1 + 2;
```

Bu ifade ağacı oluşturmak için, yaprak düğümleri inşa gerekir.
Yaprak düğümleri sabittir, bu nedenle düğümleri oluşturmak için `Expression.Constant` yöntemi kullanabilirsiniz:

```csharp
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
```

Ardından, ek ifadesini oluşturursunuz:

```csharp
var addition = Expression.Add(one, two);
```

Ek ifadeyi aldıktan sonra lambda ifadesini oluşturabilirsiniz:

```csharp
var lambda = Expression.Lambda(addition);
```

Bu çok basit bir lambda ifadesidir, çünkü hiçbir argüman içermez.
Bu bölümün ilerleyen bölümlerinde, bağımsız değişkenleri parametrelerle nasıl eşlediğinizi ve daha karmaşık ifadeler nasıl oluşturacağınızı göreceksiniz.

Bu kadar basit ifadeler için, tüm çağrıları tek bir deyimde birleştirebilirsiniz:

```csharp
var lambda = Expression.Lambda(
    Expression.Add(
        Expression.Constant(1, typeof(int)),
        Expression.Constant(2, typeof(int))
    )
);
```

## <a name="building-a-tree"></a>Ağaç İnşa Etmek

Bu bellekte bir ifade ağacı oluşturmanın temelleridir. Daha karmaşık ağaçlar genellikle daha fazla düğüm türleri ve ağaçta daha fazla düğüm anlamına gelir. Bir örnek daha inceleyelim ve ifade ağaçları oluşturduğunuzda genellikle oluşturacağınız iki düğüm türü daha gösterelim: bağımsız değişken düğümleri ve yöntem çağrı düğümleri.

Bu ifadeyi oluşturmak için bir ifade ağacı oluşturalım:

```csharp
Expression<Func<double, double, double>> distanceCalc =
    (x, y) => Math.Sqrt(x * x + y * y);
```

Parametre ifadeleri oluşturarak başlayacaksınız `x` ve: `y`

```csharp
var xParameter = Expression.Parameter(typeof(double), "x");
var yParameter = Expression.Parameter(typeof(double), "y");
```

Çarpma ve ekleme ifadeleri oluşturma, daha önce gördüğünüz deseni izler:

```csharp
var xSquared = Expression.Multiply(xParameter, xParameter);
var ySquared = Expression.Multiply(yParameter, yParameter);
var sum = Expression.Add(xSquared, ySquared);
```

Ardından, çağrı için bir yöntem arama ifadesi `Math.Sqrt`oluşturmanız gerekir.

```csharp
var sqrtMethod = typeof(Math).GetMethod("Sqrt", new[] { typeof(double) });
var distance = Expression.Call(sqrtMethod, sum);
```

Ve son olarak, bir lambda ifade içine yöntem arama koymak ve lambda ifade argümanlar tanımlamak için emin olun:

```csharp
var distanceLambda = Expression.Lambda(
    distance,
    xParameter,
    yParameter);
```

Bu daha karmaşık örnekte, genellikle ifade ağaçları oluşturmak için gereken birkaç teknik daha bakın.

İlk olarak, bunları kullanmadan önce parametreleri veya yerel değişkenleri temsil eden nesneleri oluşturmanız gerekir. Bu nesneleri oluşturduktan sonra, bunları istediğiniz yerde ifade ağacınızda kullanabilirsiniz.

İkinci olarak, bu yönteme erişmek için bir ifade `MethodInfo` ağacı oluşturabilmeniz için bir nesne oluşturmak için Yansıma API'lerinin bir alt kümesini kullanmanız gerekir. Kendinizi .NET Core platformunda bulunan Yansıma API'lerinin alt kümesiyle sınırlamanız gerekir. Yine, bu teknikler diğer ifade ağaçları genişletecektir.

## <a name="building-code-in-depth"></a>Derinlemesine Yapı Kodu

Bu API'leri kullanarak oluşturabilecekleriniz sınırlı değildir. Ancak, oluşturmak istediğiniz daha karmaşık ifade ağacı, kod yönetmek ve okumak için daha zor.

Bu kodun eşdeğeri olan bir ifade ağacı oluşturalım:

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

Yukarıda dikkat edin ben ifade ağacı inşa etmedi, ama sadece delege. `Expression` Sınıfı kullanarak, ifade lambdas inşa edemez. İşte aynı işlevselliği oluşturmak için gereken kod. Bir `while` döngü oluşturmak için bir API olmaması, bunun yerine koşullu bir test içeren bir döngü ve döngüden çıkmak için bir etiket hedefi oluşturmanız gerekir.

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

Faktöriyel işlev için ifade ağacı oluşturmak için kod biraz daha uzun, daha karmaşık, ve etiketler ilerler ve break ifadeleri ve günlük kodlama görevleri önlemek istiyorum diğer öğeleri ile delik deşik's.

Bu bölüm için, bu ifade ağacındaki her düğümü ziyaret etmek ve bu örnekte oluşturulan düğümler hakkında bilgi yazmak için ziyaretçi kodunu da güncelledim. Örnek kodu dotnet/docs GitHub deposundan [görüntüleyebilir veya indirebilirsiniz.](https://github.com/dotnet/samples/tree/master/csharp/expression-trees) Örnekleri oluşturarak ve çalıştırarak kendiniz deneyin. İndirme talimatları için [Örnekler ve Öğreticiler'e](../samples-and-tutorials/index.md#viewing-and-downloading-samples)bakın.

## <a name="examining-the-apis"></a>API'lerin incelenmesi

İfade ağacı API'leri .NET Core'da gezinmek daha zor olanlardan bazılarıdır, ancak bu sorun değil. Amaçları oldukça karmaşık bir girişimdir: çalışma zamanında kod üreten kod yazmak. C# dilinde bulunan tüm kontrol yapılarını desteklemek ve API'lerin yüzey alanını makul olduğunca küçük tutmak arasında bir denge sağlamak için mutlaka karmaşıktır. Bu denge, birçok denetim yapısının C# yapıları ile değil, derleyicinin bu üst düzey yapılardan oluşturduğu temel mantığı temsil eden yapılartarafından temsil edildiği anlamına gelir.

Ayrıca, şu anda, doğrudan sınıf yöntemleri kullanılarak `Expression` oluşturulamayan C# ifadeleri vardır. Genel olarak, bunlar C# 5 ve C# 6'da eklenen en yeni işleçler ve ifadeler olacaktır. (Örneğin, `async` ifadeler oluşturulamaz ve yeni `?.` işleç doğrudan oluşturulamaz.)

[Sonraki -- İfadeleri Çevirme](expression-trees-translating.md)
