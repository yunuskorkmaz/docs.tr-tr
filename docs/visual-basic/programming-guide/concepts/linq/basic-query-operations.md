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
ms.openlocfilehash: efae72c65ad67b4a1b157b67dcc4d4d65f31f77b
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266384"
---
# <a name="basic-query-operations-visual-basic"></a>Temel Sorgu İşlemleri (Visual Basic)
Bu konu, Visual Basic'teki Dil Tümleşik Sorgu (LINQ) ifadelerine ve bir sorguda gerçekleştirdiğiniz tipik işlem türlerinden bazılarına kısa bir giriş sağlar. Daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın:  
  
 [Visual Basic'de LINQ'e Giriş](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
  
 [Sorgular](../../../../visual-basic/language-reference/queries/index.md)  
  
 [İzlenecek Yol: Visual Basic'de Sorgu Yazma](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md)  
  
## <a name="specifying-the-data-source-from"></a>Veri Kaynağını (Kimden) Belirtme  
 LINQ sorgusunda ilk adım, sorgulamak istediğiniz veri kaynağını belirtmektir. Bu nedenle, bir sorguda `From` yan tümce her zaman önce gelir. Sorgu işleçleri kaynağın türüne göre sonucu seçer ve şekillendirin.  
  
 [!code-vb[VbLINQBasicOps#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#1)]  
  
 Yan `From` tümce, veri kaynağını `customers`ve *bir aralık değişkenini* `cust`belirtir. Aralık değişkeni bir döngü yineleme değişkeni gibidir, ancak sorgu ifadesinde gerçek yineleme gerçekleşmez. Sorgu yürütüldüğünde, genellikle bir `For Each` döngü kullanılarak, aralık değişkeni `customers`. Derleyici türünü `cust`çıkarabileceğinden, bunu açıkça belirtmeniz gerekmez. Açık yazıyla ve açık yazmadan yazılan sorgu örnekleri için sorgu [işlemlerinde (Visual Basic) Tür İlişkileri](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md)bölümüne bakın.  
  
 Visual Basic'teki yan `From` tümcenin nasıl kullanılacağı hakkında daha fazla bilgi için [Bkz.](../../../../visual-basic/language-reference/queries/from-clause.md)  
  
## <a name="filtering-data-where"></a>Veri Filtreleme (Yeri)  
 Büyük olasılıkla en yaygın sorgu işlemi Boolean ifadesi şeklinde bir filtre uygulamaktır. Sorgu daha sonra yalnızca ifadenin doğru olduğu öğeleri döndürür. Filtreleme gerçekleştirmek için bir `Where` yan tümce kullanılır. Filtre, veri kaynağındaki hangi öğelerin elde edilen sıraya dahil olacağını belirtir. Aşağıdaki örnekte, yalnızca Londra'da adresi olan müşteriler dahildir.  
  
 [!code-vb[VbLINQBasicOps#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#2)]  
  
 Bir `Where` yan tümcedeki `And` `Or` filtre ifadeleri gibi mantıksal işleçleri kullanabilirsiniz. Örneğin, yalnızca Londra'dan gelen ve adı Devon olan müşterileri döndürmek için aşağıdaki kodu kullanın:  
  
```vb  
Where cust.City = "London" And cust.Name = "Devon"
```  
  
 Londra veya Paris'ten müşterileri iade etmek için aşağıdaki kodu kullanın:  
  
```vb  
Where cust.City = "London" Or cust.City = "Paris"
```  
  
 Visual Basic'teki yan `Where` tümcenin nasıl kullanılacağı hakkında daha fazla bilgi için [bkz.](../../../../visual-basic/language-reference/queries/where-clause.md)  
  
## <a name="ordering-data-order-by"></a>Veri Sıralama (Sıralama Ölçütü)  
 Döndürülen verileri belirli bir sırada sıralamak genellikle uygundur. Yan `Order By` tümce, döndürülen sırada yer alan öğelerin belirli bir alanda veya alanda sıralansın. Örneğin, aşağıdaki sorgu sonuçları `Name` özelliğe göre sıralar. `Name` Bir dize olduğundan, döndürülen veriler a'dan Z'ye alfabetik olarak sıralanır.  
  
 [!code-vb[VbLINQBasicOps#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#3)]  
  
 Sonuçları z'den A'ya ters sırayla `Order By...Descending` sıralamak için yan tümceyi kullanın. Varsayılan değer, `Ascending` `Ascending` ne `Descending` belirtilmiş ne de belirtilir.  
  
 Visual Basic'teki yan `Order By` tümcenin nasıl kullanılacağı hakkında daha fazla bilgi için [bkz.](../../../../visual-basic/language-reference/queries/order-by-clause.md)  
  
## <a name="selecting-data-select"></a>Verileri Seçme (Seçim)  
 Yan `Select` tümce, döndürülen öğelerin biçimini ve içeriğini belirtir. Örneğin, sonuçlarınızın tam `Customer` nesnelerden mi, yalnızca bir `Customer` özellikten, bir özellik alt kümesinden, çeşitli veri kaynaklarından özelliklerin birleşiminden mi yoksa bir hesaplamaya dayalı yeni bir sonuç türünden mi oluşacağını belirtebilirsiniz. `Select` Yan tümce kaynak öğenin bir kopyası ndan başka bir şey ürettiğinde, işlem *projeksiyon*olarak adlandırılır.  
  
 Tam `Customer` nesnelerden oluşan bir koleksiyon almak için aralık değişkeninin kendisini seçin:  
  
 [!code-vb[VbLINQBasicOps#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#4)]  
  
 Bir `Customer` örnek çok alanı olan büyük bir nesneyse ve almak istediğiniz tek şey `cust.Name`adsa, aşağıdaki örnekte gösterildiği gibi, bunu seçebilirsiniz. Yerel tür çıkarım, bu nesnelerin bir koleksiyondan `Customer` dizeleri bir koleksiyon için sonuç türünü değiştirir tanır.  
  
 [!code-vb[VbLINQBasicOps#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#5)]  
  
 Veri kaynağından birden çok alan seçmek için iki seçeneğiniz vardır:  
  
- Yan `Select` tümcede, sonuca eklemek istediğiniz alanları belirtin. Derleyici, özellikleri bu alanları içeren anonim bir tür tanımlar. Daha fazla bilgi için [Bkz. Anonim Türler.](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
  
     Aşağıdaki örnekte döndürülen öğeler anonim tür örnekleri olduğundan, kodunuzun başka bir yerinde ada göre türüne başvuramazsınız. Tür için derleyici tarafından atanan ad, normal Visual Basic kodunda geçerli olmayan karakterler içerir. Aşağıdaki örnekte, koleksiyondaki sorgu tarafından döndürülen öğeler `londonCusts4` anonim türörnekleridir  
  
     [!code-vb[VbLINQBasicOps#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#6)]  
  
     -veya-  
  
- Sonuca eklemek istediğiniz belirli alanları içeren adlandırılmış bir tür tanımlayın ve yan tümcedeki `Select` tür örnekleri oluşturun ve başharfe alın. Bu seçeneği yalnızca iade edildikleri koleksiyon dışında tek tek sonuçlar kullanmanız gerekiyorsa veya bunları yöntem çağrılarında parametre olarak geçirmeniz gerekiyorsa kullanın. Aşağıdaki `londonCusts5` örnekte türü IEnumerable (NamePhone of) olduğunu.  
  
     [!code-vb[VbLINQBasicOps#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#7)]  
  
     [!code-vb[VbLINQBasicOps#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#8)]  
  
 Visual Basic'te yan `Select` tümcenin nasıl kullanılacağı hakkında daha fazla bilgi için [bkz.](../../../../visual-basic/language-reference/queries/select-clause.md)  
  
## <a name="joining-data-join-and-group-join"></a>Veri Katma (Katma ve Grup Katma)  
 `From` Yan tümcede birden fazla veri kaynağını çeşitli şekillerde birleştirebilirsiniz. Örneğin, aşağıdaki kod iki veri kaynağı kullanır ve dolaylı olarak sonuç her ikisinin özellikleri birleştirir. Sorgu, soyadı sesli harfle başlayan öğrencileri seçer.  
  
 [!code-vb[VbLINQBasicOps#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#9)]  
  
> [!NOTE]
> Bu [kodu, Nasıl Oluşturulur: Öğeler Listesi Oluşturma'da](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)oluşturulan öğrencilerin listesiyle çalıştırabilirsiniz.  
  
 Anahtar `Join` kelime SQL'deki `INNER JOIN` bir kelimeye eşdeğerdir. İki koleksiyondaki öğeler arasında eşleşen anahtar değerleri temel alan iki koleksiyonu birleştirir. Sorgu, anahtar değerleri eşleşen toplama öğelerinin tümününveya bir kısmını döndürür. Örneğin, aşağıdaki kod önceki örtük birleştirme eylemini yineler.  
  
 [!code-vb[VbLINQBasicOps#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#10)]  
  
 `Group Join`koleksiyonları SQL'deki gibi `LEFT JOIN` tek bir hiyerarşik koleksiyonda birleştirir. Daha fazla bilgi için [Group Join Clause](../../../../visual-basic/language-reference/queries/group-join-clause.md) [bkz.](../../../../visual-basic/language-reference/queries/join-clause.md)  
  
## <a name="grouping-data-group-by"></a>Verileri Gruplandırma (Gruplandırma Ölçütü)  
 Sorgu sonucundaki `Group By` öğeleri öğelerin bir veya daha fazla alanına göre gruplandırmak için bir yan tümce ekleyebilirsiniz. Örneğin, aşağıdaki kod öğrencileri sınıf yılına göre gruplanır.  
  
 [!code-vb[VbLINQBasicOps#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#11)]  
  
 Bu kodu [nasıl oluşturulur: Öğeler Listesi oluşturma'](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)da oluşturulan öğrencilerin listesini kullanarak `For Each` çalıştırın, deyimden çıktı:  
  
 Yıl: Junior  
  
 Tucker, Michael  
  
 Garcia, Hugo  
  
 Garcia, Debra  
  
 Tucker, Lance  
  
 Yıl: Kıdemli  
  
 Omelchenko, Svetlana  
  
 Osada, Michiko  
  
 Fakhouri, Fadi  
  
 Feng, Hanying  
  
 Adams, Terry  
  
 Yıl: Birinci Sınıf  
  
 Mortensen, Sven  
  
 Garcia, Cesar  
  
 Aşağıdaki kodda gösterilen varyasyon sınıf yıllarını emreder ve her yıl içinde öğrencilere soyadını verir.  
  
 [!code-vb[VbLINQBasicOps#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#12)]  
  
 Hakkında `Group By`daha fazla bilgi için bkz: [Grup Yan Tümcesi.](../../../../visual-basic/language-reference/queries/group-by-clause.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Generic.IEnumerable%601>
- [Visual Basic'te LINQ'e Başlarken](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [Sorgular](../../../../visual-basic/language-reference/queries/index.md)
- [Standart Sorgu Operatörlerine Genel Bakış (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
