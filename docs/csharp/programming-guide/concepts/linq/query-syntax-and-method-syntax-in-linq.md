---
title: LINQ'te Sorgu Sözdizimi ve Yöntem Sözdizimi (C#)
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], query syntax vs. method syntax
- queries [LINQ in C#], syntax comparisons
ms.assetid: eedd6dd9-fec2-428c-9581-5b8783810ded
ms.openlocfilehash: 6b943da442d2ec1210911cb9f4b6a0d56c7216d7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33336358"
---
# <a name="query-syntax-and-method-syntax-in-linq-c"></a>LINQ'te Sorgu Sözdizimi ve Yöntem Sözdizimi (C#)
Çoğu sorgularda giriş dil ile tümleşik sorgu ([!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]) belgeleri LINQ bildirim temelli sorgu sözdizimi kullanılarak yazılır. Bununla birlikte, kod derlendiğinde sorgu söz dizimi .NET ortak dil çalışma zamanı (CLR) için yöntem çağrılarını içine çevrilmelidir. Bu yöntem çağrılarını gibi adlara sahip standart sorgu işleçleri çağırma `Where`, `Select`, `GroupBy`, `Join`, `Max`, ve `Average`. Sorgu sözdizimi yerine doğrudan yöntemi sözdizimini kullanarak bunları çağırabilirsiniz.  
  
 Sorgu sözdizimi ve yöntem sözdizimi anlam olarak aynıdır, ancak çoğu kişi sorgu söz dizimi daha basit ve okuması daha kolay bulmak. Bazı sorgular yöntem çağrılarını ifade edilmesi gerekir. Örneğin, belirli bir koşul eşleşen öğe sayısını alır. bir sorgu ifade etmek için bir yöntem çağrısı kullanmanız gerekir. Ayrıca, bir kaynak dizisinde en büyük değer olan öğeyi alır. bir sorgu için bir yöntem çağrısı kullanmanız gerekir. Standart sorgu işleçleri için başvuru belgeleri <xref:System.Linq> ad alanı genellikle yöntemi sözdizimini kullanır. Bu nedenle, bile yazma Başlarken [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgular, bu, sorgular ve sorgu ifadeleri kendilerini yöntemi sözdizimini kullanma hakkında bilgi sahibi olmanız yararlıdır.  
  
## <a name="standard-query-operator-extension-methods"></a>Standart Sorgu İşleci Genişletme Yöntemleri  
 Aşağıdaki örnekte basit bir *sorgu ifadesi* ve anlam olarak eşdeğer sorgu olarak yazılmış bir *yöntemi tabanlı sorgu*.  
  
 [!code-csharp[csLINQGettingStarted#22](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/query-syntax-and-method-syntax-in-linq_1.cs)]  
  
 İki örnek çıkışı aynıdır. Sorgu değişkeninin türü hem formlarında aynı olduğunu görebilirsiniz: <xref:System.Collections.Generic.IEnumerable%601>.  
  
 Yöntem temelli sorgu anlamak için onu daha yakından inceleyelim. İfadesinin sağ tarafta dikkat `where` yan tümcesi şimdi ifade bir örnek yöntemi olarak `numbers` geri çağırma, aynı nesne türü olan `IEnumerable<int>`. Genel ile biliyorsanız <xref:System.Collections.Generic.IEnumerable%601> arabirimi, bildiğiniz değil sahip bir `Where` yöntemi. Ancak, Visual Studio IDE içinde IntelliSense tamamlanma listesi çağırma, göreceğiniz yalnızca bir `Where` yöntemi, ancak gibi birçok diğer yöntemler `Select`, `SelectMany`, `Join`, ve `Orderby`. Tüm standart sorgu işleçleri bunlar.  
  
 ![IntelliSense içinde standart sorgu işleçleri](../../../../csharp/programming-guide/concepts/linq/media/standardqueryops.png "StandardQueryOps")  
  
 Görünüyor ancak gibi <xref:System.Collections.Generic.IEnumerable%601> bu değil durumu aslında bu ek yöntemleri eklemek için tanımlandı. Standart sorgu işleçleri yöntemi olarak adlandırılan yeni bir tür olarak uygulanan *genişletme yöntemleri*. Genişletme yöntemleri "mevcut bir türle genişletmek"; türün örnek yöntemleri değilmiş gibi bunlar çağrılabilir. Standart sorgu işleçleri genişletmek <xref:System.Collections.Generic.IEnumerable%601> ve diğer bir deyişle neden yazabilirsiniz `numbers.Where(...)`.  
  
 Kullanmaya başlamak için [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], gerçekten uzantı yöntemleri hakkında bilmeniz gereken tek şey bunları uygulamanız kapsamında doğru kullanarak duruma getirmek nasıl `using` yönergeleri. Uygulamanızın açısından bakıldığında, bir genişletme yöntemi ve normal örnek yöntemi aynıdır.  
  
 Uzantı yöntemleri hakkında daha fazla bilgi için bkz: [genişletme yöntemleri](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md). Standart sorgu işleçleri hakkında daha fazla bilgi için bkz: [standart sorgu işleçlerine genel bakış (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md). Bazı [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sağlayıcıları gibi [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] ve [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], kendi standart sorgu işleçleri ve yanı sıra diğer türleri için ek genişletme yöntemleri uygulamak <xref:System.Collections.Generic.IEnumerable%601>.  
  
## <a name="lambda-expressions"></a>Lambda İfadeleri  
 Önceki örnekte dikkat koşullu ifade (`num % 2 == 0`) satır içi bağımsız değişken olarak geçirilen `Where` yöntemi: `Where(num => num % 2 == 0).` bu satır içi ifade lambda ifadesi olarak adlandırılır. Aksi takdirde daha kullanışsız formunda anonim bir yöntemi veya genel temsilcisi veya bir ifade ağacına yazılmış zorunda kod yazmak için uygun bir yoludur. C# `=>` "giden" olarak okuma lambda işleci. `num` İşlecinin sol tarafta karşılık gelen giriş değişkenidir `num` sorgu ifadesinde. Derleyici türünü çıkarımını `num` , bildiği için `numbers` genel <xref:System.Collections.Generic.IEnumerable%601> türü. Lambda tıpkı sorgu söz dizimi veya herhangi bir C# ifadesi veya deyimi ifade olarak gövdesidir; Yöntem çağrıları ve diğer karmaşık bir mantık içerebilir. "Dönüş değerini" yalnızca ifade sonucudur.  
  
 Kullanmaya başlamak için [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], Lambda'lar yaygın kullanmak zorunda değil. Ancak, bazı sorgular yalnızca yöntemi sözdiziminde ifade ve bazıları lambda ifadeleri gerektirir. Lambda'lar ile daha tanıdık sonra güçlü ve esnek aracında olduğunu göreceksiniz, [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] araç. Daha fazla bilgi için bkz: [Lambda ifadeleri](../../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
## <a name="composability-of-queries"></a>Sorgu Oluşturabilirliği  
 Önceki kod örneğinde unutmayın `OrderBy` yöntemi çağrılır çağrıda dot işleci kullanılarak `Where`. `Where` Filtre uygulanmış bir sıra oluşturur ve ardından `Orderby` sıralama tarafından bu dizisi üzerinde çalışır. Sorguları döndürür çünkü bir `IEnumerable`, siz bunları yöntemi sözdiziminde yöntem çağrılarını birlikte zincirleme tarafından oluştur. Sorgu sözdizimi kullanılarak sorguları yazdığınızda derleyici arka planda ne yaptığını budur. Ve bir sorgu değişkeni sorgu sonuçlarını depolamaz çünkü değiştirin veya hatta yürütüldükten sonra herhangi bir zamanda yeni bir sorgu için temel olarak kullanmak.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C#'de LINQ Kullanmaya Başlama](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
