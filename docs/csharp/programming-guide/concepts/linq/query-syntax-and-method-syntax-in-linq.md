---
title: LINQ'te Sorgu Sözdizimi ve Yöntem Sözdizimi (C#)
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], query syntax vs. method syntax
- queries [LINQ in C#], syntax comparisons
ms.assetid: eedd6dd9-fec2-428c-9581-5b8783810ded
ms.openlocfilehash: 8351661bdb7eaf841577eb128a8fec12efed2360
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69591413"
---
# <a name="query-syntax-and-method-syntax-in-linq-c"></a>LINQ'te Sorgu Sözdizimi ve Yöntem Sözdizimi (C#)
Giriş dili tümleşik sorgu ([!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]) belgelerindeki çoğu sorgu LINQ bildirime dayalı sorgu söz dizimi kullanılarak yazılır. Ancak, kod derlendiğinde, sorgu söz dizimi .NET ortak dil çalışma zamanı (CLR) için yöntem çağrılarına çevrilmelidir. Bu `Where`Yöntem `Select`, ,,`Join`,, ve`Average`gibi adlara sahip standart sorgu işleçlerini çağırır. `GroupBy` `Max` Sorgu söz dizimi yerine yöntemi sözdizimi kullanarak doğrudan çağırabilirsiniz.  
  
 Sorgu sözdizimi ve Yöntem sözdizimi anlam açısından aynıdır, ancak birçok kişi sorgu söz dizimini daha basit ve okunması daha kolay bir şekilde bulur. Bazı sorgular Yöntem çağrıları olarak ifade etmelidir. Örneğin, belirli bir koşulla eşleşen öğe sayısını alan bir sorgu ifade etmek için bir yöntem çağrısı kullanmanız gerekir. Ayrıca, bir kaynak dizisinde en büyük değere sahip öğeyi alan bir sorgu için bir yöntem çağrısı kullanmanız gerekir. <xref:System.Linq> Ad alanındaki standart sorgu işleçleri için başvuru belgeleri genellikle Yöntem sözdizimini kullanır. Bu nedenle, sorgu yazmaya [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] Başlarken bile, sorgularda ve sorgu ifadelerinde Yöntem sözdiziminin nasıl kullanılacağına ilişkin bilgi sahibi olmak yararlı olacaktır.  
  
## <a name="standard-query-operator-extension-methods"></a>Standart Sorgu İşleci Genişletme Yöntemleri  
 Aşağıdaki örnek, basit bir *sorgu ifadesini* ve *Yöntem tabanlı sorgu*olarak yazılmış anlamsal olarak denk sorguyu gösterir.  
  
 [!code-csharp[csLINQGettingStarted#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#22)]  
  
 İki örnekten alınan çıkış aynı. Sorgu değişkeninin türünün her iki formlarda de aynı olduğunu görebilirsiniz: <xref:System.Collections.Generic.IEnumerable%601>.  
  
 Yöntem tabanlı sorguyu anlamak için daha yakından inceleyelim. İfadenin sağ tarafında, `where` yan tümcesinin artık `numbers` nesne üzerinde bir örnek yöntemi olarak ifade ettiğini unutmayın `IEnumerable<int>`. Bu, geri çekmenin bir türü olur. Genel <xref:System.Collections.Generic.IEnumerable%601> arabirime alışkın değilseniz, bir `Where` yöntemi olmadığını bilirsiniz. Ancak, Visual Studio IDE 'de IntelliSense tamamlanma listesini çağırdığınızda yalnızca `Where` bir yöntem değil,, ve `Orderby`gibi birçok başka yöntem `Select` `SelectMany` `Join`de görüntülenir. Bunlar standart sorgu işleçleridir.  
  
 ![IntelliSense 'de tüm standart sorgu işleçlerini gösteren ekran görüntüsü.](./media/query-syntax-and-method-syntax-in-linq/standard-query-operators.png)  
  
 Bu ek yöntemleri dahil etmek <xref:System.Collections.Generic.IEnumerable%601> için yeniden tanımlanmış gibi görünse de, aslında bu durum değildir. Standart sorgu işleçleri, *genişletme yöntemleri*olarak adlandırılan yeni bir yöntem türü olarak uygulanır. Uzantı yöntemleri "genişletme" varolan bir tür; Bunlar, tür üzerinde örnek yöntemmiş gibi çağrılabilir. Standart sorgu işleçleri genişletilir <xref:System.Collections.Generic.IEnumerable%601> ve bu, neden yazılabilir. `numbers.Where(...)`  
  
 Kullanmaya [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]başlamak için, aslında uzantı yöntemleri hakkında bilmeniz gereken her şey, doğru `using` yönergeleri kullanarak bunları uygulamanızdaki kapsama getirme yöntemleridir. Uygulamanızın görünüm noktasından, bir genişletme yöntemi ve normal bir örnek yöntemi aynıdır.  
  
 Uzantı yöntemleri hakkında daha fazla bilgi için bkz. [Uzantı yöntemleri](../../classes-and-structs/extension-methods.md). Standart sorgu işleçleri hakkında daha fazla bilgi için bkz. [Standart sorgu IşleçlerineC#genel bakış ()](./standard-query-operators-overview.md). [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] Ve [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] <xref:System.Collections.Generic.IEnumerable%601>gibi bazı sağlayıcılar, kendi standart sorgu işleçlerini ve diğer türler için ek genişletme yöntemlerini uygular. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]  
  
## <a name="lambda-expressions"></a>Lambda İfadeleri  
 Önceki örnekte, koşullu ifadenin (`num % 2 == 0`) `Where` yönteme bir satır içi bağımsız değişken olarak geçtiğini unutmayın: `Where(num => num % 2 == 0).`Bu satır içi ifadeye lambda ifadesi denir. Başka türlü bir anonim yöntem veya bir genel temsilci ya da bir ifade ağacı olarak daha az sayıda biçimde yazılması gereken kodu yazmak için kullanışlı bir yoldur. ' C# `=>` De, "gider" olarak okunan lambda işleçtir. İşlecinin sol tarafındaki giriş değişkeni sorgu ifadesinde öğesine `num` karşılık gelir. `num` Derleyici, genel `num` `numbers` birtürolduğunubildiğinden<xref:System.Collections.Generic.IEnumerable%601> , türünü çıkarabilir. Lambda gövdesi sorgu söz dizimi ya da başka C# bir ifade ya da deyimde yalnızca ifadesiyle aynıdır; Bu, Yöntem çağrılarını ve diğer karmaşık mantığı içerebilir. "Dönüş değeri" yalnızca ifade sonucudur.  
  
 Kullanmaya [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]başlamak için lambdaları yoğun bir şekilde kullanmanız gerekmez. Ancak bazı sorgular yalnızca Yöntem söz dizimine ve bu öğelerden bazıları lambda ifadeleri gerektirir. Lambdalar hakkında daha tanıdık olduktan sonra, [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] araç kutusu 'nda güçlü ve esnek bir araç olduğunu fark edersiniz. Daha fazla bilgi için bkz. [lambda ifadeleri](../../statements-expressions-operators/lambda-expressions.md).  
  
## <a name="composability-of-queries"></a>Sorgu Oluşturabilirliği  
 Önceki kod örneğinde, `OrderBy` yönteminin, `Where`çağrısı üzerindeki nokta operatörü kullanılarak çağrılacağını unutmayın. `Where`filtrelenmiş bir sıra üretir ve sonra `Orderby` bu dizi üzerinde sıralama yaparak çalışır. Sorgular bir `IEnumerable`döndürdüğü için, Yöntem çağrılarını birlikte zincirleyerek yöntem sözdiziminde oluşturursunuz. Sorgu söz dizimini kullanarak sorgular yazdığınızda derleyicinin arka planda yaptığı şeydir. Bir sorgu değişkeni sorgunun sonuçlarını depolamadığından, bunu değiştirebilir veya herhangi bir zamanda yeni bir sorgu için temel olarak kullanabilirsiniz.  
