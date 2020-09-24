---
title: DataView nesnesi oluşturma (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 76057508-e12d-4779-a707-06a4c2568acf
ms.openlocfilehash: f76574a912128918ed575cbf0eca892041dc354c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148327"
---
# <a name="creating-a-dataview-object-linq-to-dataset"></a>DataView nesnesi oluşturma (LINQ to DataSet)

LINQ to DataSet bağlamında oluşturmak için iki yol vardır <xref:System.Data.DataView> . Bir <xref:System.Data.DataView> LINQ to DataSet sorgusundan bir oluşturabilirsiniz <xref:System.Data.DataTable> veya türü bir veya türü belirlenmiş ya da işaretsiz bir şekilde oluşturabilirsiniz <xref:System.Data.DataTable> . Her iki durumda da, <xref:System.Data.DataView> Uzantısı yöntemlerinden birini kullanarak oluşturursunuz <xref:System.Data.DataTableExtensions.AsDataView%2A> ; <xref:System.Data.DataView> LINQ to DataSet bağlamında doğrudan oluşturulabilir.  
  
 Oluşturulduktan sonra <xref:System.Data.DataView> , bir Windows Forms uygulaması veya ASP.NET uygulamasındaki BIR UI denetimine bağlanabilir ya da filtreleme ve sıralama ayarlarını değiştirebilirsiniz.  
  
 <xref:System.Data.DataView> filtre ve sıralama gibi, dizini kullanan işlemlerin performansını önemli ölçüde artıran bir dizin oluşturur. ' A ait dizin, <xref:System.Data.DataView> her ikisi de <xref:System.Data.DataView> oluşturulduğunda ve sıralama ya da filtreleme bilgisi değiştirildiğinde oluşturulur. Oluşturma <xref:System.Data.DataView> ve daha sonra sıralama veya filtreleme bilgilerini ayarlama, dizinin en az iki kez oluşturulmasına neden olur: oluşturulduğunda bir kez <xref:System.Data.DataView> ve sıralama veya filtre özelliklerinden herhangi biri değiştirildiğinde.  
  
 Filtreleme ve sıralama hakkında daha fazla bilgi için <xref:System.Data.DataView> bkz. DataView [ile filtreleme](filtering-with-dataview-linq-to-dataset.md) ve [DataView ile sıralama](sorting-with-dataview-linq-to-dataset.md).  
  
## <a name="creating-dataview-from-a-linq-to-dataset-query"></a>LINQ to DataSet sorgusundan DataView oluşturma  

 Bir <xref:System.Data.DataView> nesne, sonuçların bir nesne projeksiyonu olduğu LINQ to DataSet sorgusunun sonuçlarından oluşturulabilir <xref:System.Data.DataRow> . Yeni oluşturulan, <xref:System.Data.DataView> filtreleme ve sıralama bilgilerini, oluşturulduğu sorgudan devralır.  
  
> [!NOTE]
> Çoğu durumda, filtreleme ve sıralama için kullanılan ifadelerin yan etkileri olmaması ve belirleyici olması gerekir. Ayrıca, sıralama ve filtreleme işlemleri herhangi bir sayıda yürütülene kadar, ifadeler bir dizi yürütme sayısına bağlı herhangi bir mantığı içermemelidir.  
  
 <xref:System.Data.DataView>Anonim türleri veya JOIN işlemleri gerçekleştiren sorguları döndüren bir sorgudan oluşturma desteklenmez.  
  
 Oluşturmak için kullanılan bir sorguda yalnızca aşağıdaki sorgu işleçleri desteklenir <xref:System.Data.DataView> :  
  
- <xref:System.Data.EnumerableRowCollectionExtensions.Cast%2A>  
  
- <xref:System.Data.EnumerableRowCollectionExtensions.OrderBy%2A>  
  
- <xref:System.Data.EnumerableRowCollectionExtensions.OrderByDescending%2A>  
  
- <xref:System.Data.EnumerableRowCollectionExtensions.Select%2A>  
  
- <xref:System.Data.EnumerableRowCollectionExtensions.ThenBy%2A>  
  
- <xref:System.Data.EnumerableRowCollectionExtensions.ThenByDescending%2A>  
  
- <xref:System.Data.EnumerableRowCollectionExtensions.Where%2A>  
  
 Bir <xref:System.Data.DataView> LINQ to DataSet sorgusundan oluşturulduğunda <xref:System.Data.EnumerableRowCollectionExtensions.Select%2A> yöntemin sorguda çağrılan son yöntem olması gerektiğini unutmayın. Bu, aşağıdaki örnekte gösterilmiştir ve bu <xref:System.Data.DataView> nedenle toplam olarak sıralanmış bir çevrimiçi sipariş oluşturulur:  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQuery1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromquery1)]
 [!code-vb[DP DataView Samples#CreateLDVFromQuery1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromquery1)]  
  
 <xref:System.Data.DataView.RowFilter%2A> <xref:System.Data.DataView.Sort%2A> Bir sorgudan oluşturulduktan sonra filtrelemek ve sıralamak için dize tabanlı ve özellikleri de kullanabilirsiniz <xref:System.Data.DataView> . Bunun, sorgudan devralınan sıralama ve filtreleme bilgilerini temizleyip temizyacağını unutmayın. Aşağıdaki örnek, <xref:System.Data.DataView> ' den başlayan son adlara göre filtreleyen bir LINQ to DataSet sorgusundan bir oluşturur. Dize tabanlı özellik, <xref:System.Data.DataView.Sort%2A> son adlarla artan düzende sıralanacak şekilde ayarlanır ve ardından ilk adı azalan sırada alır:  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromquerystringsort)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromquerystringsort)]  
  
## <a name="creating-a-dataview-from-a-datatable"></a>DataTable 'dan bir DataView oluşturma  

 Bir LINQ to DataSet sorgusundan oluşturulmalarının yanı sıra, <xref:System.Data.DataView> yöntemi kullanılarak bir nesnesi de oluşturulabilir <xref:System.Data.DataTable> <xref:System.Data.DataTableExtensions.AsDataView%2A> .  
  
 Aşağıdaki örnek, <xref:System.Data.DataView> SalesOrderDetail tablosundan bir oluşturur ve bunu bir nesnenin veri kaynağı olarak ayarlar <xref:System.Windows.Forms.BindingSource> . Bu nesne, bir denetim için proxy görevi görür <xref:System.Windows.Forms.DataGridView> .  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromTable](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromtable)]
 [!code-vb[DP DataView Samples#CreateLDVFromTable](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromtable)]  
  
 Filtreleme ve sıralama, <xref:System.Data.DataView> bir öğesinden oluşturulduktan sonra üzerinde ayarlanabilir <xref:System.Data.DataTable> . Aşağıdaki örnek, <xref:System.Data.DataView> kişi tablosundan bir oluşturur ve bu <xref:System.Data.DataView.Sort%2A> özelliği, son adlarla artan düzende sıralanacak şekilde ayarlar ve ardından azalan sırada ilk isimleri yapar:  
  
 [!code-csharp[DP DataView Samples#LDVStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvstringsort)]
 [!code-vb[DP DataView Samples#LDVStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvstringsort)]  
  
 Ancak, <xref:System.Data.DataView.RowFilter%2A> <xref:System.Data.DataView.Sort%2A> bir sorgudan oluşturulduktan sonra veya özelliğini ayarlamaya yönelik bir performans kaybı vardır <xref:System.Data.DataView> çünkü <xref:System.Data.DataView> filtre ve sıralama işlemlerini desteklemek için bir dizin oluşturur. <xref:System.Data.DataView.RowFilter%2A>Veya özelliğinin ayarlanması <xref:System.Data.DataView.Sort%2A> , verilerin dizinini yeniden oluşturur, uygulamanıza ek yük ekler ve performansı azaltır. Mümkün olduğunda, ilk olarak oluştururken filtreleme ve sıralama bilgilerini belirtmek <xref:System.Data.DataView> ve daha sonra değiştirmeyi önlemek daha iyidir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Bağlama ve LINQ to DataSet](data-binding-and-linq-to-dataset.md)
- [DataView ile Filtreleme](filtering-with-dataview-linq-to-dataset.md)
- [DataView ile Sıralama](sorting-with-dataview-linq-to-dataset.md)
