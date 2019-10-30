---
title: İfade Ağaçlarını Destekleyen Çerçeve Türleri
description: İfade ağaçlarını destekleyen çerçeve türleri, ifade ağaçları oluşturma ve ifade ağacı API 'Leri ile çalışmaya yönelik teknikler hakkında bilgi edinin.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: e9c85021-0d36-48af-91b7-aaaa66f22654
ms.openlocfilehash: 157e97594f27345ac96fe91f7dd6f29907c2c7ac
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73037615"
---
# <a name="framework-types-supporting-expression-trees"></a>İfade Ağaçlarını Destekleyen Çerçeve Türleri

[Önceki--Ifade ağaçları açıklanıyor](expression-trees-explained.md)

.NET Core Framework 'te Ifade ağaçları ile çalışan sınıfların büyük bir listesi vardır.
<xref:System.Linq.Expressions>listenin tam listesini görebilirsiniz.
Tam liste üzerinden çalıştırmak yerine, Framework sınıflarının nasıl tasarlandığını anlayalim.

Dil tasarımında, bir ifade bir değeri değerlendiren ve döndüren bir kod gövdesidir. İfadeler çok basit olabilir: `1` sabit ifade, 1 sabit değerini döndürür. Daha karmaşık olabilir: ifade `(-B + Math.Sqrt(B*B - 4 * A * C)) / (2 * A)` ikinci dereceden bir Denklem için bir kök döndürür (denklemin bir çözüme sahip olduğu durumda).  

## <a name="it-all-starts-with-systemlinqexpression"></a>Hepsi System. LINQ. Expression ile başlar

İfade ağaçları ile çalışmanın karmaşıklıklarından biri, programlarda birçok yerde birçok farklı türde ifade geçerli olur. Atama ifadesi düşünün. Atamanın sağ tarafı sabit bir değer, bir değişken, bir yöntem çağrısı ifadesi veya başka bir değer olabilir. Bu dil esnekliği, bir ifade ağacında çapraz geçiş yaparken bir ağacın düğümleri içinde herhangi bir yerde birçok farklı ifade türüyle karşılaşacağınız anlamına gelir. Bu nedenle, temel ifade türüyle çalışabilmeniz için en kolay yöntem vardır. Ancak bazen daha fazla bilmeniz gerekir.
Taban Ifade sınıfı, bu amaçla bir `NodeType` özelliği içerir.
Olası ifade türlerinin numaralandırması olan bir `ExpressionType` döndürür.
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

`System.Linq.Expression` sınıfı, ifadeler oluşturmak için birçok statik yöntem de içerir. Bu yöntemler, alt öğeleri için sağlanan bağımsız değişkenleri kullanarak bir ifade düğümü oluşturur. Bu şekilde, yaprak düğümlerinden bir ifade oluşturursunuz. Örneğin, bu kod bir ekleme ifadesi oluşturur:

```csharp
// Addition is an add expression for "1 + 2"
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
var addition = Expression.Add(one, two);
```

Bu basit örnekte, ifade ağaçları oluşturmak ve bunlarla çalışmak için birçok tür bulunduğunu görebilirsiniz. Bu karmaşıklık, C# dilin sağladığı zengin sözlük yeteneklerini sağlamak için gereklidir.

## <a name="navigating-the-apis"></a>API 'Lerde gezinme
C# Dilin sözdizimi öğelerinin neredeyse tamamına eşlenen ifade düğüm türleri vardır. Her türün bu tür dil öğesi için özel yöntemleri vardır. Tek seferde baş bir süre içinde tutulması çok önemlidir. Her şeyi yeniden denemeye çalışmak yerine, Ifade ağaçları ile çalışmak için kullandığım teknikler şunlardır:

1. İnceleme yapmanız gereken olası düğümleri öğrenmek için `ExpressionType` numaralandırmasının üyelerine bakın. Bu aslında bir ifade ağacını geçmek ve anlamak istediğinizde yardımcı olur.
2. Bir ifade oluşturmak için `Expression` sınıfının statik üyelerine bakın. Bu yöntemler bir alt düğümleri kümesinden herhangi bir ifade türü oluşturabilir.
3. Değiştirilen bir ifade ağacı oluşturmak için `ExpressionVisitor` sınıfına bakın.

Bu üç alanın her birine baktığımızda daha fazla bilgi bulabilirsiniz. Bağımsız olarak, bu üç adımdan biriyle başladığınızda ne yapmanız gerektiğini öğreneceksiniz.
 
 [Sonraki--Ifade ağaçları yürütülüyor](expression-trees-execution.md)
