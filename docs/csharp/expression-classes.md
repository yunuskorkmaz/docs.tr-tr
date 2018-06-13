---
title: Destek ifade ağaçları Framework türleri
description: İfade ağaçları destekleme framework türleri ifade ağaçları ve ifade ağacına API'leri ile çalışmak için teknikleri oluşturma hakkında bilgi edinin.
ms.date: 06/20/2016
ms.assetid: e9c85021-0d36-48af-91b7-aaaa66f22654
ms.openlocfilehash: 3110f2a9534085aba95fcb5c8e76f66229e79f86
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33214951"
---
# <a name="framework-types-supporting-expression-trees"></a>Destek ifade ağaçları Framework türleri

[Önceki--Açıklandığı ifade ağaçları](expression-trees-explained.md)

İfade ağaçları ile iş sınıfları .NET Core Framework'te büyük listesi verilmiştir.
Tam listeye bakın [burada](/dotnet/core/api/System.Linq.Expressions).
Tam listeyi çalıştırmak yerine nasıl framework sınıfları tasarlanmış anlayalım.

Dil tasarımında, bir ifade değerlendirir ve bir değer döndürür kodu gövdesidir. İfadeleri çok basit: sabit ifade `1` sabit 1 değerini döndürür. Daha karmaşık olabilir: ifade `(-B + Math.Sqrt(B*B + 4 * A * C)) / (2 * A)` ikinci derece eşitlik (denklemi bir çözüme sahip olduğu durumda) için bir kök döndürür.  

## <a name="it-all-starts-with-systemlinqexpression"></a>Tüm System.Linq.Expression ile başlar

İfade ağaçları ile çalışmanın karmaşıklıkları birçok farklı türde ifadeler programlar birçok yerde geçerli olduğunu biridir. Bir atama ifadesi göz önünde bulundurun. Sağ taraftaki atama sabit bir değer, bir değişken, bir yöntem çağrısı ifadesi veya başkalarının olabilir. Bu dil esneklik bir ifade ağacına gezme zaman ağaç düğümleri başka bir yerindeki birçok farklı ifade türleri karşılaşabileceğiniz anlamına gelir. Temel ifade türü ile çalışabilir, bu nedenle, iş için en basit yolu olmasıdır. Ancak, bazen daha fazla bilgi edinmek gerekir.
Temel ifade sınıfı içeren bir `NodeType` özelliği bu amaç için.
Döndürdüğü bir `ExpressionType` olası ifade türleri numaralandırması olduğu.
Düğüm türü öğrendikten sonra onu bu türe ve ifade düğümü türü bilerek belirli eylemleri gerçekleştirebilirsiniz. Belirli düğüm türleri arayın ve sonra bu tür bir ifade belirli özellikleri ile çalışma.

Örneğin, bu kod bir değişken adı bir değişken erişim ifadenin yazdırır. Düğüm türü denetimi sonra bir değişken erişim ifadesi atama ve belirli ifade türünün özelliklerini denetleme uygulama takip:

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

## <a name="creating-expression-trees"></a>İfade ağaçları oluşturma

`System.Linq.Expression` Sınıfı ayrıca ifadeleri oluşturmak için birçok statik yöntemler içerir. Bu yöntemler, çocuklar için sağlanan bağımsız değişkenler kullanarak bir ifade düğümü oluşturur. Bu şekilde, bir ifade, yaprak düğümü oluşturmak. Örneğin, bu kod bir Ekle ifade oluşturur:

```csharp
// Addition is an add expression for "1 + 2"
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
var addition = Expression.Add(one, two);
```

Bu basit örneğindeki birçok türleri oluşturma ve ifade ağaçları ile çalışma oynayan görebilirsiniz. Bu karmaşıklık C# dili tarafından sağlanan zengin sözlük özellikleri sağlamak gereklidir.

## <a name="navigating-the-apis"></a>API'ler gezinme
Neredeyse tüm C# dili sözdizimi öğelerinin eşleme ifadesi düğüm türü vardır. Her tür language öğesi türü için belirli yöntemler vardır. Bir kerede başının içinde tutmak için çok karmaşıktır. Her şeyi ezberleme çalıştığınızda yerine ifade ağaçları ile çalışmak için kullandığım teknikler şunlardır:
1. Ara üyelerinden birinde `ExpressionType` incelemekte olası düğümleri enum. Bu gerçekten çapraz geçiş ve bir ifade ağacına anlamak istediğinizde yardımcı olur.
2. Ara statik üyeleri `Expression` bir ifade oluşturmak için sınıfı. Bu yöntemlerin herhangi bir alt kümesini ifade türünden düğümleri oluşturabilirsiniz.
3. Bakmak `ExpressionVisitor` değiştirilmiş ifade ağacına oluşturmak için sınıfı.

Yazarken daha fazla alanlarının her birinde bu üç Ara bulabilirsiniz. Neredeyse şaşmaz biçimde, bu üç adımı biri ile başlattığınızda gerekenler bulacaksınız.
 
 [Sonraki--İfade ağaçlarını yürütme](expression-trees-execution.md)
 
