---
title: İfade Ağaçlarını Çevirme
description: Bu ifade ağacının değiştirilmiş bir kopyasını yaparken bir ifade ağacındaki her düğümü nasıl ziyaret edin.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: b453c591-acc6-4e08-8175-97e5bc65958e
ms.openlocfilehash: f60c447d5c89aa83f85073e642e621608131ed8d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76115784"
---
# <a name="translate-expression-trees"></a>İfade ağaçlarını çevir

[Önceki -- Yapı İfadeleri](expression-trees-building.md)

Bu son bölümde, bu ifade ağacının değiştirilmiş bir kopyasını yaparken bir ifade ağacındaki her düğümü nasıl ziyaret edeceğinizi öğreneceksiniz. Bunlar, iki önemli senaryoda kullanacağınız tekniklerdir. Birincisi, bir ifade ağacı tarafından ifade edilen algoritmaları anlamak, böylece başka bir ortama çevrilebilir. İkincisi, oluşturulan algoritmayı değiştirmek istediğiniz dedir. Bu, günlüğe kaydetme, yöntem aramalarını engellemek ve bunları izlemek veya başka amaçlar eklemek olabilir.

## <a name="translating-is-visiting"></a>Tercüme Etmek Ziyaret Etmektir

İfade ağacını çevirmek için oluşturduğunuz kod, ağaçtaki tüm düğümleri ziyaret etmek için gördüğünüz şeyin bir uzantısıdır. Bir ifade ağacını çevirdiğinizde, tüm düğümleri ziyaret edeyim ve onları ziyaret ederken yeni ağaç oluşturursunuz. Yeni ağaç, özgün düğümlere veya ağaca yerleştirdiğiniz yeni düğümlere başvurular içerebilir.

Bir ifade ağacını ziyaret ederek ve bazı değiştirme düğümleri ile yeni bir ağaç oluşturarak bunu iş başında görelim. Bu örnekte, herhangi bir sabiti on kat daha büyük bir sabitle değiştirelim.
Aksi takdirde, ifade ağacını sağlam bırakırız. Sabitin değerini okumak ve yeni bir sabitle değiştirmek yerine, sabit düğümü çarpma işlemini gerçekleştiren yeni bir düğümle değiştirerek bu değişikliği yapacağız.

Burada, sabit bir düğüm bulduğunuzda, çocukları orijinal sabit olan yeni bir çarpma `10`düğümü oluşturursunuz ve sabit:

```csharp
private static Expression ReplaceNodes(Expression original)
{
    if (original.NodeType == ExpressionType.Constant)
    {
        return Expression.Multiply(original, Expression.Constant(10));
    }
    else if (original.NodeType == ExpressionType.Add)
    {
        var binaryExpression = (BinaryExpression)original;
        return Expression.Add(
            ReplaceNodes(binaryExpression.Left),
            ReplaceNodes(binaryExpression.Right));
    }
    return original;
}
```

Orijinal düğümü yedekle değiştirerek, modifikasyonlarımızı içeren yeni bir ağaç oluşturulur. Değiştirilen ağacı derleyip çalıştırarak bunu doğrulayabiliriz.

```csharp
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
var addition = Expression.Add(one, two);
var sum = ReplaceNodes(addition);
var executableFunc = Expression.Lambda(sum);

var func = (Func<int>)executableFunc.Compile();
var answer = func();
Console.WriteLine(answer);
```

Yeni bir ağaç oluşturmak, varolan ağaçtaki düğümleri ziyaret etmenin ve yeni düğümler oluşturmanın ve bunları ağaca eklemenin bir kombinasyonudur.

Bu örnek, ifade ağaçlarının değişmez olmasının önemini göstermektedir. Yukarıda oluşturulan yeni ağacın yeni oluşturulan düğümlerin ve varolan ağaçtan düğümlerin bir karışımını içerdiğine dikkat edin. Bu güvenlidir, çünkü varolan ağaçtaki düğümler değiştirilemez. Bu önemli bellek verimliliği neden olabilir.
Aynı düğümler bir ağaç boyunca veya birden çok ifade ağacında kullanılabilir. Düğümler değiştirilemediğinden, aynı düğüm gerektiğinde yeniden kullanılabilir.

## <a name="traversing-and-executing-an-addition"></a>Bir Eklemeyi Geçiş ve Yürütme

Bunu, ek düğümler ağacında yürüyen ve sonucu hesaplayan ikinci bir ziyaretçi oluşturarak doğrulayalım. Bunu, şimdiye kadar gördüğünüz ziyaretçiiçin birkaç değişiklik yaparak yapabilirsiniz. Bu yeni sürümde, ziyaretçi ekleme işleminin kısmi toplamını bu noktaya kadar döndürecektir. Sabit bir ifade için, bu sadece sabit ifadenin değeridir. Ek bir ifade için, sonuç, bu ağaçlar geçildikten sonra, sol ve sağ operands toplamıdır.

```csharp
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
var three= Expression.Constant(3, typeof(int));
var four = Expression.Constant(4, typeof(int));
var addition = Expression.Add(one, two);
var add2 = Expression.Add(three, four);
var sum = Expression.Add(addition, add2);

// Declare the delegate, so we can call it
// from itself recursively:
Func<Expression, int> aggregate = null;
// Aggregate, return constants, or the sum of the left and right operand.
// Major simplification: Assume every binary expression is an addition.
aggregate = (exp) =>
    exp.NodeType == ExpressionType.Constant ?
    (int)((ConstantExpression)exp).Value :
    aggregate(((BinaryExpression)exp).Left) + aggregate(((BinaryExpression)exp).Right);

var theSum = aggregate(sum);
Console.WriteLine(theSum);
```

Burada biraz kod var, ama kavramlar çok yaklaşılabilir.
Bu kod, derinlemesine ilk aramada çocukları ziyaret eder. Sabit bir düğümle karşılaştığında, ziyaretçi sabitin değerini döndürür. Ziyaretçi her iki çocuğu da ziyaret ettikten sonra, bu çocuklar bu alt ağaç için hesaplanan toplamı hesaplamış olacaklar. Ek düğüm artık toplamını hesaplayabilir.
İfade ağacındaki tüm düğümler ziyaret edildikten sonra, toplam hesaplanmış olur. Örneği hata ayıklamada çalıştırarak ve yürütmeyi izleyerek yürütmeyi izleyebilirsiniz.

Düğümlerin nasıl analiz edildiğini ve ağacın geçişiyle toplamın nasıl hesaplandırılanını izlemeyi kolaylaştıralım. Aşağıda, agrega yönteminin oldukça fazla izleme bilgisi içeren güncelleştirilmiş bir sürümü verem:

```csharp
private static int Aggregate(Expression exp)
{
    if (exp.NodeType == ExpressionType.Constant)
    {
        var constantExp = (ConstantExpression)exp;
        Console.Error.WriteLine($"Found Constant: {constantExp.Value}");
        return (int)constantExp.Value;
    }
    else if (exp.NodeType == ExpressionType.Add)
    {
        var addExp = (BinaryExpression)exp;
        Console.Error.WriteLine("Found Addition Expression");
        Console.Error.WriteLine("Computing Left node");
        var leftOperand = Aggregate(addExp.Left);
        Console.Error.WriteLine($"Left is: {leftOperand}");
        Console.Error.WriteLine("Computing Right node");
        var rightOperand = Aggregate(addExp.Right);
        Console.Error.WriteLine($"Right is: {rightOperand}");
        var sum = leftOperand + rightOperand;
        Console.Error.WriteLine($"Computed sum: {sum}");
        return sum;
    }
    else throw new NotSupportedException("Haven't written this yet");
}
```

Aynı ifade üzerinde çalıştırmak aşağıdaki çıktıyı verir:

```output
10
Found Addition Expression
Computing Left node
Found Addition Expression
Computing Left node
Found Constant: 1
Left is: 1
Computing Right node
Found Constant: 2
Right is: 2
Computed sum: 3
Left is: 3
Computing Right node
Found Addition Expression
Computing Left node
Found Constant: 3
Left is: 3
Computing Right node
Found Constant: 4
Right is: 4
Computed sum: 7
Right is: 7
Computed sum: 10
10
```

Çıktıyı izleyin ve yukarıdaki kodda izleyin. Kodun her düğümü nasıl ziyaret ettiğinizi ve ağaçtan geçerken toplamı nasıl hesaplayabilmelisinizi ve toplamı nasıl bulduğunu öğrenebilirsiniz.

Şimdi, farklı bir çalışma bakalım, ifade ile: `sum1`

```csharp
Expression<Func<int> sum1 = () => 1 + (2 + (3 + 4));
```

Bu ifadeyi incelemenin çıktısı aşağıda verebisi aşağıda veda edebilirsiniz:

```output
Found Addition Expression
Computing Left node
Found Constant: 1
Left is: 1
Computing Right node
Found Addition Expression
Computing Left node
Found Constant: 2
Left is: 2
Computing Right node
Found Addition Expression
Computing Left node
Found Constant: 3
Left is: 3
Computing Right node
Found Constant: 4
Right is: 4
Computed sum: 7
Right is: 7
Computed sum: 9
Right is: 9
Computed sum: 10
10
```

Son yanıt aynı olsa da, ağaç geçişi tamamen farklıdır. Ağaç ilk meydana gelen farklı işlemler ile inşa edildi, çünkü düğümleri farklı bir sırada seyahat edilir.

## <a name="learning-more"></a>Daha Fazla Bilgi

Bu örnek, bir ifade ağacı tarafından temsil edilen algoritmaları geçiş ve yorumlamak için oluşturacağınız kodun küçük bir alt kümesini gösterir. İfade ağaçlarını başka bir dile çeviren genel amaçlı bir kütüphane oluşturmak için gereken tüm çalışmaların tam bir tartışması için lütfen Matt Warren'ın [bu dizisini](https://docs.microsoft.com/archive/blogs/mattwar/linq-building-an-iqueryable-provider-series) okuyun. Bir ifade ağacında bulabileceğiniz kodlardan herhangi birinin nasıl çevrilebileceği hakkında ayrıntılı bilgi edinilir.

Umarım ifade ağaçlarının gerçek gücünü görmüşsunuzdur.
Bir kod kümesini inceleyebilir, bu kodda istediğiniz değişiklikleri yapabilir ve değiştirilen sürümü çalıştırabilirsiniz. İfade ağaçları değişmez olduğundan, varolan ağaçların bileşenlerini kullanarak yeni ağaçlar oluşturabilirsiniz. Bu, değiştirilmiş ifade ağaçları oluşturmak için gereken bellek miktarını en aza indirir.

[Sonraki -- Özetleme](expression-trees-summary.md)
