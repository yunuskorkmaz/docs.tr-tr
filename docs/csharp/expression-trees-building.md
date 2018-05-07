---
title: Yapı ifade ağaçları
description: İfade ağaçları oluşturma teknikleri hakkında bilgi edinin.
ms.date: 06/20/2016
ms.assetid: 542754a9-7f40-4293-b299-b9f80241902c
ms.openlocfilehash: 52e03bd1ea2635d75da6d70af6918b33b64622b0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="building-expression-trees"></a>Yapı ifade ağaçları

[Önceki--İfadeleri yorumlama](expression-trees-interpreting.md)

Şu ana kadar gördüğünüz ifade ağaçları C# Derleyici tarafından oluşturuldu. Tüm yapmanız gerekiyordu edildi olarak türünde bir değişkenden atandığı bir lambda ifadesi oluşturma bir `Expression<Func<T>>` veya bazı benzer türü. Bir ifade ağacına oluşturmak için tek yolu değil. Birçok senaryoları için bellek çalışma zamanında bir ifadede yapı gerektiğini fark edebilirsiniz. 

İfade ağaçları oluşturma Bu ifade ağaçları değişmez gerçeğiyle karmaşık. Kök kadar bırakır ağacından oluşturmalısınız olan değişmez anlamına gelir. İfade ağaçları oluşturmak için kullanmanız API'leri olgunun yansıtacak: bir düğüm oluşturmak için kullandığınız yöntemleri bağımsız olarak tüm alt öğelerini alın. Şimdi teknikleri göstermek için birkaç örneklerle yol.

## <a name="creating-nodes"></a>Düğümlerini oluşturma

Görece basit başlayalım yeniden. Bu bölümleri t ile çalışmakta Toplama ifadesi kullanacağız:

```csharp
Expression<Func<int>> sum = () => 1 + 2;
```

Bu ifade ağacına oluşturmak için ve yaprak düğümlerin oluşturmalıdır.
Kullanabilmek için ve yaprak düğümlerin, sabittir `Expression.Constant` yöntemi düğümleri oluşturmak için:

```csharp
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
```

Ardından, toplama ifadesi oluştur:

```csharp
var addition = Expression.Add(one, two);
```

Toplama ifadesi getirdikten sonra lambda ifadesi oluşturabilirsiniz:

```csharp
var lamdba = Expression.Lambda(addition);
```

Bağımsız değişkenler içerdiğinden çok basit bir LambdaExpression budur.
Daha sonra bu bölümde, bağımsız değişkenler parametreleriyle eşleyin ve daha karmaşık ifadeleri oluşturmak nasıl görürsünüz.

Bu bir basit ifadeler için tek bir deyimde tüm çağrılar birleştirmek:

```csharp
var lambda = Expression.Lambda(
    Expression.Add(
        Expression.Constant(1, typeof(int)),
        Expression.Constant(2, typeof(int))
    )
);
```

## <a name="building-a-tree"></a>Bir ağaç oluşturma

Bir ifade ağacına bellekte oluşturmanın temel olmasıdır. Daha karmaşık ağaçları genellikle daha fazla düğüm türleri ve daha fazla düğüm ağacında anlamına gelir. Şimdi aracılığıyla bir örnek daha çalıştırın ve ifade ağaçları oluşturduğunuzda, genellikle oluşturacaksınız iki daha fazla düğüm türleri göster: bağımsız değişken düğümleri ve yöntem çağrısı düğümleri.

Şimdi bu deyim oluşturmak için bir ifade ağacına oluşturun:

```csharp
Expression<Func<double, double, double>> distanceCalc =
    (x, y) => Math.Sqrt(x * x + y * y);
```
 
Parametresi ifadelerine oluşturarak başlayacağız `x` ve `y`:

```csharp
var xParameter = Expression.Parameter(typeof(double), "x");
var yParameter = Expression.Parameter(typeof(double), "y");
```

Çarpma ve toplama ifadeleri oluşturma gördünüz deseni izler:

```csharp
var xSquared = Expression.Multiply(xParameter, xParameter);
var ySquared = Expression.Multiply(yParameter, yParameter);
var sum = Expression.Add(xSquared, ySquared);
```

Ardından, bir yöntem çağrısı ifadesi çağrısı için oluşturmanız gerekir `Math.Sqrt`.

```csharp
var sqrtMethod = typeof(Math).GetMethod("Sqrt", new[] { typeof(double) });
var distance = Expression.Call(sqrtMethod, sum);
```

Ve ardından son olarak, yöntem çağrısının bir lambda ifadesi yerleştirin ve bağımsız değişkenler lambda ifadesi tanımladığınızdan emin olun:

```csharp
var distanceLambda = Expression.Lambda(
    distance,
    xParameter,
    yParameter);
```

Daha karmaşık Bu örnekte, genellikle ifade ağaçları oluşturmanız gerekir birkaç daha fazla teknikleri bakın.

İlk olarak, kullanmadan önce parametreleri veya yerel değişkenler temsil eden nesneler oluşturmanız gerekir. Bu nesneler oluşturduktan sonra ihtiyaç duyduğunuz her yerde bunları, ifade ağacına kullanabilirsiniz.

İkinci olarak, bir alt kümesini yansıma API'ları oluşturmak için kullanılacak ihtiyacınız bir `MethodInfo` o yöntemi erişimi için bir ifade ağacına oluşturabilmesi için nesne. Kendiniz .NET Core platformda kullanılabilir yansıma API'leri alt sınırı, gerekir. Yeniden, bu teknikler diğer ifade ağaçları uzatır.

## <a name="building-code-in-depth"></a>Yapı kod derinliği:

Şunları yapabilirsiniz sınırlı değil bu API'leri kullanarak oluşturun. Ancak, daha fazla kod okumak için ve yönetmek için zordur, oluşturmak istediğiniz ifade ağacına karmaşık. 

Şimdi bu kodu eşdeğerdir bir ifade ağacına oluşturun:

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

Yukarıdaki ı ifade ağacına, ancak yalnızca temsilci yapı değil dikkat edin. Kullanarak `Expression` sınıfı, deyimi Lambda'lar oluşturamaz. Aynı işlevselliği oluşturmak için gerekli kod aşağıdaki gibidir. Derleme için bir API değil gerçeğiyle karmaşık bir `while` döngü, bunun yerine koşullu test ve dışında döngüsünü kesmek için bir etiket hedef içeren bir döngü yapı vermeniz gerekir. 

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

Daha karmaşık, ifade ağacına Faktöriyel işlevi için yapı için kodu oldukça biraz daha uzun ve etiketleri ve sonu deyimleri ve diğer öğeleri önlemek için görevler kodlama bizim her gün içinde isteriz ile riddled. 

Bu bölümde, t her düğüm bu ifade ağacına ziyaret edin ve bu örnekte oluşturulan düğümleri hakkında bilgi yazmak için ziyaretçi kod güncelleştirdik. Yapabilecekleriniz [görüntülemek veya karşıdan örnek kod](https://github.com/dotnet/samples/tree/master/csharp/expression-trees) dotnet/belgeler GitHub deposunda. Kendiniz oluşturmak ve örnekleri çalıştırmak denemeler yapın. Yükleme yönergeleri için bkz: [örnekler ve öğreticiler](../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="examining-the-apis"></a>API'ler inceleniyor

İfade ağacına API'leri .NET Core gitmek daha zor bazıları, ancak sorun yoktur. Bunların amaçla yerine karmaşık bir iş değil: çalışma zamanında kod oluşturur kod yazma. Bunlar, mutlaka C# dilinde kullanılabilir tüm denetim yapıları destekleme ve API'ın yüzey alanını olabildiğince küçük makul tutma arasında bir denge sağlamak karmaşıktır. Bu Bakiye birçok denetim yapıları kendi C# yapılarını tarafından değil, ancak bu daha yüksek düzeyli yapıları derleyici oluşturur temel mantığını temsil eden yapılar tarafından temsil edilen anlamına gelir. 

Ayrıca, şu anda vardır kullanarak doğrudan oluşturulamıyor C# ifadeleri `Expression` sınıfı yöntemlerinin. Genel olarak, bu yeni işleçler ve ifadeler C# 5 ve C# 6'da eklenmiş olacaktır. (Örneğin, `async` ifadeleri yerleşik olamaz ve yeni `?.` işleci doğrudan oluşturulamıyor.)

[Sonraki--İfadeleri çevirme](expression-trees-translating.md)
