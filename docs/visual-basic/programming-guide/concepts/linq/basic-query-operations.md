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
ms.openlocfilehash: af99a6c22239be1f9f03bafd8323c73f83df5c51
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64642272"
---
# <a name="basic-query-operations-visual-basic"></a>Temel Sorgu İşlemleri (Visual Basic)
Bu konu, kısa bir giriş sağlar. [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] ifadeleri Visual Basic'te ve bazı sorguda gerçekleştirdiğiniz işlemleri tipik türleri. Daha fazla bilgi için aşağıdaki konulara bakın:  
  
 [Visual Basic'de LINQ'e giriş](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
  
 [Sorgular](../../../../visual-basic/language-reference/queries/index.md)  
  
 [İzlenecek yol: Visual Basic'de sorgu yazma](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md)  
  
## <a name="specifying-the-data-source-from"></a>Veri Kaynağını (Kimden) Belirtme  
 İçinde bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu, ilk adımıdır sorgulamak istediğiniz veri kaynağını belirtmek için. Bu nedenle, `From` yan tümcesinin sorgudaki her zaman gelen ilk. Sorgu işleçleri seçin ve kaynak türüne göre sonuç şekli.  
  
 [!code-vb[VbLINQBasicOps#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#1)]  
  
 `From` Yan tümcesi veri kaynağını belirtir `customers`ve *aralık değişkeni*, `cust`. Aralık değişkeni bir döngü yineleme değişkeni gibi bir sorgu ifadesinde gerçek yineleme gerçekleşir dışında aynıdır. Ne zaman sorgu yürütüldüğünde, genellikle kullanarak bir `For Each` aralık değişkeni döngü, hizmet art arda gelen her öğe için başvuru olarak `customers`. Derleyicinin türü çıkarsayabilir `cust`, açıkça belirtmeniz gerekmez. Olmadan açık yazım ve yazılan sorgularının örnekleri için bkz: [(Visual Basic) sorgu işlemlerinde tür ilişkileri](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md).  
  
 Nasıl kullanılacağı hakkında daha fazla bilgi için `From` yan tümcesine Visual Basic'te bakın [From yan tümcesi](../../../../visual-basic/language-reference/queries/from-clause.md).  
  
## <a name="filtering-data-where"></a>Veri Filtreleme (Yeri)  
 Muhtemelen en sık kullanılan sorgu işlemi formunda bir Boolean ifadesinin filtre uygulanıyor. Sorgu, ardından ifade true olduğu öğeleri döndürür. A `Where` yan tümcesi filtreleme işlemleri için kullanılır. Filtre hangi öğelerin elde edilen sırayla eklemek için veri kaynağı belirtir. Aşağıdaki örnekte, Londra'daki bir adresi olan müşterilerin dahil edilir.  
  
 [!code-vb[VbLINQBasicOps#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#2)]  
  
 Mantıksal işleçler gibi kullanabileceğiniz `And` ve `Or` filtre ifadelerinde birleştirmek için bir `Where` yan tümcesi. Örneğin, yalnızca Londra'dan olan ve Devon adı olan müşteriler döndürmek için aşağıdaki kodu kullanın:  
  
```vb  
Where cust.City = "London" And cust.Name = "Devon"   
```  
  
 Müşteriler Londra veya Paris döndürmek için aşağıdaki kodu kullanın:  
  
```vb  
Where cust.City = "London" Or cust.City = "Paris"   
```  
  
 Nasıl kullanılacağı hakkında daha fazla bilgi için `Where` yan tümcesine Visual Basic'te bakın [Where yan tümcesi](../../../../visual-basic/language-reference/queries/where-clause.md).  
  
## <a name="ordering-data-order-by"></a>Veri Sıralama (Sıralama Ölçütü)  
 Genellikle, döndürülen veriler belirli bir sıralamaya sıralamak uygundur. `Order By` Yan tümcesi neden öğeleri belirtilen bir alan veya alanlar üzerinde sıralanacak döndürülen dizideki. Örneğin, aşağıdaki sorguyu göre sonuçları sıralayan `Name` özelliği. Çünkü `Name` bir dizedir, döndürülen veriler, a-z alfabetik olarak sıralanır.  
  
 [!code-vb[VbLINQBasicOps#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#3)]  
  
 Sonuçları Z'den A'ya, ters sırada sıralamak için kullanmak `Order By...Descending` yan tümcesi. Varsayılan değer `Ascending` ne zaman `Ascending` ya da `Descending` belirtilir.  
  
 Nasıl kullanılacağı hakkında daha fazla bilgi için `Order By` yan tümcesine Visual Basic'te bakın [Order By yan tümcesi](../../../../visual-basic/language-reference/queries/order-by-clause.md).  
  
## <a name="selecting-data-select"></a>Verileri Seçme (Seçim)  
 `Select` Yan tümcesi, form ve döndürülen öğelerin içeriğini belirtir. Örneğin, sizin sonuçlarınız, tam oluşacağını belirtebilirsiniz `Customer` nesneler, yalnızca bir tane `Customer` özelliği, bir özellik alt kümesi, çeşitli veri kaynaklarından veya bazı yeni sonuç türü özelliklerinin alan üzerinde bir hesaplama. Zaman `Select` yan tümcesi bir kopyasını bir kaynak öğesi dışında bir şey üretir, işlem çağrılır bir *projeksiyon*.  
  
 Tam oluşan bir koleksiyonu almak için `Customer` nesneleri, aralık değişkeni seçin:  
  
 [!code-vb[VbLINQBasicOps#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#4)]  
  
 Varsa bir `Customer` örneği birçok alan, bir büyük nesnesi olan ve almak istediğiniz tüm adı, seçebileceğiniz `cust.Name`, aşağıdaki örnekte gösterildiği gibi. Yerel tür çıkarımı tanır bu sonuç türü koleksiyonundan değiştirir `Customer` dizelerden oluşan bir koleksiyon nesneleri.  
  
 [!code-vb[VbLINQBasicOps#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#5)]  
  
 Veri kaynağından birden çok alan seçmek için iki seçeneğiniz vardır:  
  
- İçinde `Select` yan tümcesi, sonuç dahil etmek istediğiniz alanları belirtin. Derleyici bu alanları olarak kendi özellikleri olan anonim bir tür tanımlar. Daha fazla bilgi için [anonim türler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
     Aşağıdaki örnekte döndürülen öğeler anonim bir türün örneklerinin olduğundan, türüne adıyla başka bir yerde kodunuzda başvuruda bulunamaz. Derleyici tarafından atanan adı türü için normal Visual Basic kodu içinde geçerli olmayan karakterler içeriyor. Aşağıdaki örnekte, sorgu tarafından döndürülen koleksiyondaki öğelerin `londonCusts4` anonim bir türün örnekleri  
  
     [!code-vb[VbLINQBasicOps#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#6)]  
  
     -veya-  
  
- Adlandırılmış tür sonucuna dahil, oluşturma ve başlatma türün örneklerinin istediğiniz belirli alanları içeren tanımlama `Select` yan tümcesi. Yalnızca bireysel sonuçları döndürülen koleksiyon dışında kullanmanız gerekiyorsa veya yöntem çağrılarını parametreler olarak geçirileceğini gerekiyorsa bu seçeneği kullanın. Türünü `londonCusts5` IEnumerable (Of NamePhone) aşağıdaki örnekte olduğu.  
  
     [!code-vb[VbLINQBasicOps#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#7)]  
  
     [!code-vb[VbLINQBasicOps#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#8)]  
  
 Nasıl kullanılacağı hakkında daha fazla bilgi için `Select` yan tümcesine Visual Basic'te bakın [Select tümcesi](../../../../visual-basic/language-reference/queries/select-clause.md).  
  
## <a name="joining-data-join-and-group-join"></a>Veri Katma (Katma ve Grup Katma)  
 Birden fazla veri kaynağında birleştirebilirsiniz `From` çeşitli şekillerde yan tümcesi. Örneğin, aşağıdaki kod, iki veri kaynağı kullanır ve sonuçta ikisinin özelliklerinden örtük olarak birleştirir. Sorgu son adları bir harfle başlayan Öğrenciler seçer.  
  
 [!code-vb[VbLINQBasicOps#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#9)]  
  
> [!NOTE]
>  Oluşturulan Öğrenciler listesiyle birlikte bu kodu çalıştırmak [nasıl yapılır: Öğe listesi oluşturma](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).  
  
 `Join` Anahtar sözcüğü, eşdeğer bir `INNER JOIN` SQL. Bu, iki koleksiyon öğeleri arasında eşleşen anahtar değerlere göre iki koleksiyon birleştirir. Sorgu anahtar değerlerini eşleşen koleksiyon öğelerinin bir kısmını veya tamamını döndürür. Örneğin, aşağıdaki kod önceki örtük birleştirme eylemini çoğaltır.  
  
 [!code-vb[VbLINQBasicOps#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#10)]  
  
 `Group Join` Tıpkı koleksiyonları tek bir hiyerarşik koleksiyon halinde birleştirir bir `LEFT JOIN` SQL. Daha fazla bilgi için [JOIN yan tümcesi](../../../../visual-basic/language-reference/queries/join-clause.md) ve [Group JOIN yan tümcesi](../../../../visual-basic/language-reference/queries/group-join-clause.md).  
  
## <a name="grouping-data-group-by"></a>Verileri Gruplandırma (Gruplandırma Ölçütü)  
 Ekleyebileceğiniz bir `Group By` yan tümcesi bir sorgu sonucunu öğelerin bir veya daha fazla alanlara göre öğeleri gruplandırmak için. Örneğin, aşağıdaki kod Öğrenciler sınıfı yıla göre gruplandırır.  
  
 [!code-vb[VbLINQBasicOps#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#11)]  
  
 Oluşturulan Öğrenciler listesini kullanarak bu kodu çalıştırırsanız [nasıl yapılır: Bir öğe listesi oluşturma](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md), çıkışı `For Each` deyimidir:  
  
 Yıl: Alt düzey  
  
 Tucker, Michael  
  
 Garcia, Hugo  
  
 Garcia, Debra  
  
 Tucker, Lance  
  
 Yıl: Üst düzey  
  
 Omelchenko, Svetlana  
  
 Osada, Michiko  
  
 Fakhouri, Fadi  
  
 Feng, Hanying  
  
 Adams, Terry  
  
 Yıl: Freshman  
  
 Mortensen, Sven  
  
 Garcia, Cesar  
  
 Aşağıdaki kodda gösterilen değişim sınıfı yıllar sıralar ve ardından Öğrenciler her yıl içinde soyadına göre sıralar.  
  
 [!code-vb[VbLINQBasicOps#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#12)]  
  
 Hakkında daha fazla bilgi için `Group By`, bkz: [Group yan tümcesi tarafından](../../../../visual-basic/language-reference/queries/group-by-clause.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Generic.IEnumerable%601>
- [Visual Basic'te lınq'e Başlarken](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [Sorgular](../../../../visual-basic/language-reference/queries/index.md)
- [Standart sorgu işleçlerine genel bakış (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
