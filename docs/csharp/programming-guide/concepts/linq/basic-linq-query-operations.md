---
title: "Temel LINQ Sorgu İşlemleri (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- orderby clause [LINQ in C#]
- ordering data [LINQ in C#]
- selecting data [LINQ in C#]
- queries [LINQ in C#], basic operations
- grouping data [LINQ in C#]
- data sources [LINQ in C#]
- sorting data [LINQ in C#]
- projections [LINQ in C#]
- filtering data [LINQ in C#]
- joining data [LINQ in C#]
- select clause [LINQ in C#]
- LINQ [C#], basic query operations
- join clause [LINQ in C#]
- group clause [LINQ in C#]
ms.assetid: a7ea3421-1cf4-4df7-832a-aa22fe6379e9
caps.latest.revision: "39"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c7a258ae8d85425abb6d1474d2cb01b02f6deb2e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="basic-linq-query-operations-c"></a>Temel LINQ Sorgu İşlemleri (C#)
Bu konuda kısa bir giriş sağlar [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu ifadeleri ve bazı tipik türleri sorguda gerçekleştirdiğiniz işlem. Daha ayrıntılı bilgi aşağıdaki konularda verilmiştir:  
  
 [LINQ Sorgu ifadeleri](../../../../csharp/programming-guide/linq-query-expressions/index.md)  
  
 [Standart sorgu işleçlerine genel bakış (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
  
 [İzlenecek yol: Sorguları C# ile yazma](../../../../csharp/programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)  
  
> [!NOTE]
>  SQL veya XQuery gibi bir sorgu dili ile bilginiz varsa, bu konunun en atlayabilirsiniz. Hakkında bilgi edinin "`from` yan tümcesi" yan tümcelerinde sırasını hakkında bilgi almak için sonraki bölümde [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu ifadeleri.  
  
## <a name="obtaining-a-data-source"></a>Bir Veri Kaynağı Elde Etme  
 İçinde bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu, ilk adımdır veri kaynağını belirtmek için. Kullanılabilmesi için C# çoğu programlama dilinde olduğu gibi bir değişkeni bildirilmelidir. İçinde bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu `from` yan tümcesi gelen ilk veri kaynağı sunmak için (`customers`) ve *aralık değişkeni* (`cust`).  
  
 [!code-csharp[csLINQGettingStarted#23](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_1.cs)]  
  
 Yineleme değişkeni aralık değişkeni benzer bir `foreach` sorgu ifadesinde gerçek bir yineleme gerçekleşir ancak bu döngü. Sorgu çalıştırıldığında, aralık değişkeni art arda gelen her öğe için bir başvuru olarak hizmet verecektir `customers`. Derleyici türünü çıkarımını çünkü `cust`, açıkça belirtmek zorunda değilsiniz. Ek aralık değişkeni sunulan tarafından bir `let` yan tümcesi. Daha fazla bilgi için bkz: [let tümcesi](../../../../csharp/language-reference/keywords/let-clause.md).  
  
> [!NOTE]
>  İçin genel olmayan veri kaynakları gibi <xref:System.Collections.ArrayList>, aralık değişkeni açıkça yazılmalıdır. Daha fazla bilgi için bkz: [nasıl yapılır: LINQ (C#) ile ArrayList sorgulama](../../../../csharp/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md) ve [from yan tümcesi](../../../../csharp/language-reference/keywords/from-clause.md).  
  
## <a name="filtering"></a>Filtreleme  
 Boole ifadesi şeklinde bir filtre uygulamak için en yaygın sorgu işlemi olabilir. Filtre yalnızca ifade doğru ise öğeleri döndürecek şekilde sorguyu neden olur. Sonuç kullanılarak üretilen `where` yan tümcesi. Filtre etkin kaynak dizisinden dışlamak için hangi öğelerin belirtir. Aşağıdaki örnekte, yalnızca `customers` bir adresi Londra'da sahip döndürülür.  
  
 [!code-csharp[csLINQGettingStarted#24](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_2.cs)]  
  
 Kullanabileceğiniz tanıdık C# mantıksal `AND` ve `OR` birçok ifadeleri gerekli olarak filtre olarak uygulamak için işleçleri `where` yan tümcesi. Örneğin, "Londra'dan" yalnızca Müşteriler döndürülecek `AND` adı olan "yazma aşağıdaki kodu Devon":  
  
 [!code-csharp[csLINQGettingStarted#25](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_3.cs)]  
  
 Londra veya Paris müşteriler döndürmek için aşağıdaki kodu yazabilirsiniz:  
  
 [!code-csharp[csLINQGettingStarted#26](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_4.cs)]  
  
 Daha fazla bilgi için bkz: [burada yan tümcesi](../../../../csharp/language-reference/keywords/where-clause.md).  
  
## <a name="ordering"></a>Sıralama  
 Genellikle döndürülen verileri sıralamak uygundur. `orderby` Yan tümcesi neden olacak öğeleri göre sıralanan türü için varsayılan karşılaştırıcı sıralanacak döndürülen dizideki. Örneğin, aşağıdaki sorguyu temel sonuçları sıralamak için Genişletilebilir `Name` özelliği. Çünkü `Name` bir dizedir varsayılan karşılaştırıcı alfabetik sıralama A'dan Z'ye gerçekleştirir.  
  
 [!code-csharp[csLINQGettingStarted#27](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_5.cs)]  
  
 Sonuçları Z'den A'ya, ters sırada sıralamak için kullanmak `orderby…descending` yan tümcesi.  
  
 Daha fazla bilgi için bkz: [orderby yan tümcesinin](../../../../csharp/language-reference/keywords/orderby-clause.md).  
  
## <a name="grouping"></a>Gruplandırma  
 `group` Yan tümcesi, belirttiğiniz bir anahtarı temel sonuçlarınızı gruplamanıza olanak sağlar. Örneğin sonuçları tarafından gruplandırılmalıdır belirtebilirsiniz `City` tek tek gruplarında Londra veya Paris tüm müşterilerden; böylece. Bu durumda, `cust.City` anahtardır.  
  
 [!code-csharp[csLINQGettingStarted#28](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_6.cs)]  
  
 Son zaman bir sorgu ile bir `group` yan tümcesi, sonuçlarınızı formun listeleri listesini alın. Her bir öğe listesi olan bir nesnedir bir `Key` üye ve bu anahtarın altında gruplanmış öğeleri listesi. Grup bir dizi üreten bir sorgu yineleme yaparken, iç içe bir kullanmalısınız `foreach` döngü. Her grup üzerinden dış döngüsü yineler ve iç döngüsü her grubun üyeleri üzerinde yineler.  
  
 Bir grup İşlem sonuçlarını başvurmalıdır, kullanabileceğiniz `into` daha fazla sorgulanabilir bir tanımlayıcı oluşturmak üzere anahtar sözcük. Aşağıdaki sorguda ikiden fazla müşteriler içeren gruplar döndürür:  
  
 [!code-csharp[csLINQGettingStarted#29](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_7.cs)]  
  
 Daha fazla bilgi için bkz: [group yan tümcesi](../../../../csharp/language-reference/keywords/group-clause.md).  
  
## <a name="joining"></a>Katılma  
 Birleştirme işlemleri oluşturmak dizileri arasındaki ilişkileri, veri kaynaklarında açıkça Modellenen değil. Örneğin müşteriler ve aynı konuma sahip dağıtıcıları bulmak için bir birleştirme gerçekleştirebilirsiniz. İçinde [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] `join` yan tümcesi her zaman çalışır veritabanı tablolarını yerine nesne koleksiyonları karşı doğrudan.  
  
 [!code-csharp[csLINQGettingStarted#36](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_8.cs)]  
  
 İçinde [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] kullanmak zorunda değil `join` SQL'de çünkü bunu sıklıkta yabancı anahtarları [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] nesne modelinde öğeleri koleksiyonu tutun özellikleri olarak temsil edilir. Örneğin, bir `Customer` nesnesini içeren koleksiyonu `Order` nesneleri. Bir birleştirme gerçekleştirmek yerine, noktalı gösterim kullanılarak siparişleri erişebilirsiniz:  
  
```  
from order in Customer.Orders...  
```  
  
 Daha fazla bilgi için bkz: [JOIN yan tümcesi](../../../../csharp/language-reference/keywords/join-clause.md).  
  
## <a name="selecting-projections"></a>Seçme (Tahminler)  
 `select` Yan tümcesi sorgu sonuçlarını üretir ve "Şekil" ya da her döndürülen öğe türünü belirtir. Örneğin, sonuçlarınızı, tam oluşacağını belirtebilirsiniz `Customer` nesneleri, yalnızca bir üye, üyelerin bir alt kümesini veya bazı tamamen farklı bir sonuç türü göre bir hesaplama veya yeni nesne oluşturma. Zaman `select` yan tümcesi üreten bir kopyasını kaynak öğenin dışında işlemi adlı bir *projeksiyon*. Verileri dönüştürmek için tahminleri güçlü kullanımıdır [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu ifadeleri. Daha fazla bilgi için bkz: [LINQ (C#) ile veri dönüştürmeler](../../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md) ve [select yan tümcesi](../../../../csharp/language-reference/keywords/select-clause.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# üzerinde LINQ ile çalışmaya başlama](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [LINQ Sorgu ifadeleri](../../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [İzlenecek yol: Sorguları C# ile yazma](../../../../csharp/programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)  
 [Sorgu anahtar sözcükleri (LINQ)](../../../../csharp/language-reference/keywords/query-keywords.md)  
 [Anonim türler](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
