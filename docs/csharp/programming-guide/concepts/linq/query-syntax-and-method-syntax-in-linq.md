---
title: LINQ'te Sorgu Sözdizimi ve Yöntem Sözdizimi (C#)
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], query syntax vs. method syntax
- queries [LINQ in C#], syntax comparisons
ms.assetid: eedd6dd9-fec2-428c-9581-5b8783810ded
ms.openlocfilehash: 17280daaf98010245bbd019652a2a46d7f66ab59
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635502"
---
# <a name="query-syntax-and-method-syntax-in-linq-c"></a>LINQ'te Sorgu Sözdizimi ve Yöntem Sözdizimi (C#)
Giriş dili tümleşik sorgu (LINQ) belgelerindeki çoğu sorgu LINQ bildirime dayalı sorgu söz dizimi kullanılarak yazılır. Ancak, kod derlendiğinde, sorgu söz dizimi .NET ortak dil çalışma zamanı (CLR) için yöntem çağrılarına çevrilmelidir. Bu yöntem, `Where`, `Select`, `GroupBy`, `Join`, `Max`ve `Average`gibi adlara sahip standart sorgu işleçlerini çağırır. Sorgu söz dizimi yerine yöntemi sözdizimi kullanarak doğrudan çağırabilirsiniz.  
  
 Sorgu sözdizimi ve Yöntem sözdizimi anlam açısından aynıdır, ancak birçok kişi sorgu söz dizimini daha basit ve okunması daha kolay bir şekilde bulur. Bazı sorgular Yöntem çağrıları olarak ifade etmelidir. Örneğin, belirli bir koşulla eşleşen öğe sayısını alan bir sorgu ifade etmek için bir yöntem çağrısı kullanmanız gerekir. Ayrıca, bir kaynak dizisinde en büyük değere sahip öğeyi alan bir sorgu için bir yöntem çağrısı kullanmanız gerekir. <xref:System.Linq> ad alanındaki standart sorgu işleçleri için başvuru belgeleri genellikle Yöntem sözdizimini kullanır. Bu nedenle, LINQ sorguları yazmaya Başlarken bile, sorgularda ve sorgu ifadelerinde Yöntem sözdiziminin nasıl kullanılacağını bilmek yararlı olur.  
  
## <a name="standard-query-operator-extension-methods"></a>Standart Sorgu İşleci Genişletme Yöntemleri  
 Aşağıdaki örnek, basit bir *sorgu ifadesini* ve *Yöntem tabanlı sorgu*olarak yazılmış anlamsal olarak denk sorguyu gösterir.  
  
 [!code-csharp[csLINQGettingStarted#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#22)]  
  
 İki örnekten alınan çıkış aynı. Sorgu değişkeninin türünün her iki formlarda de aynı olduğunu görebilirsiniz: <xref:System.Collections.Generic.IEnumerable%601>.  
  
 Yöntem tabanlı sorguyu anlamak için daha yakından inceleyelim. İfadenin sağ tarafında, `where` yan tümcesinin artık `numbers` nesnesi üzerinde bir örnek yöntemi olarak ifade ettiğini unutmayın. Bu, geri çekmenin bir `IEnumerable<int>`türü olur. Genel <xref:System.Collections.Generic.IEnumerable%601> arabirimi hakkında bilginiz varsa, bir `Where` yöntemine sahip olmadığını bilirsiniz. Ancak, Visual Studio IDE 'de IntelliSense tamamlanma listesini çağırdığınızda yalnızca bir `Where` yöntemi değil, `Select`, `SelectMany`, `Join`ve `Orderby`gibi diğer birçok yöntem de görürsünüz. Bunlar standart sorgu işleçleridir.  
  
 ![IntelliSense 'de tüm standart sorgu işleçlerini gösteren ekran görüntüsü.](./media/query-syntax-and-method-syntax-in-linq/standard-query-operators.png)  
  
 Bu ek yöntemleri dahil etmek için <xref:System.Collections.Generic.IEnumerable%601> yeniden tanımlansa da, aslında bu durum böyle değildir. Standart sorgu işleçleri, *genişletme yöntemleri*olarak adlandırılan yeni bir yöntem türü olarak uygulanır. Uzantı yöntemleri "genişletme" varolan bir tür; Bunlar, tür üzerinde örnek yöntemmiş gibi çağrılabilir. Standart sorgu işleçleri <xref:System.Collections.Generic.IEnumerable%601> genişletir ve bu nedenle `numbers.Where(...)`yazabilmenizi sağlayabilir.  
  
 LINQ kullanmaya başlamak için, aslında uzantı yöntemleri hakkında bilmeniz gereken her şey, doğru `using` yönergelerini kullanarak bunları uygulamanızdaki kapsama getirme yöntemleridir. Uygulamanızın görünüm noktasından, bir genişletme yöntemi ve normal bir örnek yöntemi aynıdır.  
  
 Uzantı yöntemleri hakkında daha fazla bilgi için bkz. [Uzantı yöntemleri](../../classes-and-structs/extension-methods.md). Standart sorgu işleçleri hakkında daha fazla bilgi için bkz. [Standart sorgu IşleçlerineC#genel bakış ()](./standard-query-operators-overview.md). [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] ve [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]gibi bazı LINQ sağlayıcıları, <xref:System.Collections.Generic.IEnumerable%601>yanı sıra diğer türler için kendi standart sorgu işleçlerini ve ek uzantı yöntemlerini uygular.  
  
## <a name="lambda-expressions"></a>Lambda İfadeleri  
 Önceki örnekte, koşullu ifadenin (`num % 2 == 0`) `Where` yöntemine satır içi bağımsız değişken olarak geçirildiğine dikkat edin: Bu satır içi ifadeye `Where(num => num % 2 == 0).` lambda ifadesi olarak adlandırılır. Başka türlü bir anonim yöntem veya bir genel temsilci ya da bir ifade ağacı olarak daha az sayıda biçimde yazılması gereken kodu yazmak için kullanışlı bir yoldur. C# `=>`, "gider" olarak okunan lambda işleçtir. İşlecin sol tarafındaki `num`, sorgu ifadesindeki `num` karşılık gelen giriş değişkenidir. Derleyici, `numbers` genel bir <xref:System.Collections.Generic.IEnumerable%601> türü olduğunu bildiği için `num` türünü çıkarabilir. Lambda gövdesi sorgu söz dizimi ya da başka C# bir ifade ya da deyimde yalnızca ifadesiyle aynıdır; Bu, Yöntem çağrılarını ve diğer karmaşık mantığı içerebilir. "Dönüş değeri" yalnızca ifade sonucudur.  
  
 LINQ kullanmaya başlamak için lambdaları yoğun bir şekilde kullanmanız gerekmez. Ancak bazı sorgular yalnızca Yöntem söz dizimine ve bu öğelerden bazıları lambda ifadeleri gerektirir. Lambdalar hakkında daha fazla bilgi sahibi olduktan sonra, LINQ araç kutusu 'nda güçlü ve esnek bir araç olduğunu fark edersiniz. Daha fazla bilgi için bkz. [lambda ifadeleri](../../statements-expressions-operators/lambda-expressions.md).  
  
## <a name="composability-of-queries"></a>Sorgu Oluşturabilirliği  
 Önceki kod örneğinde, `OrderBy` yönteminin, `Where`çağrısında nokta işleci kullanılarak çağrıldığı unutulmamalıdır. `Where` filtrelenmiş bir sıra üretir ve sonra bu sırada `Orderby` sıralayarak çalışır. Sorgular bir `IEnumerable`döndürdüğü için, Yöntem çağrılarını birlikte zincirleyerek yöntem sözdiziminde oluşturursunuz. Sorgu söz dizimini kullanarak sorgular yazdığınızda derleyicinin arka planda yaptığı şeydir. Bir sorgu değişkeni sorgunun sonuçlarını depolamadığından, bunu değiştirebilir veya herhangi bir zamanda yeni bir sorgu için temel olarak kullanabilirsiniz.  
