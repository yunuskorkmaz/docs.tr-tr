---
title: "İfade ağaçları çevirme"
description: "Bu ifade ağacına değiştirilmiş bir kopyasını oluşturulurken bir ifade ağacına her düğümünde ziyaret öğrenin."
keywords: .NET, .NET core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: b453c591-acc6-4e08-8175-97e5bc65958e
ms.openlocfilehash: 602a17591d27ebfd098516453b9028bca37ad5e3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="translating-expression-trees"></a>İfade ağaçları çevirme

[Önceki--Yapı ifadeleri](expression-trees-building.md)

Son Bu bölümde, bir ifade ağacına içindeki her düğüm bu ifade ağacına değiştirilmiş bir kopyasını oluşturulurken ziyaret etmek öğreneceksiniz. Bu iki önemli senaryolarda kullanacağınız tekniklerle aynıdır. İlk böylece başka bir ortama çevrilebilir bir ifade ağacına tarafından ifade algoritmaları anlamaktır. Oluşturuldu algoritması değiştirmek istediğinizde saniyedir. Bu günlük kaydı ekleyin, yöntem çağrıları durdurur ve bunları veya başka amaçlarla izlemek için olabilir.

## <a name="translating-is-visiting"></a>Çevirme ziyaret edin

Bir ifade ağacına çevrilemedi derleme kodu ne ağacındaki tüm düğümleri ziyaret etmek için gördünüz bir uzantısıdır. Bir ifade ağacına çevrilemedi, tüm düğümlere ziyaret edin ve bunları ziyaret ederken yeni ağacını oluşturun. Yeni ağaç özgün düğümleri veya ağacında yerleştirdiğiniz yeni düğümler başvurular içeriyor olabilir.

Bu eylem bir ifade ağacına ziyaret eden ve bazı değiştirme düğümlerle yeni bir ağaç oluşturarak görelim. Bu örnekte, tüm sabit şimdi on kez daha büyük bir sabit ile değiştirin.
Aksi takdirde, ifade ağacına sağlam bırakacağız. Sabit değer okuma ve yeni bir sabit ile değiştirerek yerine bu değiştirme çarpma gerçekleştiren sahip yeni bir düğüm sabit düğüm değiştirerek vermiyoruz.

Burada, sabit bir düğüm bulduktan sonra alt öğeleri olan özgün sabiti ve sabiti yeni bir çarpma düğüm oluşturun `10`:

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

Özgün düğüme ikame ile değiştirerek, yeni bir ağaç bizim değişiklikler içeren biçimlendirilmemiş. Biz, derleme ve değiştirilen ağaç yürütme doğrulayabilirsiniz.

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

Yeni bir ağacı oluşturma, varolan ağacında düğümlerin ziyaret ve yeni düğümler oluşturma ve bunları ağacına ekleyerek bir birleşimidir.

Bu örnek değişmez olan ifade ağaçları önemini gösterir. Yukarıda oluşturduğunuz yeni ağaç yeni oluşturulan düğümlerini ve mevcut ağaç düğümü bileşimi içerdiğine dikkat edin. Varolan ağacında düğümlerin değiştirdiğinden güvenli olmasıdır. Bu, önemli bellek verimliliği neden olabilir.
Aynı düğümlerine bir ağaç boyunca veya birden çok ifade ağaçları kullanılabilir. Düğümleri değiştirilemediği aynı düğüm olabilir her yeniden kendi gerekli.

## <a name="traversing-and-executing-an-addition"></a>Çapraz geçiş yapma ve ek yürütme

Şimdi bu toplama düğümlerin ağacı anlatılmaktadır ve sonucu hesaplar ikinci bir ziyaretçi oluşturarak doğrulayın. Şu ana kadar gördüğünüz vistor birkaç değişiklik yaparak bunu yapabilirsiniz. Bu yeni sürümde ziyaretçi ekleme işlemi bu noktaya kadar kısmi toplamını döndürür. Sabit bir ifade için yalnızca sabit ifadenin değerini olmasıdır. Bu ağaçlar geçiş sonra bir toplama ifadesi için sonuç sol ve sağ işlenen toplamıdır.

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

Oldukça biraz kod burada yoktur, ancak kavramları kullanılmalarını.
Bu kod derinliği ilk aramaya alt ziyaret eder. Sabit düğüm ile karşılaştığında ziyaretçi sabiti değerini döndürür. Ziyaretçi her iki alt ziyaret ettikten sonra bu alt alt ağacı için hesaplanan toplam hesaplanan. Ek düğüm artık kendi sum hesaplayabilirsiniz.
İfade ağacına tüm düğümlerin ziyaret sonra toplamı hesaplandıktan. Hata Ayıklayıcısı'ndaki örnek çalıştıran ve yürütme izleme yürütme izleyebilirsiniz.

İzleme düğümleri nasıl analiz ve toplamı travsersing tarafından nasıl hesaplanır daha kolay olalım ağacı. İzleme bilgilerinin oldukça bit içerir toplama yöntemi güncelleştirilmiş bir sürümünü şöyledir:

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

Aynı ifadeye çalıştıran aşağıdaki çıktısı verir:

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

İzleme çıkışı ve yukarıdaki kod izleyin. Nasıl kodu her düğüm ziyaret eder ve ağacıyla gider ve toplamını bulur toplamı hesaplar çıkışı iş olması gerekir.

Şimdi, Farklı Çalıştır tarafından verilen ifade ile bakalım `sum1`:

```csharp
Expression<Func<int> sum1 = () => 1 + (2 + (3 + 4));
```

Bu ifade inceleniyor gelen çıktısı şöyledir:

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

Son yanıt aynı olsa da, ağaç geçişi tamamen farklıdır. Ağaç önce yürütülen farklı işlem ile oluşturulan çünkü düğümlerin farklı bir sırayla seyahat.

## <a name="learning-more"></a>Daha fazla öğrenme

Bu örnek, küçük bir alt kümesine çapraz geçiş ve bir ifade ağacına tarafından temsil edilen algoritmaları yorumlamak için derleme kodu gösterir. İfade ağaçları başka bir diline çeviren bir genel amaçlı kitaplığı oluşturmak için gereken tüm iş tam bir tartışma için lütfen okuyun [bu seri](http://blogs.msdn.com/b/mattwar/archive/2008/11/18/linq-links.aspx) Matt Warren tarafından. Herhangi bir ifade ağacına bulabileceğiniz kod Çevir konusunda harika ayrıntıya gider.

I ifade ağaçları true gücünü şimdi gördüğünüz umuyoruz.
Kod kümesi inceleyin, bu kodu ister ve değiştirilen sürüm yürütme tüm değişiklikleri yapın. İfade ağaçları değişmez olduğundan, varolan ağaçları bileşenlerinin kullanarak yeni ağaçları oluşturabilirsiniz. Bu değiştirilmiş ifade ağaçları oluşturmak için gerekli bellek miktarını azaltır.

[Sonraki--Özetle](expression-trees-summary.md)
