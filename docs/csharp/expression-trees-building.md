---
title: Ifade ağaçları oluşturma
description: İfade ağaçları oluşturma teknikleri hakkında bilgi edinin.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: 542754a9-7f40-4293-b299-b9f80241902c
ms.openlocfilehash: 45628b00633c8d6ff51dbd5f5dbdda7ca25dd7c4
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73037101"
---
# <a name="building-expression-trees"></a>Ifade ağaçları oluşturma

[Önceki--Ifadeleri yorumlama](expression-trees-interpreting.md)

Şimdiye kadar gördüğünüz tüm ifade ağaçları C# derleyici tarafından oluşturulmuştur. Tek yapmanız gereken, `Expression<Func<T>>` veya benzer bir tür olarak yazılmış bir değişkene atanan bir lambda ifadesi oluşturmaktır. Bu, bir ifade ağacı oluşturmanın tek yolu değildir. Birçok senaryoda, çalışma zamanında bellekte bir ifade oluşturmanız gerektiğini fark edebilirsiniz. 

Ifade ağaçları oluşturma, bu ifade ağaçlarının sabit olması olgusuna göre karmaşıktır. Sabit olması, ağacın köke kadar olan yaprakları oluşturmanız gerektiği anlamına gelir. İfade ağaçları oluşturmak için kullanacağınız API 'Ler bu olguyu yansıtır: bir düğüm oluşturmak için kullanacağınız Yöntemler tüm alt öğelerini bağımsız değişken olarak alır. Aşağıda, teknikleri göstermek için birkaç örnek yürülim.

## <a name="creating-nodes"></a>Düğüm oluşturma

Yine de nispeten daha başlayalım. Bu bölümlerin tamamında üzerinde çalıştık ekleme ifadesini kullanacağız:

```csharp
Expression<Func<int>> sum = () => 1 + 2;
```

Bu ifade ağacını oluşturmak için yaprak düğümleri oluşturmanız gerekir.
Yaprak düğümler sabittir, bu sayede düğümleri oluşturmak için `Expression.Constant` yöntemini kullanabilirsiniz:

```csharp
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
```

Daha sonra, toplama ifadesi oluşturacaksınız:

```csharp
var addition = Expression.Add(one, two);
```

Toplama ifadesini aldıktan sonra lambda ifadesini oluşturabilirsiniz:

```csharp
var lambda = Expression.Lambda(addition);
```

Bağımsız değişken içermediğinden bu çok basit bir lambda ifadesidir.
Bu bölümde daha sonra, bağımsız değişkenlerin parametrelere nasıl eşlendiğini ve daha karmaşık ifadeler nasıl oluşturulacağını öğreneceksiniz.

Bu kadar basit olan ifadeler için tüm çağrıları tek bir deyim halinde birleştirebilirsiniz:

```csharp
var lambda = Expression.Lambda(
    Expression.Add(
        Expression.Constant(1, typeof(int)),
        Expression.Constant(2, typeof(int))
    )
);
```

## <a name="building-a-tree"></a>Ağaç oluşturma

Bu, bellekte bir ifade ağacı oluşturmanın temel larıdır. Daha karmaşık ağaçlar genellikle daha fazla düğüm türü ve ağaçta daha fazla düğüm anlamına gelir. Daha sonra bir örnek daha çalıştıralım ve genellikle ifade ağaçları oluştururken oluşturacağınız iki düğüm türü gösterelim: bağımsız değişken düğümleri ve yöntem çağrı düğümleri.

Bu ifadeyi oluşturmak için bir ifade ağacı oluşturalım:

```csharp
Expression<Func<double, double, double>> distanceCalc =
    (x, y) => Math.Sqrt(x * x + y * y);
```
 
`x` ve `y`için parametre ifadeleri oluşturarak başlayacaksınız:

```csharp
var xParameter = Expression.Parameter(typeof(double), "x");
var yParameter = Expression.Parameter(typeof(double), "y");
```

Çarpma ve ekleme ifadelerinin oluşturulması, zaten gördüğünüz kalıbı izler:

```csharp
var xSquared = Expression.Multiply(xParameter, xParameter);
var ySquared = Expression.Multiply(yParameter, yParameter);
var sum = Expression.Add(xSquared, ySquared);
```

Sonra, `Math.Sqrt`çağrısı için bir yöntem çağrısı ifadesi oluşturmanız gerekir.

```csharp
var sqrtMethod = typeof(Math).GetMethod("Sqrt", new[] { typeof(double) });
var distance = Expression.Call(sqrtMethod, sum);
```

Son olarak, yöntem çağrısını bir lambda ifadesine yerleştirir ve lambda ifadesinin bağımsız değişkenlerini tanımladığınızdan emin olun:

```csharp
var distanceLambda = Expression.Lambda(
    distance,
    xParameter,
    yParameter);
```

Bu daha karmaşık örnekte, genellikle ifade ağaçları oluşturmanız için gereken birkaç teknik görürsünüz.

İlk olarak, parametreleri veya yerel değişkenleri kullanmadan önce bunları temsil eden nesneleri oluşturmanız gerekir. Bu nesneleri oluşturduktan sonra, bunları, ihtiyacınız olan her yerde ifade ağacınızdaki bir şekilde kullanabilirsiniz.

İkinci olarak, bir `MethodInfo` nesnesi oluşturmak için yansıma API 'lerinin bir alt kümesini kullanmanız gerekir; böylece bu yönteme erişmek için bir ifade ağacı oluşturabilirsiniz. Kendinizi .NET Core platformunda bulunan yansıma API 'Lerinin alt kümesiyle sınırlandırmalısınız. Bu teknikler yine de diğer ifade ağaçlarına genişletilir.

## <a name="building-code-in-depth"></a>Derinlemesine kod derleme

Bu API 'Leri kullanarak neleri oluşturabileceğiniz sınırlı değilsiniz. Ancak, derlemek istediğiniz daha karmaşık ifade ağacı, kodun yönetilmesi ve okunması daha zordur. 

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

Yukarıda, ifade ağacını oluşturamadım, ancak yalnızca temsilciyi temsil ediyorum. `Expression` sınıfını kullanarak, ifade lambdaları derleyebilirsiniz. Aynı işlevselliği oluşturmak için gereken kod aşağıda verilmiştir. `while` döngüsünü derlemek için bir API olmadığından, koşullu bir test içeren bir döngü ve döngünün dışına bölmek için bir etiket hedefi oluşturmanız gerekir. 

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

Çarpınımı işlevi için ifade ağacını oluşturmaya yönelik kod çok daha uzun, daha karmaşıktır ve Etiketler ve break deyimleri ve günlük kodlama görevlerimizde kaçınmak istiyoruz. 

Bu bölüm için, ziyaretçi kodunu bu ifade ağacındaki her düğümü ziyaret etmek ve bu örnekte oluşturulan düğümlerle ilgili bilgileri yazmak için güncelleştirdim. Örnek kodu DotNet/docs GitHub deposunda [görüntüleyebilir veya indirebilirsiniz](https://github.com/dotnet/samples/tree/master/csharp/expression-trees) . Örnekleri oluşturup çalıştırarak kendiniz için denemeler yapın. İndirme yönergeleri için bkz. [örnekler ve öğreticiler](../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="examining-the-apis"></a>API 'Leri İnceleme

İfade ağacı API 'Leri, .NET Core 'ta gezinmek daha zordur, ancak bu kadar iyidir. Amaçları, karmaşık bir yetersiz alma: çalışma zamanında kod üreten kod yazma. Bu C# diller, dilde kullanılabilen tüm denetim yapılarını destekleme ve API 'lerin yüzey alanını makul şekilde küçük tutarak bir denge sağlamak için karmaşıktır. Bu Bakiye, birçok denetim yapısının C# yapılarına göre değil, ancak derleyicinin bu üst düzey yapıların oluşturduğu temel mantığı temsil eden yapılar tarafından temsil edildiği anlamına gelir. 

Ayrıca, şu anda`Expression`sınıf yöntemleri kullanılarak C# doğrudan derlenemez ifadeler vardır. Genel olarak, bunlar 5 ve C# C# 6 ' da eklenen en yeni işleçler ve ifadeler olacaktır. (Örneğin, `async` ifadeleri derlenemez ve yeni `?.` işleci doğrudan oluşturulamaz.)

[İleri--Ifadeleri çevirme](expression-trees-translating.md)
