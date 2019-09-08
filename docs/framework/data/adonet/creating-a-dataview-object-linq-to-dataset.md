---
title: DataView nesnesi oluşturma (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 76057508-e12d-4779-a707-06a4c2568acf
ms.openlocfilehash: 054898a3520cbc2b607fc26b94b72b9896ad9c71
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786690"
---
# <a name="creating-a-dataview-object-linq-to-dataset"></a>DataView nesnesi oluşturma (LINQ to DataSet)
LINQ to DataSet bağlamında oluşturmak <xref:System.Data.DataView> için iki yol vardır. Bir LINQ to DataSet sorgusundan <xref:System.Data.DataTable>bir <xref:System.Data.DataView> oluşturabilirsiniz veya <xref:System.Data.DataTable>türü bir veya türü belirlenmiş ya da işaretsiz bir şekilde oluşturabilirsiniz. Her iki durumda da <xref:System.Data.DataView> <xref:System.Data.DataTableExtensions.AsDataView%2A> uzantısını uzantı yöntemlerinden birini kullanarak oluşturursunuz; <xref:System.Data.DataView> LINQ to DataSet bağlamında doğrudan oluşturulabilir değildir.  
  
 <xref:System.Data.DataView> Oluşturulduktan sonra, bir Windows Forms uygulaması veya ASP.NET uygulamasındaki bir UI denetimine bağlanabilir ya da filtreleme ve sıralama ayarlarını değiştirebilirsiniz.  
  
 <xref:System.Data.DataView>filtre ve sıralama gibi, dizini kullanan işlemlerin performansını önemli ölçüde artıran bir dizin oluşturur. ' A <xref:System.Data.DataView> ait dizin, her ikisi de <xref:System.Data.DataView> oluşturulduğunda ve sıralama ya da filtreleme bilgisi değiştirildiğinde oluşturulur. Oluşturma ve daha sonra sıralama veya filtreleme bilgilerini ayarlama, dizinin en az iki kez oluşturulmasına neden olur: oluşturulduğunda bir kez <xref:System.Data.DataView> ve sıralama veya filtre özelliklerinden herhangi biri değiştirildiğinde. <xref:System.Data.DataView>  
  
 Filtreleme ve sıralama <xref:System.Data.DataView>hakkında daha fazla bilgi için bkz. DataView [ile filtreleme](filtering-with-dataview-linq-to-dataset.md) ve [DataView ile sıralama](sorting-with-dataview-linq-to-dataset.md).  
  
## <a name="creating-dataview-from-a-linq-to-dataset-query"></a>LINQ to DataSet sorgusundan DataView oluşturma  
 Bir <xref:System.Data.DataView> nesne, sonuçların bir <xref:System.Data.DataRow> nesne projeksiyonu olduğu LINQ to DataSet sorgusunun sonuçlarından oluşturulabilir. Yeni oluşturulan <xref:System.Data.DataView> , filtreleme ve sıralama bilgilerini, oluşturulduğu sorgudan devralır.  
  
> [!NOTE]
> Çoğu durumda, filtreleme ve sıralama için kullanılan ifadelerin yan etkileri olmaması ve belirleyici olması gerekir. Ayrıca, sıralama ve filtreleme işlemleri herhangi bir sayıda yürütülene kadar, ifadeler bir dizi yürütme sayısına bağlı herhangi bir mantığı içermemelidir.  
  
 <xref:System.Data.DataView> Anonim türleri veya JOIN işlemleri gerçekleştiren sorguları döndüren bir sorgudan oluşturma desteklenmez.  
  
 Oluşturmak <xref:System.Data.DataView>için kullanılan bir sorguda yalnızca aşağıdaki sorgu işleçleri desteklenir:  
  
- <xref:System.Data.EnumerableRowCollectionExtensions.Cast%2A>  
  
- <xref:System.Data.EnumerableRowCollectionExtensions.OrderBy%2A>  
  
- <xref:System.Data.EnumerableRowCollectionExtensions.OrderByDescending%2A>  
  
- <xref:System.Data.EnumerableRowCollectionExtensions.Select%2A>  
  
- <xref:System.Data.EnumerableRowCollectionExtensions.ThenBy%2A>  
  
- <xref:System.Data.EnumerableRowCollectionExtensions.ThenByDescending%2A>  
  
- <xref:System.Data.EnumerableRowCollectionExtensions.Where%2A>  
  
 Bir LINQ to DataSet sorgusundan oluşturulduğunda yöntemin sorguda çağrılan son yöntem olması gerektiğini unutmayın. <xref:System.Data.EnumerableRowCollectionExtensions.Select%2A> <xref:System.Data.DataView> Bu, aşağıdaki örnekte gösterilmiştir ve bu nedenle toplam olarak sıralanmış <xref:System.Data.DataView> bir çevrimiçi sipariş oluşturulur:  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQuery1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromquery1)]
 [!code-vb[DP DataView Samples#CreateLDVFromQuery1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromquery1)]  
  
 Bir <xref:System.Data.DataView.Sort%2A> <xref:System.Data.DataView.RowFilter%2A> sorgudanoluşturulduktansonrafiltrelemekvesıralamakiçindizetabanlıveözellikleridekullanabilirsiniz.<xref:System.Data.DataView> Bunun, sorgudan devralınan sıralama ve filtreleme bilgilerini temizleyip temizyacağını unutmayın. Aşağıdaki örnek, ' den <xref:System.Data.DataView> başlayan son adlara göre filtreleyen bir LINQ to DataSet sorgusundan bir oluşturur. Dize tabanlı <xref:System.Data.DataView.Sort%2A> özellik, son adlarla artan düzende sıralanacak şekilde ayarlanır ve ardından ilk adı azalan sırada alır:  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromquerystringsort)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromquerystringsort)]  
  
## <a name="creating-a-dataview-from-a-datatable"></a>DataTable 'dan bir DataView oluşturma  
 Bir LINQ to DataSet sorgusundan oluşturulmalarının yanı sıra, <xref:System.Data.DataView> <xref:System.Data.DataTableExtensions.AsDataView%2A> yöntemi kullanılarak bir <xref:System.Data.DataTable> nesnesi de oluşturulabilir.  
  
 Aşağıdaki örnek, SalesOrderDetail <xref:System.Data.DataView> tablosundan bir oluşturur ve bunu bir <xref:System.Windows.Forms.BindingSource> nesnenin veri kaynağı olarak ayarlar. Bu nesne, bir <xref:System.Windows.Forms.DataGridView> denetim için proxy görevi görür.  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromTable](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromtable)]
 [!code-vb[DP DataView Samples#CreateLDVFromTable](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromtable)]  
  
 Filtreleme ve sıralama, <xref:System.Data.DataView> bir <xref:System.Data.DataTable>öğesinden oluşturulduktan sonra üzerinde ayarlanabilir. Aşağıdaki örnek, kişi tablosundan <xref:System.Data.DataView> bir oluşturur ve bu özelliği, <xref:System.Data.DataView.Sort%2A> son adlarla artan düzende sıralanacak şekilde ayarlar ve ardından azalan sırada ilk isimleri yapar:  
  
 [!code-csharp[DP DataView Samples#LDVStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvstringsort)]
 [!code-vb[DP DataView Samples#LDVStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvstringsort)]  
  
 Ancak, bir sorgudan <xref:System.Data.DataView.RowFilter%2A> oluşturulduktan sonra <xref:System.Data.DataView> veya <xref:System.Data.DataView.Sort%2A> özelliğini ayarlamaya yönelik bir performans kaybı vardır çünkü <xref:System.Data.DataView> filtre ve sıralama işlemlerini desteklemek için bir dizin oluşturur. <xref:System.Data.DataView.RowFilter%2A> Veya<xref:System.Data.DataView.Sort%2A> özelliğinin ayarlanması, verilerin dizinini yeniden oluşturur, uygulamanıza ek yük ekler ve performansı azaltır. Mümkün olduğunda, ilk olarak oluştururken <xref:System.Data.DataView> filtreleme ve sıralama bilgilerini belirtmek ve daha sonra değiştirmeyi önlemek daha iyidir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Bağlama ve LINQ to DataSet](data-binding-and-linq-to-dataset.md)
- [DataView ile Filtreleme](filtering-with-dataview-linq-to-dataset.md)
- [DataView ile Sıralama](sorting-with-dataview-linq-to-dataset.md)
