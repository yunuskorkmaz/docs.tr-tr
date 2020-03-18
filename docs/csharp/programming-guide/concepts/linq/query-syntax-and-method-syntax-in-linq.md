---
title: LINQ'te Sorgu Sözdizimi ve Yöntem Sözdizimi (C#)
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], query syntax vs. method syntax
- queries [LINQ in C#], syntax comparisons
ms.assetid: eedd6dd9-fec2-428c-9581-5b8783810ded
ms.openlocfilehash: 17280daaf98010245bbd019652a2a46d7f66ab59
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635502"
---
# <a name="query-syntax-and-method-syntax-in-linq-c"></a>LINQ'te Sorgu Sözdizimi ve Yöntem Sözdizimi (C#)
Giriş Dili Tümleşik Sorgusu (LINQ) belgelerindeki sorguların çoğu LINQ bildirimsel sorgu sözdizimi kullanılarak yazılır. Ancak, sorgu sözdizimi, kod derlendiğinde .NET ortak dil çalışma zamanı (CLR) için yöntem çağrılarına çevrilmelidir. Bu yöntem çağrıları, , , `Where` `Select` `GroupBy` `Join`, `Max`, ve `Average`. gibi adları olan standart sorgu işleçleri, çağırır. Sorgu sözdizimi yerine yöntem sözdizimini kullanarak doğrudan arayabilirsiniz.  
  
 Sorgu sözdizimi ve yöntem sözdizimi anlamsal olarak aynıdır, ancak birçok kişi sorgu sözdizimini daha basit ve okunması daha kolay bulur. Bazı sorgular yöntem çağrıları olarak ifade edilmelidir. Örneğin, belirtilen bir koşulla eşleşen öğe sayısını alan bir sorguyu ifade etmek için bir yöntem çağrısı kullanmanız gerekir. Ayrıca, kaynak sırasında en yüksek değere sahip öğeyi alan bir sorgu için yöntem çağrısı kullanmanız gerekir. <xref:System.Linq> Ad alanındaki standart sorgu işleçleri için başvuru belgeleri genellikle yöntem sözdizimini kullanır. Bu nedenle, LINQ sorguları yazmaya başlarken bile, sorgularda ve sorgu ifadelerinde yöntem sözdizimini nasıl kullanılacağını bilmek yararlıdır.  
  
## <a name="standard-query-operator-extension-methods"></a>Standart Sorgu İşleci Genişletme Yöntemleri  
 Aşağıdaki örnekte basit bir *sorgu ifadesi* ve yöntem *tabanlı sorgu*olarak yazılmış anlamsal eşdeğer sorgu gösterilmektedir.  
  
 [!code-csharp[csLINQGettingStarted#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#22)]  
  
 İki örnekten elde edilen çıktı aynıdır. Sorgu değişkeninin türünün her iki formda da <xref:System.Collections.Generic.IEnumerable%601>aynı olduğunu görebilirsiniz: .  
  
 Yöntem tabanlı sorguyu anlamak için daha yakından inceleyelim. İfadenin sağ tarafında, yan tümcenin `where` artık `numbers` nesne üzerinde bir örnek yöntemi olarak ifade edildiğine `IEnumerable<int>`dikkat edin, hatırlayacağınız gibi bir tür . Genel <xref:System.Collections.Generic.IEnumerable%601> arabirimi biliyorsanız, bir `Where` yöntemi olmadığını bilirsiniz. Ancak, Visual Studio IDE'deki IntelliSense tamamlama listesini çağırırsanız, `Where` yalnızca bir yöntem değil, `Select` `SelectMany`aynı `Join`zamanda `Orderby`, , , ve . Bunlar standart sorgu işleçleridir.  
  
 ![Intellisense tüm standart sorgu operatörleri gösteren ekran görüntüsü.](./media/query-syntax-and-method-syntax-in-linq/standard-query-operators.png)  
  
 Bu ek yöntemleri <xref:System.Collections.Generic.IEnumerable%601> içerecek şekilde yeniden tanımlanmış gibi görünse de, aslında durum böyle değildir. Standart sorgu işleçleri *uzantı yöntemleri*olarak adlandırılan yeni bir yöntem türü olarak uygulanır. Uzantıları yöntemleri varolan bir türü "genişletmek"; türünde örnek yöntemleri gibi çağrılabilir. Standart sorgu işleçleri genişletmek <xref:System.Collections.Generic.IEnumerable%601> ve `numbers.Where(...)`bu yüzden yazabilirsiniz.  
  
 LINQ kullanmaya başlamak için, uzantı yöntemleri hakkında gerçekten bilmeniz gereken tek şey, doğru `using` yönergeleri kullanarak uygulamanızda bunları nasıl kapsamına sokacağınızdır. Uygulamanızın bakış açısından, bir uzantı yöntemi ve normal bir örnek yöntemi aynıdır.  
  
 Uzantı yöntemleri hakkında daha fazla bilgi için [Uzantı Yöntemleri'ne](../../classes-and-structs/extension-methods.md)bakın. Standart sorgu işleçleri hakkında daha fazla bilgi [için, Standart Sorgu Operatörlerine Genel Bakış (C#)](./standard-query-operators-overview.md)bakın. Bazı LINQ sağlayıcıları, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]gibi ve, yanı sıra <xref:System.Collections.Generic.IEnumerable%601>diğer türleri için kendi standart sorgu operatörleri ve ek uzatma yöntemleri uygulamak.  
  
## <a name="lambda-expressions"></a>Lambda İfadeleri  
 Önceki örnekte, koşullu ifadenin`num % 2 == 0`( ) `Where` yönteme satır içi bağımsız `Where(num => num % 2 == 0).` değişken olarak geçirildiğine dikkat edin: Bu satır içi ifadeye lambda ifadesi denir. Aksi takdirde anonim bir yöntem veya genel bir temsilci veya bir ifade ağacı olarak daha hantal biçimde yazılması gereken kod yazmak için uygun bir yoldur. C#'da `=>` lambda operatörü "gider" olarak okunur. İşleticinin `num` solundaki giriş değişkeni sorgu `num` ifadesinde karşılık gelir. Derleyici, bunun genel `num` `numbers` <xref:System.Collections.Generic.IEnumerable%601> bir tür olduğunu bildiği için türünü çıkartabilir. Lambda gövdesi, sorgu sözdiziminde veya başka bir C# ifadesinde veya deyimindeki ifadeyle aynıdır; yöntem çağrıları ve diğer karmaşık mantık içerebilir. "İade değeri" sadece ifade sonucudur.  
  
 LINQ kullanmaya başlamak için lambdas'ı yoğun olarak kullanmanız gerekmez. Ancak, bazı sorgular yalnızca yöntem sözdizimi ile ifade edilebilir ve bunlardan bazıları lambda ifadeleri gerektirir. Lambdas'ı daha iyi tanıdıktan sonra, linq araç kutunuzda güçlü ve esnek bir araç olduklarını göreceksiniz. Daha fazla bilgi için [Lambda İfadeleri'ne](../../statements-expressions-operators/lambda-expressions.md)bakın.  
  
## <a name="composability-of-queries"></a>Sorgu Oluşturabilirliği  
 Önceki kod örneğinde, `OrderBy` `Where`''ye yapılan çağrıda nokta işleci kullanılarak yöntemin çağrıldığını unutmayın. `Where`filtreuygulanmış bir sıra `Orderby` üretir ve sonra bu sıraüzerinde sıralayarak çalışır. Sorgular bir `IEnumerable`döndürüldünden, yöntem çağrılarını birbirine zincirleyerek yöntem sözdiziminde oluşturursunuz. Sorgu sözdizimini kullanarak sorgu yazarken derleyicinin arka planda yaptığı budur. Ve bir sorgu değişkeni sorgunun sonuçlarını depolamadığından, sorguyu değiştirebilir veya yürütüldükten sonra bile istediğiniz zaman yeni bir sorgu için temel olarak kullanabilirsiniz.  
