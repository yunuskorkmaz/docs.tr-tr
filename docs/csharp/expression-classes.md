---
title: İfade Ağaçlarını Destekleyen Çerçeve Türleri
description: İfade ağaçlarını destekleyen çerçeve türleri, ifade ağaçları oluşturma ve ifade ağacı API 'Leri ile çalışmaya yönelik teknikler hakkında bilgi edinin.
ms.date: 06/20/2016
ms.assetid: e9c85021-0d36-48af-91b7-aaaa66f22654
ms.openlocfilehash: d11a13000019faf2ab5c35d41d48fa199e901d1c
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70925965"
---
# <a name="framework-types-supporting-expression-trees"></a>İfade Ağaçlarını Destekleyen Çerçeve Türleri

[Önceki--Ifade ağaçları açıklanıyor](expression-trees-explained.md)

.NET Core Framework 'te Ifade ağaçları ile çalışan sınıfların büyük bir listesi vardır.
Listenin tam listesini <xref:System.Linq.Expressions>görebilirsiniz.
Tam liste üzerinden çalıştırmak yerine, Framework sınıflarının nasıl tasarlandığını anlayalim.

Dil tasarımında, bir ifade bir değeri değerlendiren ve döndüren bir kod gövdesidir. İfadeler çok basit olabilir: sabit ifade `1` , 1 sabit değerini döndürür. Daha karmaşık olabilir: İfade `(-B + Math.Sqrt(B*B - 4 * A * C)) / (2 * A)` , ikinci dereceden bir denklem (denklemin bir çözüme sahip olduğu durumda) için bir kök döndürür.  

## <a name="it-all-starts-with-systemlinqexpression"></a>Hepsi System. LINQ. Expression ile başlar

İfade ağaçları ile çalışmanın karmaşıklıklarından biri, programlarda birçok yerde birçok farklı türde ifade geçerli olur. Atama ifadesi düşünün. Atamanın sağ tarafı sabit bir değer, bir değişken, bir yöntem çağrısı ifadesi veya başka bir değer olabilir. Bu dil esnekliği, bir ifade ağacında çapraz geçiş yaparken bir ağacın düğümleri içinde herhangi bir yerde birçok farklı ifade türüyle karşılaşacağınız anlamına gelir. Bu nedenle, temel ifade türüyle çalışabilmeniz için en kolay yöntem vardır. Ancak bazen daha fazla bilmeniz gerekir.
Taban ifade sınıfı bu amaç için `NodeType` bir özellik içeriyor.
Olası ifade türlerinin `ExpressionType` bir numaralandırması olan bir döndürür.
Düğümün türünü öğrendikten sonra, bu türe çevirebilirsiniz ve ifade düğümünün türünü bilmenin belirli eylemlerini gerçekleştirebilirsiniz. Belirli düğüm türlerini arayabilir ve ardından bu tür bir ifadenin belirli özellikleriyle çalışabilirsiniz.

Örneğin, bu kod bir değişken erişim ifadesi için bir değişkenin adını yazdırır. Düğüm türünü denetleme, sonra bir değişken erişim ifadesine atama ve ardından belirli bir ifade türünün özelliklerini denetleme alıştırması yaşıyorum:

```csharp
Expression<Func<int, int>> addFive = (num) => num + 5;

if (addFive.NodeType == ExpressionType.Lambda)
{
    var lambdaExp = (LambdaExpression)addFive;

    var parameter = lambdaExp.Parameters.First();

    Console.WriteLine(parameter.Name);
    Console.WriteLine(parameter.Type);
}
```

## <a name="creating-expression-trees"></a>Ifade ağaçları oluşturma

`System.Linq.Expression` Sınıfı ayrıca ifadeler oluşturmak için birçok statik yöntem içerir. Bu yöntemler, alt öğeleri için sağlanan bağımsız değişkenleri kullanarak bir ifade düğümü oluşturur. Bu şekilde, yaprak düğümlerinden bir ifade oluşturursunuz. Örneğin, bu kod bir ekleme ifadesi oluşturur:

```csharp
// Addition is an add expression for "1 + 2"
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
var addition = Expression.Add(one, two);
```

Bu basit örnekte, ifade ağaçları oluşturmak ve bunlarla çalışmak için birçok tür bulunduğunu görebilirsiniz. Bu karmaşıklık, C# dilin sağladığı zengin sözlük yeteneklerini sağlamak için gereklidir.

## <a name="navigating-the-apis"></a>API 'Lerde gezinme
C# Dilin sözdizimi öğelerinin neredeyse tamamına eşlenen ifade düğüm türleri vardır. Her türün bu tür dil öğesi için özel yöntemleri vardır. Tek seferde baş bir süre içinde tutulması çok önemlidir. Her şeyi yeniden denemeye çalışmak yerine, Ifade ağaçları ile çalışmak için kullandığım teknikler şunlardır:

1. Gözden geçirmeniz gereken olası düğümleri öğrenmek `ExpressionType` için numaralandırmanın üyelerine bakın. Bu aslında bir ifade ağacını geçmek ve anlamak istediğinizde yardımcı olur.
2. Bir ifade oluşturmak için `Expression` sınıfın statik üyelerine bakın. Bu yöntemler bir alt düğümleri kümesinden herhangi bir ifade türü oluşturabilir.
3. Değiştirilen bir ifade ağacı oluşturmak için sınıfınabakın.`ExpressionVisitor`

Bu üç alanın her birine baktığımızda daha fazla bilgi bulabilirsiniz. Bağımsız olarak, bu üç adımdan biriyle başladığınızda ne yapmanız gerektiğini öğreneceksiniz.
 
 [Sonraki--Ifade ağaçları yürütülüyor](expression-trees-execution.md)
