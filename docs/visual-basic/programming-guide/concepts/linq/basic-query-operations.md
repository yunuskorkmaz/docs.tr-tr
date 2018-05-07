---
title: Temel Sorgu İşlemleri (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- data sources [LINQ in Visual Basic]
- Join clause [LINQ in Visual Basic]
- ordering data [LINQ in Visual Basic]
- projections [LINQ in Visual Basic]
- LINQ [Visual Basic], query operations
- Order By clause [LINQ in Visual Basic]
- joining data [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], basic operations
- selecting data [LINQ in Visual Basic]
- Group By clause [LINQ in Visual Basic]
- grouping data [LINQ in Visual Basic]
- Select clause [LINQ in Visual Basic]
ms.assetid: 1146f6d0-fcb8-4f4d-8223-c9db52620d21
ms.openlocfilehash: 5587a60e97464324659b325e38a18ac25488d30d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="basic-query-operations-visual-basic"></a>Temel Sorgu İşlemleri (Visual Basic)
Bu konu kısa bir giriş sağlar [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] ifadeleri Visual Basic'te ve bazı tipik türleri sorguda gerçekleştirdiğiniz işlem. Daha fazla bilgi için aşağıdaki konulara bakın:  
  
 [Visual Basic'de LINQ'e giriş](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
  
 [Sorgular](../../../../visual-basic/language-reference/queries/queries.md)  
  
 [İzlenecek yol: Visual Basic'de sorgu yazma](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md)  
  
## <a name="specifying-the-data-source-from"></a>Veri Kaynağını (Kimden) Belirtme  
 İçinde bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu, ilk adımdır sorgulamak istediğiniz veri kaynağını belirlemek için. Bu nedenle, `From` yan tümcesinin sorgudaki her zaman gelen ilk. Sorgu işleçleri seçin ve kaynak türüne göre sonuç şekil.  
  
 [!code-vb[VbLINQBasicOps#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_1.vb)]  
  
 `From` Yan tümcesi veri kaynağını belirtir `customers`ve bir *aralık değişkeni*, `cust`. Gerçek bir yineleme sorgu ifadesinde oluşur aralık değişkeni bir döngü yineleme değişkeni gibi olmasıdır. Ne zaman sorgu yürütüldüğünde, genellikle kullanarak bir `For Each` aralık değişkeni döngü, hizmet art arda gelen her öğe için bir başvuru olarak `customers`. Derleyici türünü çıkarımını çünkü `cust`, açıkça belirtmek zorunda değilsiniz. İle ve açık yazarak olmadan yazılan sorguları örnekleri için bkz: [(Visual Basic) sorgu işlemlerinde tür ilişkileri](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md).  
  
 Nasıl kullanılacağı hakkında daha fazla bilgi için `From` Visual Basic'te yan tümcesine bakın [From yan tümcesi](../../../../visual-basic/language-reference/queries/from-clause.md).  
  
## <a name="filtering-data-where"></a>Veri Filtreleme (Yeri)  
 Büyük olasılıkla en yaygın sorgu işlemi Boole ifadesi şeklinde bir filtre uygulanıyor. Sorgu daha sonra yalnızca ifade doğru ise öğeleri döndürür. A `Where` yan tümcesi filtreleme gerçekleştirmek için kullanılır. Filtre hangi öğelerin elde edilen sırayla dahil etmek için veri kaynağı belirtir. Aşağıdaki örnekte, Londra'daki bir adresi olan müşteriler dahil edilir.  
  
 [!code-vb[VbLINQBasicOps#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_2.vb)]  
  
 Mantıksal işleçler gibi kullanabilir `And` ve `Or` filtre ifadelerinde birleştirmek için bir `Where` yan tümcesi. Örneğin, yalnızca Londra'dan olan ve Devon adı olan müşteriler döndürmek için aşağıdaki kodu kullanın:  
  
```vb  
Where cust.City = "London" And cust.Name = "Devon"   
```  
  
 Londra veya Paris müşteriler döndürmek için aşağıdaki kodu kullanın:  
  
```vb  
Where cust.City = "London" Or cust.City = "Paris"   
```  
  
 Nasıl kullanılacağı hakkında daha fazla bilgi için `Where` Visual Basic'te yan tümcesine bakın [Where yan tümcesi](../../../../visual-basic/language-reference/queries/where-clause.md).  
  
## <a name="ordering-data-order-by"></a>Veri Sıralama (Sıralama Ölçütü)  
 Genellikle, döndürülen verileri belirli bir sırada sıralayın uygundur. `Order By` Yan tümcesi neden olacak öğeleri belirtilen bir alan veya alanlar sıralanacak döndürülen dizideki. Örneğin, aşağıdaki sorguyu temel sonuçlarını sıralar `Name` özelliği. Çünkü `Name` bir dizedir döndürülen verileri A'dan Z'ye alfabetik olarak sıralanır.  
  
 [!code-vb[VbLINQBasicOps#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_3.vb)]  
  
 Sonuçları Z'den A'ya, ters sırada sıralamak için kullanmak `Order By...Descending` yan tümcesi. Varsayılan değer `Ascending` ne zaman `Ascending` ya da `Descending` belirtilir.  
  
 Nasıl kullanılacağı hakkında daha fazla bilgi için `Order By` Visual Basic'te yan tümcesine bakın [Order By yan tümcesi](../../../../visual-basic/language-reference/queries/order-by-clause.md).  
  
## <a name="selecting-data-select"></a>Verileri Seçme (Seçim)  
 `Select` Yan tümcesi, form ve döndürülen öğelerinin içeriğini belirtir. Örneğin, sonuçlarınızı, tam oluşacağını belirtebilirsiniz `Customer` nesneleri, yalnızca bir `Customer` özelliği, bir alt özellikler kümesini, çeşitli veri kaynakları veya bazı yeni sonuç türü özelliklerinden bir birleşimini temel üzerinde bir hesaplama. Zaman `Select` yan tümcesi üreten bir kopyasını kaynak öğenin dışında işlemi adlı bir *projeksiyon*.  
  
 Tam oluşan bir koleksiyon almak için `Customer` nesneleri, aralık değişkeni seçin:  
  
 [!code-vb[VbLINQBasicOps#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_4.vb)]  
  
 Varsa bir `Customer` örneğidir fazla alan sahip büyük bir nesne ve almak istediğiniz tüm adı, seçebileceğiniz `cust.Name`, aşağıdaki örnekte gösterildiği gibi. Yerel türü çıkarımı tanıdığı bu sonuç türü bir koleksiyonundan değiştirir `Customer` dizeleri koleksiyonu nesnelere.  
  
 [!code-vb[VbLINQBasicOps#5](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_5.vb)]  
  
 Birden çok alan veri kaynağından seçmek için iki seçeneğiniz vardır:  
  
-   İçinde `Select` yan tümcesi, sonuçta dahil etmek istediğiniz alanları belirtin. Derleyici, bu alanlar olarak özellikleri olan anonim bir tür tanımlayacaksınız. Daha fazla bilgi için bkz: [anonim türler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
     Aşağıdaki örnekte döndürülen öğeler anonim bir türün örneklerinin olduğundan, türüne adıyla başka bir yerde kodunuzda başvuruda bulunamaz. Derleyici tarafından atanan adı türü için normal Visual Basic kodunda geçerli olmayan karakterler içeriyor. Aşağıdaki örnekte, sorgu tarafından döndürülen koleksiyondaki öğe `londonCusts4` anonim bir türün örnekleri  
  
     [!code-vb[VbLINQBasicOps#6](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_6.vb)]  
  
     -veya-  
  
-   Sonucunda dahil oluşturmak ve türünün örneklerini başlatmak istediğiniz belirli alanları içeren adlandırılmış bir tür tanımlama `Select` yan tümcesi. Döndürülen koleksiyon dışındaki tek tek sonuç kullanmanız gerektiğinde veya bunları yöntem çağrılarını parametre olarak geçirmek varsa bu seçeneği kullanın. Türü `londonCusts5` IEnumerable (Of NamePhone) aşağıdaki örnekte olduğu.  
  
     [!code-vb[VbLINQBasicOps#7](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_7.vb)]  
  
     [!code-vb[VbLINQBasicOps#8](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_8.vb)]  
  
 Nasıl kullanılacağı hakkında daha fazla bilgi için `Select` Visual Basic'te yan tümcesine bakın [Select tümcesi](../../../../visual-basic/language-reference/queries/select-clause.md).  
  
## <a name="joining-data-join-and-group-join"></a>Veri Katma (Katma ve Grup Katma)  
 Birden çok veri kaynağında birleştirebilirsiniz `From` çeşitli şekillerde yan tümcesi. Örneğin, aşağıdaki kod iki veri kaynaklarını kullanır ve her ikisi de sonuç özelliklerinden örtük olarak birleştirir. Sorgu son adları sesli bir harfle başlayan Öğrenciler seçer.  
  
 [!code-vb[VbLINQBasicOps#9](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_9.vb)]  
  
> [!NOTE]
>  Oluşturulan Öğrenciler listesiyle birlikte bu kodu çalıştırmak [nasıl yapılır: öğelerinin listesi oluşturma](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).  
  
 `Join` Sözcüktür eşdeğer bir `INNER JOIN` SQL. İki koleksiyonlarında bulunan öğeler arasında eşleşen anahtar değerleri temel alarak iki koleksiyon birleştirir. Sorgu anahtar değerleriyle eşleşen koleksiyon öğelerinin bir bölümünü veya tümünü döndürür. Örneğin, aşağıdaki kod, önceki örtük katılma eylem çoğaltır.  
  
 [!code-vb[VbLINQBasicOps#10](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_10.vb)]  
  
 `Group Join` tek bir hiyerarşik koleksiyon koleksiyonlara tıpkı birleştiren bir `LEFT JOIN` SQL. Daha fazla bilgi için bkz: [JOIN yan tümcesi](../../../../visual-basic/language-reference/queries/join-clause.md) ve [Grup JOIN yan tümcesi](../../../../visual-basic/language-reference/queries/group-join-clause.md).  
  
## <a name="grouping-data-group-by"></a>Verileri Gruplandırma (Gruplandırma Ölçütü)  
 Ekleyebileceğiniz bir `Group By` sorgu sonucu öğe bir veya daha fazla alanlara göre öğeleri gruplandırmak için yan tümcesi. Örneğin, aşağıdaki kodu Öğrenciler sınıfı yıla göre gruplandırır.  
  
 [!code-vb[VbLINQBasicOps#11](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_11.vb)]  
  
 Oluşturulan Öğrenciler listesini kullanarak bu kodu çalıştırmak, [nasıl yapılır: öğelerinin listesi oluşturma](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md), çıkışı `For Each` ifadesi:  
  
 Yıl: alt düzey  
  
 Tucker, Michael  
  
 Garcia, Hugo  
  
 Garcia, Gamze  
  
 Tucker, Lance  
  
 Yıl: Kıdemli  
  
 Omelchenko, Svetlana  
  
 Osada, Michiko  
  
 Fakhouri, Fadi  
  
 Feng, Hanying  
  
 Adams, Terry  
  
 Yıl: Freshman  
  
 Mortensen, Sven  
  
 Garcia, Cesar  
  
 Aşağıdaki kodda gösterildiği değişim sınıfı yıl sıralar ve ardından Öğrenciler her yıl içinde son adına göre sıralar.  
  
 [!code-vb[VbLINQBasicOps#12](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_12.vb)]  
  
 Hakkında daha fazla bilgi için `Group By`, bkz: [Grup By yan tümcesi](../../../../visual-basic/language-reference/queries/group-by-clause.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Collections.Generic.IEnumerable%601>  
 [Visual Basic'te Lınq'e Başlarken](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [Sorgular](../../../../visual-basic/language-reference/queries/queries.md)  
 [Standart sorgu işleçlerine genel bakış (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
