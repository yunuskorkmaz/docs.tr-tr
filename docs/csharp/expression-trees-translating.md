---
title: Ifade ağaçları çevriliyor
description: Bu ifade ağacının değiştirilmiş bir kopyasını oluştururken bir ifade ağacındaki her bir düğümü ziyaret etmeyi öğrenin.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: b453c591-acc6-4e08-8175-97e5bc65958e
ms.openlocfilehash: cb64e79d915a5c5567d5a3d25f1d747df9687c87
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90537469"
---
# <a name="translate-expression-trees"></a>İfade ağaçlarını çevir

[Previous--Ifadeleri derleme](expression-trees-building.md)

Bu son bölümde, bu ifade ağacının değiştirilmiş bir kopyasını oluştururken bir ifade ağacındaki her bir düğümü ziyaret etmeyi öğreneceksiniz. Bunlar, iki önemli senaryoda kullanacağınız tekniklerdir. Birincisi, başka bir ortama çevrilebilmesi için bir ifade ağacı tarafından ifade edilen algoritmaları anlamaktır. İkincisi, oluşturulan algoritmayı değiştirmek istediğinizde olur. Bu, günlük kaydı eklemek, Yöntem çağrılarını ele almak ve izlemek ya da başka amaçlar olabilir.

## <a name="translating-is-visiting"></a>Çeviri ziyaret ediyor

Bir ifade ağacını çevirmek için oluşturduğunuz kod, bir ağaçtaki tüm düğümleri ziyaret etmek için zaten gördüğünüze ait bir uzantıdır. Bir ifade ağacını çevirirken, tüm düğümleri ziyaret edersiniz ve ziyaret edilirken yeni ağacı derleyebilirsiniz. Yeni ağaç orijinal düğümlere veya ağaca yerleştirdiğiniz yeni düğümlere başvuru içerebilir.

Bu işlemi, bir ifade ağacını ziyaret ederek ve değişiklik düğümleri içeren yeni bir ağaç oluşturarak görelim. Bu örnekte, her sabiti on kat daha büyük olan bir sabit ile değiştirin.
Aksi takdirde, ifade ağacını bozulmadan bırakıyoruz. Sabitin değerini okumak ve yeni bir sabitle değiştirmek yerine, sabit düğümü çarpma işlemini gerçekleştiren yeni bir düğümle değiştirerek bu değişikliği yapacağız.

Burada, sabit bir düğüm bulduktan sonra, alt öğeleri orijinal sabitine ve sabitine sahip yeni bir çarpma düğümü oluşturursunuz `10` :

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

Özgün düğümü yenisiyle değiştirerek, değişikliklerinizi içeren yeni bir ağaç oluşturulur. Değiştirilmiş ağacı derleyip yürüterek bunu doğrulayabiliriz.

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

Yeni bir ağaç oluşturmak, var olan ağaçtaki düğümleri ziyaret etme ve yeni düğümler oluşturma ve bunları ağaca ekleme birleşimidir.

Bu örnek, ifade ağaçlarının sabit olmasının önemini gösterir. Yukarıda oluşturulan yeni ağacın yeni oluşturulan düğümlerin bir karışımını ve var olan ağaçtaki düğümleri içerdiğini unutmayın. Bu, var olan ağaçtaki düğümler değiştirilemediği için güvenlidir. Bu, önemli ölçüde bellek verimliliklerini sağlayabilir.
Aynı düğümler bir ağacın tamamında veya birden çok ifade ağacında kullanılabilir. Düğümler değiştirilemediğinden, her gerektiğinde aynı düğüm yeniden kullanılabilir.

## <a name="traversing-and-executing-an-addition"></a>Çapraz geçiş ve yürütme

Ayrıca, ek düğüm ağacını gösteren ve sonucu hesaplayan ikinci bir ziyaretçi oluşturarak bunu doğrulayalım. Şimdiye kadar gördüğünüz ziyaretçi üzerinde birkaç değişiklik yaparak bunu yapabilirsiniz. Bu yeni sürümde ziyaretçi, toplama işleminin kısmi toplamını bu noktaya kadar döndürür. Sabit bir ifade için yalnızca sabit ifadenin değeridir. Bir toplama ifadesi için, bu ağaçlar alındıktan sonra, sonuç sol ve sağ işlenenlerinin toplamıdır.

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

Burada bir kod biraz daha vardır ancak kavramlar çok ulaşılabilir.
Bu kod, alt öğeleri derinlemesine bir ilk aramada ziyaret ediyor. Sabit bir düğümle karşılaştığında, ziyaretçi sabit değeri döndürür. Ziyaretçi iki alt öğeyi ziyaret ettikten sonra bu alt ağaç için hesaplanan toplamı hesaplamıştır. Toplama düğümü artık toplamını hesaplaedebilir.
İfade ağacındaki tüm düğümler ziyaret edildikten sonra toplam hesaplanır. Örneği hata ayıklayıcıda çalıştırıp yürütmeyi izleyerek yürütmeyi izleyebilirsiniz.

Düğümlerin nasıl çözümlenmekte olduğunu ve ağacın çapraz geçiş yaparak nasıl hesaplantığını izlemeyi daha kolay hale getirir. Toplam yönteminin, tam olarak bir izleme bilgisi içeren güncelleştirilmiş bir sürümü aşağıda verilmiştir:

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

Aynı ifadede çalıştırmak aşağıdaki çıktıyı verir:

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

Çıktıyı izleyin ve yukarıdaki kodda izleyin. Kodun her bir düğümü nasıl ziyaret edebilmeli ve toplam ağaçta gezinilerek toplamı nasıl hesapladığını ve toplamı bulabileceksiniz.

Şimdi, tarafından verilen ifadeyle farklı bir çalıştırmaya bakalım `sum1` :

```csharp
Expression<Func<int> sum1 = () => 1 + (2 + (3 + 4));
```

Bu ifadeyi inceleyerek çıkış şu şekildedir:

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

Nihai yanıt aynı olsa da, ağaç geçişi tamamen farklıdır. Ağaç, ilk olarak oluşan farklı işlemlerle oluşturulduğundan, bu düğümler farklı bir sıraya göre yapılır.

## <a name="learning-more"></a>Daha Fazla Bilgi

Bu örnek, bir ifade ağacı tarafından temsil edilen algoritmaları çapraz olarak geçirmek ve yorumlamak için derleyerek kodun küçük bir alt kümesini gösterir. İfade ağaçlarını başka bir dile çeviren genel amaçlı bir kitaplık oluşturmak için gereken tüm çalışmalar hakkında ayrıntılı bir açıklama için lütfen [Bu seriyi](/archive/blogs/mattwar/linq-building-an-iqueryable-provider-series) Matt Warren ile okuyun. Bir ifade ağacında bulabileceğiniz herhangi bir kodun nasıl çevrilebileceğini gösteren harika bir ayrıntıya gider.

Artık ifade ağaçlarının gerçek gücünü gördük.
Bir kod kümesini inceleyebilir, bu koda istediğiniz değişiklikleri yapabilir ve değiştirilen sürümü yürütebilirsiniz. İfade ağaçları sabit olduğundan, varolan ağaçların bileşenlerini kullanarak yeni ağaçlar oluşturabilirsiniz. Bu, değiştirilen ifade ağaçları oluşturmak için gereken bellek miktarını en aza indirir.

[İleri--toplam](expression-trees-summary.md)
