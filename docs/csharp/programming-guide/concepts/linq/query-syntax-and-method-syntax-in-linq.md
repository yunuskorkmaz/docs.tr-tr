---
title: LINQ'te Sorgu Sözdizimi ve Yöntem Sözdizimi (C#)
description: LINQ 'te sorgu sözdizimi ve Yöntem sözdizimi hakkında bilgi edinin. Buna standart sorgu işleci genişletme yöntemleri ve lambda ifadeleri dahildir.
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], query syntax vs. method syntax
- queries [LINQ in C#], syntax comparisons
ms.assetid: eedd6dd9-fec2-428c-9581-5b8783810ded
ms.openlocfilehash: 1765a15347aeedb9cc5fa6784abdfad6fafe4016
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87300767"
---
# <a name="query-syntax-and-method-syntax-in-linq-c"></a>LINQ'te Sorgu Sözdizimi ve Yöntem Sözdizimi (C#)
Giriş dili tümleşik sorgu (LINQ) belgelerindeki çoğu sorgu LINQ bildirime dayalı sorgu söz dizimi kullanılarak yazılır. Ancak, kod derlendiğinde, sorgu söz dizimi .NET ortak dil çalışma zamanı (CLR) için yöntem çağrılarına çevrilmelidir. Bu yöntem,,,,, ve gibi adlara sahip standart sorgu işleçlerini `Where` çağırır `Select` `GroupBy` `Join` `Max` `Average` . Sorgu söz dizimi yerine yöntemi sözdizimi kullanarak doğrudan çağırabilirsiniz.  
  
 Sorgu sözdizimi ve Yöntem sözdizimi anlam açısından aynıdır, ancak birçok kişi sorgu söz dizimini daha basit ve okunması daha kolay bir şekilde bulur. Bazı sorgular Yöntem çağrıları olarak ifade etmelidir. Örneğin, belirli bir koşulla eşleşen öğe sayısını alan bir sorgu ifade etmek için bir yöntem çağrısı kullanmanız gerekir. Ayrıca, bir kaynak dizisinde en büyük değere sahip öğeyi alan bir sorgu için bir yöntem çağrısı kullanmanız gerekir. Ad alanındaki standart sorgu işleçleri için başvuru belgeleri <xref:System.Linq> genellikle Yöntem sözdizimini kullanır. Bu nedenle, LINQ sorguları yazmaya Başlarken bile, sorgularda ve sorgu ifadelerinde Yöntem sözdiziminin nasıl kullanılacağını bilmek yararlı olur.  
  
## <a name="standard-query-operator-extension-methods"></a>Standart Sorgu İşleci Genişletme Yöntemleri  
 Aşağıdaki örnek, basit bir *sorgu ifadesini* ve *Yöntem tabanlı sorgu*olarak yazılmış anlamsal olarak denk sorguyu gösterir.  
  
 [!code-csharp[csLINQGettingStarted#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#22)]  
  
 İki örnekten alınan çıkış aynı. Sorgu değişkeninin türünün her iki formlarda de aynı olduğunu görebilirsiniz: <xref:System.Collections.Generic.IEnumerable%601> .  
  
 Yöntem tabanlı sorguyu anlamak için daha yakından inceleyelim. İfadenin sağ tarafında, `where` yan tümcesinin artık nesne üzerinde bir örnek yöntemi olarak ifade ettiğini unutmayın. Bu, `numbers` geri çekmenin bir türü olur `IEnumerable<int>` . Genel arabirime alışkın değilseniz <xref:System.Collections.Generic.IEnumerable%601> , bir yöntemi olmadığını bilirsiniz `Where` . Ancak, Visual Studio IDE 'de IntelliSense tamamlanma listesini çağırdığınızda yalnızca bir yöntem değil,, `Where` ve gibi birçok başka yöntem de görüntülenir `Select` `SelectMany` `Join` `Orderby` . Bunlar standart sorgu işleçleridir.  
  
 ![IntelliSense 'de tüm standart sorgu işleçlerini gösteren ekran görüntüsü.](./media/query-syntax-and-method-syntax-in-linq/standard-query-operators.png)  
  
 <xref:System.Collections.Generic.IEnumerable%601>Bu ek yöntemleri dahil etmek için yeniden tanımlanmış gibi görünse de, aslında bu durum değildir. Standart sorgu işleçleri, *genişletme yöntemleri*olarak adlandırılan yeni bir yöntem türü olarak uygulanır. Uzantı yöntemleri "genişletme" varolan bir tür; Bunlar, tür üzerinde örnek yöntemmiş gibi çağrılabilir. Standart sorgu işleçleri genişletilir <xref:System.Collections.Generic.IEnumerable%601> ve bu, neden yazılabilir `numbers.Where(...)` .  
  
 LINQ kullanmaya başlamak için, aslında uzantı yöntemleri hakkında bilmeniz gereken her şey, doğru yönergeleri kullanarak bunları uygulamanızda kapsama getirme yöntemleridir `using` . Uygulamanızın görünüm noktasından, bir genişletme yöntemi ve normal bir örnek yöntemi aynıdır.  
  
 Uzantı yöntemleri hakkında daha fazla bilgi için bkz. [Uzantı yöntemleri](../../classes-and-structs/extension-methods.md). Standart sorgu işleçleri hakkında daha fazla bilgi için bkz. [Standart sorgu Işleçlerine genel bakış (C#)](./standard-query-operators-overview.md). Ve gibi bazı LINQ sağlayıcıları [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] kendi standart sorgu işleçlerini ve diğer türler için ek genişletme yöntemlerini uygular <xref:System.Collections.Generic.IEnumerable%601> .  
  
## <a name="lambda-expressions"></a>Lambda İfadeleri  
 Önceki örnekte, koşullu ifadenin ( `num % 2 == 0` ) yönteme bir satır içi bağımsız değişken olarak geçirildiğine dikkat edin `Where` : `Where(num => num % 2 == 0).` Bu satır içi ifadeye lambda ifadesi denir. Başka türlü bir anonim yöntem veya bir genel temsilci ya da bir ifade ağacı olarak daha az sayıda biçimde yazılması gereken kodu yazmak için kullanışlı bir yoldur. C# ' de `=>` , "gider" olarak okunan lambda işleçtir. `num`İşlecinin sol tarafındaki giriş değişkeni sorgu ifadesinde öğesine karşılık gelir `num` . Derleyici, `num` genel bir tür olduğunu bildiğinden, türünü çıkarabilir `numbers` <xref:System.Collections.Generic.IEnumerable%601> . Lambda gövdesi, sorgu söz dizimi ya da başka bir C# ifadesi ya da deyimi ile yalnızca ifade ile aynıdır; Bu, Yöntem çağrılarını ve diğer karmaşık mantığı içerebilir. "Dönüş değeri" yalnızca ifade sonucudur.  
  
 LINQ kullanmaya başlamak için lambdaları yoğun bir şekilde kullanmanız gerekmez. Ancak bazı sorgular yalnızca Yöntem söz dizimine ve bu öğelerden bazıları lambda ifadeleri gerektirir. Lambdalar hakkında daha fazla bilgi sahibi olduktan sonra, LINQ araç kutusu 'nda güçlü ve esnek bir araç olduğunu fark edersiniz. Daha fazla bilgi için bkz. [lambda ifadeleri](../../statements-expressions-operators/lambda-expressions.md).  
  
## <a name="composability-of-queries"></a>Sorgu Oluşturabilirliği  
 Önceki kod örneğinde, `OrderBy` yönteminin, çağrısı üzerindeki nokta operatörü kullanılarak çağrılacağını unutmayın `Where` . `Where`filtrelenmiş bir sıra üretir ve sonra `Orderby` Bu dizi üzerinde sıralama yaparak çalışır. Sorgular bir döndürdüğü `IEnumerable` için, Yöntem çağrılarını birlikte zincirleyerek yöntem sözdiziminde oluşturursunuz. Sorgu söz dizimini kullanarak sorgular yazdığınızda derleyicinin arka planda yaptığı şeydir. Bir sorgu değişkeni sorgunun sonuçlarını depolamadığından, bunu değiştirebilir veya herhangi bir zamanda yeni bir sorgu için temel olarak kullanabilirsiniz.  
