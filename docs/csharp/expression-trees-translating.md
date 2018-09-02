---
title: İfade ağaçları çevirme
description: Bu ifade ağacını değiştirilmiş bir kopyasını oluşturulurken bir ifade ağacı içindeki her bir düğümün ziyaret öğrenin.
ms.date: 06/20/2016
ms.assetid: b453c591-acc6-4e08-8175-97e5bc65958e
ms.openlocfilehash: bd4aec2ef34e4dc972ae867c6b5070f92dcbc498
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43463729"
---
# <a name="translating-expression-trees"></a>İfade ağaçları çevirme

[Önceki--İfade derleme](expression-trees-building.md)

Bu son bölümde her bir ifade ağacı düğümünde Bu ifade ağacını değiştirilmiş bir kopyasını oluşturulurken ziyaret öğreneceksiniz. Bu iki önemli senaryoda kullanacağınız tekniklerdir. İlk, böylece başka bir ortama çevrilebilir bir ifade ağacı tarafından ifade algoritmaları öğrenmektir. Oluşturulmuş algoritma değiştirmek istediğinizde saniyedir. Bu günlük, yöntem çağrılarını ıntercept ekleyip bunları veya başka amaçlarla izlemek olabilir.

## <a name="translating-is-visiting"></a>Çevirme ziyaret edin

Bir ifade ağacına çevrilemedi derleme kodu ne zaten bir ağaçtaki tüm düğümleri ziyaret etmek için gördüğünüz bir uzantısıdır. Bir ifade ağacı Çevir, tüm düğümleri ziyaret edin ve bunları ziyaret ederken, yeni bir ağaç oluşturun. Yeni ağaç özgün düğümleri veya ağacında yerleştirmiş olduğunuz yeni düğümler içerebilir.

Bu eylem bir ifade ağacı ziyaret ve bazı değiştirme düğümlerle yeni bir ağaç oluşturma görelim. Bu örnekte, tüm sabiti şimdi on kat daha büyük bir sabit ile değiştirin.
Aksi takdirde, ifade ağacına değiştirmeden bırakacağız. Sabit değerini okumak ve yeni bir sabit ile değiştirerek yerine bu değiştirme sabit düğüm çarpma işlemi gerçekleştiren yeni bir düğüm ile değiştirerek oluşturacağız.

Sabit düğüm bulduğunuzda, burada, orijinal sabit ve sabit alt öğeleri olan yeni bir çarpma düğüm oluşturma `10`:

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

Özgün düğüme yedekle değiştirerek yeni bir ağaç yapacağımız değişiklikler burada sona içeren oluşturulur. Biz, derleme ve değiştirilen ağaç yürütme doğrulayabilirsiniz.

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

Yeni bir ağaç oluşturmak mevcut Ağaçtaki düğümler ziyaret yeni düğümler oluşturma ve bunları ağacına ekleyerek bir birleşimidir.

Bu örnek, sabit olan ifade ağaçları önemini gösterir. Yukarıda oluşturulan yeni ağaç yeni oluşturulan düğümleri ve mevcut ağaç düğümleri bir karışımını içerdiğine dikkat edin. Mevcut Ağaçtaki düğümler değiştirilemediğinden güvenli olmasıdır. Bu, önemli bellek sanayi neden olabilir.
Aynı düğüm bir ağaç boyunca veya birden fazla ifade ağaçları kullanılabilir. Düğümleri değiştirilemediğinden aynı düğümde olabilir herhangi bir zamanda yeniden kendi gerekli.

## <a name="traversing-and-executing-an-addition"></a>Geçiş ve ek yürütülüyor

Bu ek düğüm ağacı gezer ve sonucu hesaplar ikinci bir ziyaretçi oluşturarak doğrulayalım. Şu ana kadar gördüğünüz vistor birkaç değişiklik yaparak bunu yapabilirsiniz. Bu yeni sürümde ziyaretçi toplama işlemi bu noktaya kadar kısmi toplamını döndürür. Sabit bir ifade için yalnızca sabit ifadenin değeri olmasıdır. Ağaçların geçiş sonra bir toplama ifadesi sonucu sol ve sağ işlenen toplamıdır.

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

Kodu buraya olayın yoktur ancak kullanılmalarını kavramlardır.
Bu kod, alt derinliği ilk aramada ziyaret eder. Sabit düğüm karşılaştığında, ziyaretçi sabit değerini döndürür. Ziyaretçi her iki alt öğe ziyaret ettikten sonra alt alt ağacı için hesaplanan toplamı hesaplanan. Ayrıca düğüm artık, sum hesaplayabilirsiniz.
İfade ağacı tüm düğümlerin ziyaret sonra toplamı hesaplanan. Örnek hata ayıklayıcıda çalıştırma ve izleme yürütme yürütme izleyebilirsiniz.

İzleme düğümleri nasıl analiz edilir ve toplamı travsersing tarafından nasıl hesaplanır daha kolay olalım ağaç. Olayın izleme bilgilerini içeren bir toplama yöntemi güncelleştirilmiş bir sürümünü şu şekildedir:

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

Aynı ifadeye çalışan aşağıdaki çıktıyı oluşturur:

```
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

İzleme çıkışı ve yukarıdaki kod örneği takip etmek. Nasıl kod her düğüm ziyaret eder ve ağaç geçer ve toplamı bulur toplamı hesaplar out çalışabilmek için olmalıdır.

Şimdi, farklı bir çalışma zamanında tarafından verilen ifadeyle bakalım `sum1`:

```csharp
Expression<Func<int> sum1 = () => 1 + (2 + (3 + 4));
```

Bu ifade İnceleme gelen çıktısı aşağıdaki gibidir:

```
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

Son yanıt aynı olsa da, ağaç geçişi tamamen farklıdır. Ağaç önce gerçekleşen farklı işlemler ile oluşturulmuş olduğundan düğümler farklı bir sırada imkansız.

## <a name="learning-more"></a>Daha fazla öğrenme

Bu örnek, geçiş ve bir ifade ağacı tarafından temsil edilen algoritmaları yorumlamak için derleme kodu küçük bir kısmı gösterir. İfade ağaçları başka bir dile çevirir bir genel amaçlı kitaplık oluşturmak için gereken tüm iş tam bir açıklaması için lütfen okuyun [Bu seriyi](https://blogs.msdn.com/b/mattwar/archive/2008/11/18/linq-links.aspx) Matt Warren tarafından. Herhangi bir ifade ağacı içinde bulabileceğiniz kod çevirme konusunda harika ayrıntıya gider.

Umarım ifade ağaçları'nın gerçek gücünü artık gördünüz.
Bir dizi kodla incelemek, bu kodu ister ve değiştirilen sürüm yürütme herhangi bir değişiklik yapın. İfade ağaçları sabit olduğundan, mevcut ağaçları bileşenlerini kullanarak yeni ağaçları oluşturabilirsiniz. Bu, değiştirilmiş bir ifade ağacı oluşturmak için gerekli bellek miktarını en aza indirir.

[Sonraki--Özetle](expression-trees-summary.md)
