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
ms.openlocfilehash: 6f4c58b15c33d8d2007069df88b2984e692df0a8
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91078378"
---
# <a name="basic-query-operations-visual-basic"></a>Temel Sorgu İşlemleri (Visual Basic)

Bu konu, Visual Basic dil ile tümleşik sorgu (LINQ) ifadelerine ve bir sorguda gerçekleştirdiğiniz bazı tipik işlem türlerinden bazılarına kısa bir giriş sağlar. Daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın:  
  
 [Visual Basic'de LINQ'e Giriş](../../language-features/linq/introduction-to-linq.md)  
  
 [Sorgular](../../../language-reference/queries/index.md)  
  
 [İzlenecek Yol: Visual Basic'de Sorgu Yazma](walkthrough-writing-queries.md)  
  
## <a name="specifying-the-data-source-from"></a>Veri Kaynağını (Kimden) Belirtme  

 Bir LINQ sorgusunda, ilk adım sorgulamak istediğiniz veri kaynağını belirtmektir. Bu nedenle, `From` bir sorgudaki yan tümce her zaman ilk olarak gelir. Sorgu işleçleri, kaynağın türüne göre sonucu seçin ve şekillendirin.  
  
 [!code-vb[VbLINQBasicOps#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#1)]  
  
 `From`Yan tümce veri kaynağını, `customers` ve bir *Aralık değişkenini*belirtir `cust` . Aralık değişkeni, bir sorgu ifadesinde gerçek yineleme gerçekleşmediğinde bir döngü yineleme değişkeni gibidir. Sorgu yürütüldüğünde, genellikle bir `For Each` döngü kullanılarak Aralık değişkeni, içinde birbirini izleyen her öğe için bir başvuru işlevi görür `customers` . Derleyici türünü çıkarsanbildiğinden `cust` , açıkça belirtmeniz gerekmez. Açık yazma olmadan ve ile yazılan sorguların örnekleri için bkz. [sorgu Işlemlerinde tür ilişkileri (Visual Basic)](type-relationships-in-query-operations.md).  
  
 Visual Basic yan tümcesini kullanma hakkında daha fazla bilgi için `From` bkz. [from yan tümcesi](../../../language-reference/queries/from-clause.md).  
  
## <a name="filtering-data-where"></a>Veri Filtreleme (Yeri)  

 Büyük olasılıkla en yaygın sorgu işlemi, bir filtreyi Boole ifadesi biçiminde uyguluyor. Sorgu daha sonra yalnızca ifadenin true olduğu öğeleri döndürür. `Where`Filtre uygulamak için bir yan tümce kullanılır. Filtre, veri kaynağındaki hangi öğelerin sonuç dizisine ekleneceğini belirtir. Aşağıdaki örnekte, yalnızca Londra 'da bir adresi olan müşteriler dahil edilmiştir.  
  
 [!code-vb[VbLINQBasicOps#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#2)]  
  
 `And` `Or` Bir yan tümcedeki Filtre ifadelerini birleştirmek için ve gibi mantıksal işleçleri kullanabilirsiniz `Where` . Örneğin, yalnızca Londra 'dan ve adı Devon olan müşterileri döndürmek için aşağıdaki kodu kullanın:  
  
```vb  
Where cust.City = "London" And cust.Name = "Devon"
```  
  
 Londra veya Paris 'ten müşterileri döndürmek için aşağıdaki kodu kullanın:  
  
```vb  
Where cust.City = "London" Or cust.City = "Paris"
```  
  
 Yan tümcesinin Visual Basic ' de nasıl kullanılacağı hakkında daha fazla bilgi için `Where` bkz. [WHERE yan tümcesi](../../../language-reference/queries/where-clause.md).  
  
## <a name="ordering-data-order-by"></a>Veri Sıralama (Sıralama Ölçütü)  

 Genellikle döndürülen verileri belirli bir sıraya göre sıralamak kullanışlıdır. `Order By`Yan tümcesi, döndürülen dizideki öğelerin belirtilen alan veya alanlar üzerinde sıralanmasına neden olur. Örneğin, aşağıdaki sorgu sonuçları özelliğine göre sıralar `Name` . `Name`Bir dize olduğu için döndürülen veriler, a 'Dan Z 'ye kadar alfabetik olarak sıralanır.  
  
 [!code-vb[VbLINQBasicOps#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#3)]  
  
 Sonuçları Z 'den A 'ya doğru sırada sıralamak için `Order By...Descending` yan tümcesini kullanın. Varsayılan değer ne `Ascending` `Ascending` de belirtilmemişse varsayılandır `Descending` .  
  
 Visual Basic yan tümcesini kullanma hakkında daha fazla bilgi için `Order By` bkz. [order by yan tümcesi](../../../language-reference/queries/order-by-clause.md).  
  
## <a name="selecting-data-select"></a>Verileri Seçme (Seçim)  

 `Select`Yan tümce döndürülen öğelerin formunu ve içeriğini belirtir. Örneğin, sonuçlarınızın tam `Customer` nesnelerden, tek bir `Customer` özellikten, özelliklerin bir alt kümesinden, çeşitli veri kaynaklarından özelliklerin bir birleşimini veya bir hesaplamayı temel alan bir dizi yeni sonuç türüne sahip olup olmayacağını belirtebilirsiniz. `Select`Yan tümce, kaynak öğenin bir kopyası dışında bir şey üretirse, işleme bir *projeksiyon*olarak adlandırılır.  
  
 Tüm nesnelerden oluşan bir koleksiyonu almak için `Customer` , Aralık değişkeninin kendisini seçin:  
  
 [!code-vb[VbLINQBasicOps#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#4)]  
  
 Bir `Customer` örnek çok fazla alan içeren büyük bir nesnedir ve almak istediğiniz tümü adı ise, `cust.Name` Aşağıdaki örnekte gösterildiği gibi öğesini seçebilirsiniz. Yerel tür çıkarımı, bu, sonuç türünü nesne koleksiyonundan bir `Customer` dizeler koleksiyonuna değiştirinin algılar.  
  
 [!code-vb[VbLINQBasicOps#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#5)]  
  
 Veri kaynağından birden çok alan seçmek için iki seçeneğiniz vardır:  
  
- `Select`Yan tümcesinde, sonuca dahil etmek istediğiniz alanları belirtin. Derleyici, özellikleri olarak bu alanlara sahip anonim bir tür tanımlayacaktır. Daha fazla bilgi için bkz. [anonim türler](../../language-features/objects-and-classes/anonymous-types.md).  
  
     Aşağıdaki örnekteki döndürülen öğeler anonim bir türün örnekleri olduğundan, kodunuzun başka bir yerinde ada göre türe başvuramaz. Tür için derleyici tarafından belirlenen ad, normal Visual Basic kodunda geçerli olmayan karakterler içeriyor. Aşağıdaki örnekte, içindeki sorgu tarafından döndürülen koleksiyonda bulunan öğeler, `londonCusts4` anonim bir türün örnekleridir  
  
     [!code-vb[VbLINQBasicOps#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#6)]  
  
     -veya-  
  
- Sonuca dahil etmek istediğiniz belirli alanları içeren adlandırılmış bir tür tanımlayın ve yan tümcesindeki tür örneklerini oluşturun ve başlatın `Select` . Bu seçeneği yalnızca, sonuçları döndürüldüğünden koleksiyonun dışında veya yöntem çağrılarında parametre olarak geçirmeniz gerekiyorsa kullanın. `londonCusts5`Aşağıdaki örnekteki tür IEnumerable (NamePhone).  
  
     [!code-vb[VbLINQBasicOps#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#7)]  
  
     [!code-vb[VbLINQBasicOps#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#8)]  
  
 Visual Basic yan tümcesini kullanma hakkında daha fazla bilgi için `Select` bkz. [Select yan tümcesi](../../../language-reference/queries/select-clause.md).  
  
## <a name="joining-data-join-and-group-join"></a>Veri Katma (Katma ve Grup Katma)  

 Yan tümcelerinde birden fazla veri kaynağını `From` çeşitli yollarla birleştirebilirsiniz. Örneğin, aşağıdaki kod iki veri kaynağını kullanır ve sonuç olarak her ikisinin de özelliklerini örtülü olarak birleştirir. Sorgu, son adları sesli harf ile başlayan öğrencileri seçer.  
  
 [!code-vb[VbLINQBasicOps#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#9)]  
  
> [!NOTE]
> Bu kodu, [nasıl yapılır: öğe listesi oluşturma](how-to-create-a-list-of-items.md)bölümünde oluşturulan öğrenciler listesiyle çalıştırabilirsiniz.  
  
 `Join`Anahtar sözcüğü, SQL içindeki bir ile eşdeğerdir `INNER JOIN` . İki koleksiyonu iki koleksiyonda bulunan öğeler arasında eşleşen anahtar değerlerine dayalı olarak birleştirir. Sorgu, eşleşen anahtar değerleri olan koleksiyon öğelerinin tümünü veya bir bölümünü döndürür. Örneğin, aşağıdaki kod önceki örtük birleşimin eylemini yineliyor.  
  
 [!code-vb[VbLINQBasicOps#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#10)]  
  
 `Group Join` koleksiyonları SQL gibi tek bir hiyerarşik koleksiyonda birleştirir `LEFT JOIN` . Daha fazla bilgi için bkz. [JOIN yan tümcesi](../../../language-reference/queries/join-clause.md) ve [Group JOIN yan tümcesi](../../../language-reference/queries/group-join-clause.md).  
  
## <a name="grouping-data-group-by"></a>Verileri Gruplandırma (Gruplandırma Ölçütü)  

 `Group By`Bir sorgu sonucundaki öğeleri, öğelerin bir veya daha fazla alanına göre gruplandırmak için bir yan tümce ekleyebilirsiniz. Örneğin, aşağıdaki kod, öğrencileri sınıf yılından gruplandırır.  
  
 [!code-vb[VbLINQBasicOps#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#11)]  
  
 Bu kodu, [nasıl yapılır: öğe listesi oluşturma](how-to-create-a-list-of-items.md)bölümünde oluşturulan öğrencilerin listesini kullanarak çalıştırırsanız, `For Each` deyimden alınan çıkış şu şekilde olur:  
  
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
  
 Hakkında daha fazla bilgi için `Group By` bkz. [Group by yan tümcesi](../../../language-reference/queries/group-by-clause.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Generic.IEnumerable%601>
- [Visual Basic'te LINQ'e Başlarken](getting-started-with-linq.md)
- [Sorgular](../../../language-reference/queries/index.md)
- [Standart sorgu Işleçlerine genel bakış (Visual Basic)](standard-query-operators-overview.md)
- [LINQ](../../language-features/linq/index.md)
