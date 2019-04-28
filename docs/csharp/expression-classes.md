---
title: İfade ağaçlarını destekleyen çerçeve türleri
description: İfade ağaçlarını destekleyen çerçeve türleri ifade ağaçları ve ifade ağacı API'leri ile çalışmaya yönelik teknikleri oluşturma hakkında bilgi edinin.
ms.date: 06/20/2016
ms.assetid: e9c85021-0d36-48af-91b7-aaaa66f22654
ms.openlocfilehash: c18bbfb1273156a4b070d1f195d9e823256fde9d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61646585"
---
# <a name="framework-types-supporting-expression-trees"></a>İfade ağaçlarını destekleyen çerçeve türleri

[Önceki--İfade ağaçları açıklaması](expression-trees-explained.md)

İfade ağaçları ile çalışan .NET Core framework sınıfları büyük bir listesi bulunur.
Tam listesini görebilirsiniz <xref:System.Linq.Expressions>.
Tam bir listesi çalıştırmak yerine framework sınıfları nasıl tasarladık bakalım.

Dil tasarımında, bir ifade değerlendirir ve bir değer döndüren kod gövdesidir. İfadeleri çok basit: sabit ifade `1` sabit 1 değerini döndürür. Bunlar, daha karmaşık olabilir: İfade `(-B + Math.Sqrt(B*B - 4 * A * C)) / (2 * A)` bir dereceden eşitlik (Denklemin bir çözümü sahip olduğu durumda) için bir kök dizinini döndürür.  

## <a name="it-all-starts-with-systemlinqexpression"></a>Tüm System.Linq.Expression ile başlar

İfade ağaçları ile çalışmanın karmaşıklıkları birçok farklı türde ifadeler programlar pek çok yerde geçerli olduğunu biridir. Atama ifadesi göz önünde bulundurun. Sağ taraftaki atama, sabit bir değer, bir değişken, bir yöntem çağrısı ifadesi veya başkalarının olabilir. Bu dil esneklik, bir ifade ağacı gezme olduğunda, bir ağaç düğümleri herhangi bir yerindeki birçok farklı ifade türü karşılaşabileceğiniz anlamına gelir. Temel ifade türü ile çalışabilir, bu nedenle, iş yapmanın en kolay yolu olmasıdır. Ancak, bazen daha fazla bilgi edinmek gerekir.
Temel ifade sınıfı içeren bir `NodeType` bu amaç için özellik.
Döndürür bir `ExpressionType` olası ifade türleri numaralandırması olduğu.
Düğüm türü öğrendikten sonra bu türe dönüştürme ve ifadesi düğüm türü bilerek belirli eylemleri gerçekleştirme. Belirli düğüm türleri arayın ve ardından, bu tür bir ifade belirli özelliklerle çalışma.

Örneğin, bu kod, bir değişken erişim ifadesi için bir değişken adı yazdırır. Düğüm türü denetimi sonra bir değişken erişim ifadesi atama ve ardından belirli ifade türünün özelliklerini denetleme uygulaması ve ardından:

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

`System.Linq.Expression` Sınıfı da ifadeleri oluşturmak için çok sayıda statik yöntemler içerir. Bu yöntemleri kullanarak alt öğeleri için sağlanan bağımsız değişkenler bir ifade düğüm oluşturun. Bu şekilde, bir ifade yaprak düğümlerini oluşturmak. Örneğin, bu kod bir Ekle ifade oluşturur:

```csharp
// Addition is an add expression for "1 + 2"
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
var addition = Expression.Add(one, two);
```

Bu basit örnekte oluşturmak ve ifade ağaçları ile çalışan birçok türü katılan görebilirsiniz. Bu karmaşıklığı, C# dil tarafından sağlanan zengin sözlük yeteneklerini sağlamak gereklidir.

## <a name="navigating-the-apis"></a>API'leri gezinme
Neredeyse tüm C# dilinin söz dizimi öğeleri için eşleme ifadesi düğüm türü vardır. Her tür dil öğesi türü için belirli yöntemlerine sahiptir. Bu, tek seferde birikimine tutmak için çok fazla olur. Her şeyi ezberlemeniz deneyin yerine ifade ağaçları ile çalışmak için istediğim teknikler şunlardır:
1. Konum üyelerinin `ExpressionType` incelemekte olası düğümleri sabit listesi. Bu gerçekten geçiş yapmak ve bir ifade ağacı anlamak istediğinizde yardımcı olur.
2. Konum statik üyeleri `Expression` bir ifade oluşturmak için sınıf. Bu yöntemlerin herhangi bir ifade türü bir dizi alt düğümleri oluşturabilirsiniz.
3. Bakmak `ExpressionVisitor` değiştirilmiş ifade ağacı oluşturmak için sınıfı.

Üç bu alanların her şekilde daha fazla ara bulabilirsiniz. Neredeyse şaşmaz biçimde, bu üç adımı biriyle başlattığınızda gerekenler bulabilirsiniz.
 
 [Sonraki--İfade ağaçlarını yürütme](expression-trees-execution.md)
