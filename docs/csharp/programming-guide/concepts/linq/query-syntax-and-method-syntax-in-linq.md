---
title: LINQ'te Sorgu Sözdizimi ve Yöntem Sözdizimi (C#)
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], query syntax vs. method syntax
- queries [LINQ in C#], syntax comparisons
ms.assetid: eedd6dd9-fec2-428c-9581-5b8783810ded
ms.openlocfilehash: 6b943da442d2ec1210911cb9f4b6a0d56c7216d7
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2018
ms.locfileid: "43258765"
---
# <a name="query-syntax-and-method-syntax-in-linq-c"></a>LINQ'te Sorgu Sözdizimi ve Yöntem Sözdizimi (C#)
Çoğu sorgularda tanıtım dil ile tümleşik sorgu ([!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]) belgeleri LINQ Sorgu bildirim temelli söz dizimini kullanarak yazılır. Ancak, kod yeniden derlendiğinde sorgu söz dizimi yöntem çağrıları için .NET ortak dil çalışma zamanı (CLR) içine çevrilmelidir. Bu yöntem çağrıları gibi adlara sahip standart sorgu işleçleri çağırma `Where`, `Select`, `GroupBy`, `Join`, `Max`, ve `Average`. Sorgu söz dizimi yerine doğrudan yöntem sözdizimini kullanarak bunları çağırabilirsiniz.  
  
 Anlamsal olarak sorgu sözdizimi ve yöntem sözdizimi aynıdır, ancak çoğu kişi sorgu söz dizimi daha basit ve okuması daha kolay bulun. Bazı sorgular yöntemi çağrıları olarak ifade edilmelidir. Örneğin, belirtilen bir koşulla eşleşen öğe sayısını alır. bir sorgu ifade etmek için bir yöntem çağrısının kullanmanız gerekir. Ayrıca, bir kaynak dizideki en büyük değer olan öğeyi alır. bir sorgu için bir yöntem çağrısının kullanmanız gerekir. Standart sorgu işleçleri için başvuru belgeleri <xref:System.Linq> ad alanı genellikle yöntemi sözdizimini kullanır. Bu nedenle, bile yazmaya başlama [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgular, bu yöntem sözdizimi sorguları ve sorgu ifadeleri kendilerini kullanma hakkında bilgi sahibi olmanız faydalı.  
  
## <a name="standard-query-operator-extension-methods"></a>Standart Sorgu İşleci Genişletme Yöntemleri  
 Aşağıdaki örnek, basit bir gösterir *sorgu ifadesi* ve anlamsal olarak eşdeğer olarak yazılmış sorguyu bir *metot tabanlı sorgu*.  
  
 [!code-csharp[csLINQGettingStarted#22](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/query-syntax-and-method-syntax-in-linq_1.cs)]  
  
 İki örnek çıktısı aynıdır. Sorgu değişkeninin türü her iki formu içinde aynı olduğunu görebilirsiniz: <xref:System.Collections.Generic.IEnumerable%601>.  
  
 Metot tabanlı sorgu anlamak için bunu daha yakından inceleyelim. İfade sağ tarafında dikkat `where` yan tümcesi artık ifade bir örnek yöntemi `numbers` geri çağırma, aynı nesne türü olan `IEnumerable<int>`. Genel ile biliyorsanız <xref:System.Collections.Generic.IEnumerable%601> arabirimi, tanıdığınız değil sahip bir `Where` yöntemi. Ancak, Visual Studio IDE içindeki IntelliSense tamamlanma listesi çağırmak, göreceğiniz yalnızca bir `Where` yöntemi, ancak diğer birçok yöntem gibi `Select`, `SelectMany`, `Join`, ve `Orderby`. Tüm standart sorgu işleçleri şunlardır.  
  
 ![Standart sorgu işleçleri IntelliSense içinde](../../../../csharp/programming-guide/concepts/linq/media/standardqueryops.png "StandardQueryOps")  
  
 Görünüyor ancak gibi <xref:System.Collections.Generic.IEnumerable%601> bu değildir durum aslında bu ek yöntemleri içerecek şekilde tanımlandı. Standart sorgu işleçleri yöntemi olarak adlandırılan yeni bir tür olarak uygulanan *genişletme yöntemleri*. Uzantı yöntemleri "Varolan türü genişletmesi"; türün örnek yöntemleri değilmiş gibi bunlar çağrılabilir. Standart sorgu işleçlerini genişletme <xref:System.Collections.Generic.IEnumerable%601> ve diğer bir deyişle neden yazabilirsiniz `numbers.Where(...)`.  
  
 Kullanmaya başlamak için [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], gerçekten uzantı yöntemleri hakkında bilmeniz gereken tek şey bunları uygulamanızda kapsama doğru kullanarak nasıl getireceğinizi `using` yönergeleri. Uygulamanızın açısından bakıldığında, bir genişletme yöntemi ve normal örneğinde yöntemi aynıdır.  
  
 Uzantı yöntemleri hakkında daha fazla bilgi için bkz. [genişletme yöntemleri](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md). Standart sorgu işleçleri hakkında daha fazla bilgi için bkz. [standart sorgu işleçlerine genel bakış (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md). Bazı [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sağlayıcıları gibi [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] ve [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], kendi standart sorgu işleçleri ve yanı sıra diğer türleri için ek genişletme yöntemleri uygulamak <xref:System.Collections.Generic.IEnumerable%601>.  
  
## <a name="lambda-expressions"></a>Lambda İfadeleri  
 Önceki örnekte, dikkat koşullu ifade (`num % 2 == 0`) satır içi bağımsız değişken olarak geçirilen `Where` yöntemi: `Where(num => num % 2 == 0).` bu satır içi ifade bir lambda ifadesi adı verilir. Aksi takdirde bir anonim yöntem veya temsilci veya ifade ağacı olarak daha kullanışsız biçimde yazılmış olması gereken kod yazmak için kullanışlı bir yoldur. C# `=>` "giden" olarak okunur lambda işleci. `num` İşlecin solda karşılık gelen giriş değişkendir `num` sorgu ifadesinde. Derleyici, tür çıkarımını `num` , bildiğinden `numbers` genel <xref:System.Collections.Generic.IEnumerable%601> türü. Lambda gövdesi tıpkı sorgu söz dizimi veya herhangi bir C# ifadesi veya deyimi deyim olur; Yöntem çağrıları ve diğer karmaşık bir mantık içerebilir. "Dönüş değeri" yalnızca ifade sonucudur.  
  
 Kullanmaya başlamak için [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], lambdalar kapsamlı bir şekilde kullanmak zorunda değilsiniz. Ancak, bazı sorgular yalnızca yöntemi söz diziminde ifade ve bazıları ise lambda ifadeleri gerektirir. Lambda ifadeleri ile daha tanıdık sonra güçlü ve esnek bir aracı olduğunu göreceksiniz, [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] araç kutusu. Daha fazla bilgi için [Lambda ifadeleri](../../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
## <a name="composability-of-queries"></a>Sorgu Oluşturabilirliği  
 Önceki kod örneğinde unutmayın `OrderBy` yöntemi çağrısında dot işleci kullanılarak çağrıldığında `Where`. `Where` filtrelenmiş bir dizi üretir ve ardından `Orderby` sıralama tarafından o dizi üzerinde çalışır. Sorguları döndürdüğünden bir `IEnumerable`, siz bunları yöntemi sözdiziminde birlikte yöntem çağrıları zinciri tarafından oluşturun. Sorgu söz dizimi kullanılarak sorgular yazdığınızda derleyici arka planda ne yaptığını budur. Ve bir sorgu değişkeni sorgu sonuçlarını depolamaz olduğundan, değiştirin veya hatta yürütüldükten sonra istediğiniz zaman yeni bir sorgu için temel olarak kullanmak.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C#'de LINQ Kullanmaya Başlama](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
