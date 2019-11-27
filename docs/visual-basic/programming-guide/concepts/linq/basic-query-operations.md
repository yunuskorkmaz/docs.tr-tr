---
title: Temel Sorgu İşlemleri
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
ms.openlocfilehash: e9a646d60bb22507f4c6bcbcdf9222fd0ed18f02
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345758"
---
# <a name="basic-query-operations-visual-basic"></a>Temel Sorgu İşlemleri (Visual Basic)
Bu konu, Visual Basic [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] ifadelerine ve bir sorguda gerçekleştirdiğiniz bazı tipik işlem türlerinden bazılarına kısa bir giriş sağlar. Daha fazla bilgi için aşağıdaki konulara bakın:  
  
 [Visual Basic LINQ 'e giriş](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
  
 [Sorgular](../../../../visual-basic/language-reference/queries/index.md)  
  
 [İzlenecek yol: Visual Basic sorguları yazma](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md)  
  
## <a name="specifying-the-data-source-from"></a>Veri Kaynağını (Kimden) Belirtme  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgusunda, ilk adım sorgulamak istediğiniz veri kaynağını belirtmektir. Bu nedenle, bir sorgudaki `From` yan tümcesi her zaman ilk olarak gelir. Sorgu işleçleri, kaynağın türüne göre sonucu seçin ve şekillendirin.  
  
 [!code-vb[VbLINQBasicOps#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#1)]  
  
 `From` yan tümcesi veri kaynağını, `customers`ve `cust`bir *Aralık değişkenini*belirtir. Aralık değişkeni, bir sorgu ifadesinde gerçek yineleme gerçekleşmediğinde bir döngü yineleme değişkeni gibidir. Sorgu yürütüldüğünde, genellikle bir `For Each` döngüsü kullanılarak Aralık değişkeni `customers`birbirini izleyen her öğe için bir başvuru olarak görev yapar. Derleyici `cust`türünü çıkarsanbildiğinden, açıkça belirtmeniz gerekmez. Açık yazma olmadan ve ile yazılan sorguların örnekleri için bkz. [sorgu Işlemlerinde tür ilişkileri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md).  
  
 Visual Basic `From` yan tümcesinin nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [from yan tümcesi](../../../../visual-basic/language-reference/queries/from-clause.md).  
  
## <a name="filtering-data-where"></a>Veri Filtreleme (Yeri)  
 Büyük olasılıkla en yaygın sorgu işlemi, bir filtreyi Boole ifadesi biçiminde uyguluyor. Sorgu daha sonra yalnızca ifadenin true olduğu öğeleri döndürür. Filtreleme işlemini gerçekleştirmek için bir `Where` yan tümcesi kullanılır. Filtre, veri kaynağındaki hangi öğelerin sonuç dizisine ekleneceğini belirtir. Aşağıdaki örnekte, yalnızca Londra 'da bir adresi olan müşteriler dahil edilmiştir.  
  
 [!code-vb[VbLINQBasicOps#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#2)]  
  
 Filtre ifadelerini bir `Where` yan tümcesinde birleştirmek için `And` ve `Or` gibi mantıksal işleçleri kullanabilirsiniz. Örneğin, yalnızca Londra 'dan ve adı Devon olan müşterileri döndürmek için aşağıdaki kodu kullanın:  
  
```vb  
Where cust.City = "London" And cust.Name = "Devon"   
```  
  
 Londra veya Paris 'ten müşterileri döndürmek için aşağıdaki kodu kullanın:  
  
```vb  
Where cust.City = "London" Or cust.City = "Paris"   
```  
  
 Visual Basic `Where` yan tümcesinin nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [WHERE yan tümcesi](../../../../visual-basic/language-reference/queries/where-clause.md).  
  
## <a name="ordering-data-order-by"></a>Veri Sıralama (Sıralama Ölçütü)  
 Genellikle döndürülen verileri belirli bir sıraya göre sıralamak kullanışlıdır. `Order By` yan tümcesi, döndürülen dizideki öğelerin belirtilen alan veya alanlar üzerinde sıralanmasına neden olur. Örneğin, aşağıdaki sorgu sonuçları `Name` özelliğine göre sıralar. `Name` bir dize olduğundan, döndürülen veriler alfabetik olarak, A 'dan Z 'ye sıralanır.  
  
 [!code-vb[VbLINQBasicOps#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#3)]  
  
 Sonuçları Z 'den A 'ya doğru sırada sıralamak için `Order By...Descending` yan tümcesini kullanın. `Ascending` veya `Descending` belirtilmediğinde varsayılan değer `Ascending`.  
  
 Visual Basic `Order By` yan tümcesinin nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [order by yan tümcesi](../../../../visual-basic/language-reference/queries/order-by-clause.md).  
  
## <a name="selecting-data-select"></a>Verileri Seçme (Seçim)  
 `Select` yan tümcesi döndürülen öğelerin formunu ve içeriğini belirtir. Örneğin, sonuçlarınızın tam `Customer` nesnelerden, tek bir `Customer` özelliğinden, özelliklerin bir alt kümesinden, çeşitli veri kaynaklarından özelliklerin bir birleşimini veya bir hesaplamayı temel alan bazı yeni sonuç türlerini içerip içermediğini belirtebilirsiniz. `Select` yan tümcesi kaynak öğenin bir kopyası dışında bir şey üretirse, işleme bir *projeksiyon*olarak adlandırılır.  
  
 Bütün `Customer` nesnelerden oluşan bir koleksiyonu almak için, Aralık değişkeninin kendisini seçin:  
  
 [!code-vb[VbLINQBasicOps#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#4)]  
  
 `Customer` bir örnek çok fazla alan içeren büyük bir nesnedir ve almak istediğiniz tümü adı ise, aşağıdaki örnekte gösterildiği gibi `cust.Name`seçebilirsiniz. Yerel tür çıkarımı, bu, sonuç türünü bir `Customer` nesneleri koleksiyonundan dizeler koleksiyonuna değiştirinin algılar.  
  
 [!code-vb[VbLINQBasicOps#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#5)]  
  
 Veri kaynağından birden çok alan seçmek için iki seçeneğiniz vardır:  
  
- `Select` yan tümcesinde, sonuca dahil etmek istediğiniz alanları belirtin. Derleyici, özellikleri olarak bu alanlara sahip anonim bir tür tanımlayacaktır. Daha fazla bilgi için bkz. [anonim türler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
     Aşağıdaki örnekteki döndürülen öğeler anonim bir türün örnekleri olduğundan, kodunuzun başka bir yerinde ada göre türe başvuramaz. Tür için derleyici tarafından belirlenen ad, normal Visual Basic kodunda geçerli olmayan karakterler içeriyor. Aşağıdaki örnekte, `londonCusts4` içindeki sorgu tarafından döndürülen koleksiyonda bulunan öğeler anonim bir tür örnekleridir  
  
     [!code-vb[VbLINQBasicOps#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#6)]  
  
     veya  
  
- Sonuca dahil etmek istediğiniz belirli alanları içeren adlandırılmış bir tür tanımlayın ve `Select` yan tümcesindeki tür örneklerini oluşturun ve başlatın. Bu seçeneği yalnızca, sonuçları döndürüldüğünden koleksiyonun dışında veya yöntem çağrılarında parametre olarak geçirmeniz gerekiyorsa kullanın. Aşağıdaki örnekteki `londonCusts5` türü IEnumerable (NamePhone).  
  
     [!code-vb[VbLINQBasicOps#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#7)]  
  
     [!code-vb[VbLINQBasicOps#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#8)]  
  
 Visual Basic `Select` yan tümcesinin nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [Select yan tümcesi](../../../../visual-basic/language-reference/queries/select-clause.md).  
  
## <a name="joining-data-join-and-group-join"></a>Veri Katma (Katma ve Grup Katma)  
 `From` yan tümcesinde birden fazla veri kaynağını çeşitli yollarla birleştirebilirsiniz. Örneğin, aşağıdaki kod iki veri kaynağını kullanır ve sonuç olarak her ikisinin de özelliklerini örtülü olarak birleştirir. Sorgu, son adları sesli harf ile başlayan öğrencileri seçer.  
  
 [!code-vb[VbLINQBasicOps#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#9)]  
  
> [!NOTE]
> Bu kodu, [nasıl yapılır: öğe listesi oluşturma](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)bölümünde oluşturulan öğrenciler listesiyle çalıştırabilirsiniz.  
  
 `Join` anahtar sözcüğü SQL içindeki bir `INNER JOIN` eşdeğerdir. İki koleksiyonu iki koleksiyonda bulunan öğeler arasında eşleşen anahtar değerlerine dayalı olarak birleştirir. Sorgu, eşleşen anahtar değerleri olan koleksiyon öğelerinin tümünü veya bir bölümünü döndürür. Örneğin, aşağıdaki kod önceki örtük birleşimin eylemini yineliyor.  
  
 [!code-vb[VbLINQBasicOps#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#10)]  
  
 `Group Join`, SQL içindeki bir `LEFT JOIN` gibi, koleksiyonları tek bir hiyerarşik koleksiyonda birleştirir. Daha fazla bilgi için bkz. [JOIN yan tümcesi](../../../../visual-basic/language-reference/queries/join-clause.md) ve [Group JOIN yan tümcesi](../../../../visual-basic/language-reference/queries/group-join-clause.md).  
  
## <a name="grouping-data-group-by"></a>Verileri Gruplandırma (Gruplandırma Ölçütü)  
 Bir sorgu sonucundaki öğeleri, öğelerin bir veya daha fazla alanına göre gruplamak için bir `Group By` yan tümcesi ekleyebilirsiniz. Örneğin, aşağıdaki kod, öğrencileri sınıf yılından gruplandırır.  
  
 [!code-vb[VbLINQBasicOps#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#11)]  
  
 Bu kodu, [nasıl yapılır: öğe listesi oluşturma](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)bölümünde oluşturulan öğrencilerin listesini kullanarak çalıştırırsanız, `For Each` deyimden alınan çıkış şu şekilde olur:  
  
 Yıl: Junior  
  
 Tucker, Michael  
  
 Garcia, Kugo  
  
 Garcia, Deköşeli  
  
 Tucker, Izleme  
  
 Yıl: kıl  
  
 Omelchenko, Svetlana  
  
 Osada, Michiko  
  
 Fakhouri, Fadi  
  
 Feng, Hanying  
  
 Adams, Terry  
  
 Yıl: yalnızca bir Man  
  
 Mortensen, Sven  
  
 Garcia, Cesar  
  
 Aşağıdaki kodda gösterilen varyasyon, sınıf yıllarını sıralar ve ardından her yıl içinde öğrencileri soyadı olarak sıralar.  
  
 [!code-vb[VbLINQBasicOps#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#12)]  
  
 `Group By`hakkında daha fazla bilgi için bkz. [Group by yan tümcesi](../../../../visual-basic/language-reference/queries/group-by-clause.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Generic.IEnumerable%601>
- [Visual Basic LINQ ile çalışmaya başlama](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [Sorgular](../../../../visual-basic/language-reference/queries/index.md)
- [Standart sorgu Işleçlerine genel bakış (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
