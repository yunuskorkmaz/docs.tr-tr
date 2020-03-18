---
title: İfade Ağaçlarını Destekleyen Çerçeve Türleri
description: İfade ağaçlarını destekleyen, ifade ağaçları oluşturan çerçeve türleri ve ifade ağacı API'leriyle çalışma teknikleri hakkında bilgi edinin.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: e9c85021-0d36-48af-91b7-aaaa66f22654
ms.openlocfilehash: 8483c46dde3ea97138e55ab84a5924a3d2578730
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146092"
---
# <a name="framework-types-supporting-expression-trees"></a>İfade Ağaçlarını Destekleyen Çerçeve Türleri

[Önceki -- İfade Ağaçları Açıklaması](expression-trees-explained.md)

.NET Core çerçevesinde Expression Trees ile çalışan sınıfların büyük bir listesi vardır.
Tam listeyi . <xref:System.Linq.Expressions>
Tam listeyi gözden geçirmek yerine, çerçeve sınıflarının nasıl tasarlandığını anlayalım.

Dil tasarımında, bir ifade bir değeri değerlendiren ve döndüren bir kod gövdesidir. İfadeler çok basit olabilir: `1` sabit ifade 1'in sabit değerini döndürür. Bunlar daha karmaşık olabilir: `(-B + Math.Sqrt(B*B - 4 * A * C)) / (2 * A)` İfade, kuadratik bir denklem için bir kök döndürür (denklemin bir çözümü olduğu durumlarda).  

## <a name="it-all-starts-with-systemlinqexpression"></a>Her şey System.Linq.Expression ile başlar.

İfade ağaçlarıyla çalışmanın karmaşıklıklarından biri, programların birçok yerinde birçok farklı ifade türün geçerli olmasıdır. Atama ifadesini düşünün. Bir atamanın sağ tarafı sabit bir değer, değişken, yöntem arama ifadesi veya başka olabilir. Bu dil esnekliği, bir ifade ağacında gezinirken bir ağacın düğümlerinde herhangi bir yerde birçok farklı ifade türüyle karşılaşabileceğiniz anlamına gelir. Bu nedenle, temel ifade türüyle çalışabildiğinizde, bu en basit çalışma şeklidir. Ancak, bazen daha fazla bilmek gerekir.
Taban İfade sınıfı `NodeType` bu amaç için bir özellik içerir.
Olası ifade `ExpressionType` türlerinin numaralandırması olan bir döndürür.
Düğümün türünü anladıktan sonra, bu türe atabilir ve ifade düğümünün türünü bilerek belirli eylemleri gerçekleştirebilirsiniz. Belirli düğüm türlerini arayabilir ve ardından bu tür bir ifadenin belirli özellikleriyle çalışabilirsiniz.

Örneğin, bu kod değişken erişim ifadesi için bir değişkenin adını yazdırır. Düğüm türünü denetleme, ardından değişken erişim ifadesine döküm ve ardından belirli ifade türünün özelliklerini denetleme alıştırmasını uyguladım:

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

## <a name="creating-expression-trees"></a>İfade Ağaçları Oluşturma

Sınıf, `System.Linq.Expression` ifadeler oluşturmak için birçok statik yöntem de içerir. Bu yöntemler, alt ları için sağlanan bağımsız değişkenleri kullanarak bir ifade düğümü oluşturur. Bu şekilde, yaprak düğümlerinden bir ifade oluşturursunuz. Örneğin, bu kod bir Ekle ifadesi oluşturur:

```csharp
// Addition is an add expression for "1 + 2"
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
var addition = Expression.Add(one, two);
```

Bu basit örnekten, ifade ağaçlarının oluşturulması nda ve bununla çalışmada birçok türde rol aldığını görebilirsiniz. Bu karmaşıklık C# dili tarafından sağlanan zengin kelime yeteneklerini sağlamak için gereklidir.

## <a name="navigating-the-apis"></a>API'ler de gezinme
C# dilinin hemen hemen tüm sözdizimi öğeleriyle eşleyen İfade düğümü türleri vardır. Her türde dil öğesi bu tür için özel yöntemler vardır. Aynı anda kafanda tutmak çok fazla. Yerine her şeyi ezberlemek için denemek, burada Ifade ağaçları ile çalışmak için kullandığınız teknikler şunlardır:

1. İncelemeniz gereken olası `ExpressionType` düğümleri belirlemek için enum üyelerine bakın. Bu gerçekten geçiş ve bir ifade ağacı anlamak istediğinizde yardımcı olur.
2. Bir ifade oluşturmak için `Expression` sınıfın statik üyelerine bakın. Bu yöntemler, alt düğümleri kümesinden herhangi bir ifade türü oluşturabilirsiniz.
3. Değiştirilmiş bir `ExpressionVisitor` ifade ağacı oluşturmak için sınıfa bakın.

Bu üç alanın her birine baktıkça daha fazlasını bulacaksınız. Her zaman, bu üç adımdan biriyle başladığınızda ihtiyacınız olanı bulacaksınız.

 [Sonraki -- İfade Ağaçlarını Yürütme](expression-trees-execution.md)
