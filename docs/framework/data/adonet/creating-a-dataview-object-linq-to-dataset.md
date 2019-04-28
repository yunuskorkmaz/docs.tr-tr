---
title: DataView nesnesi (LINQ to DataSet) oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 76057508-e12d-4779-a707-06a4c2568acf
ms.openlocfilehash: 95bc9beed9965bad32118dfafa4a5aa76902ca10
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61607832"
---
# <a name="creating-a-dataview-object-linq-to-dataset"></a>DataView nesnesi (LINQ to DataSet) oluşturma
Oluşturmanın iki yolu vardır. bir <xref:System.Data.DataView> içinde [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] bağlamı. Oluşturabileceğiniz bir <xref:System.Data.DataView> gelen bir [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] üzerinden sorgu bir <xref:System.Data.DataTable>, ya da bir türü belirtilmiş veya türsüz oluşturabilirsiniz <xref:System.Data.DataTable>. Her iki durumda da, oluşturduğunuz <xref:System.Data.DataView> birini kullanarak <xref:System.Data.DataTableExtensions.AsDataView%2A> genişletme yöntemleri; <xref:System.Data.DataView> atmamalıdır doğrudan değil [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] bağlamı.  
  
 Sonra <xref:System.Data.DataView> olmuştur oluşturulan bir Windows forms uygulaması veya ASP.NET uygulaması bir UI denetimine bağlamak veya kullanabilirsiniz filtreleme ve sıralama ayarlarını değiştirin.  
  
 <xref:System.Data.DataView> Dizin filtreleme ve sıralama gibi kullanabileceğiniz işlemlerinin performansını önemli ölçüde artıran bir dizin oluşturur. Dizin için bir <xref:System.Data.DataView> hem zaman yerleşik <xref:System.Data.DataView> oluşturulur ve herhangi bir sıralama veya filtreleme bilgileri değiştirilir. Oluşturma bir <xref:System.Data.DataView> ve en az iki kere derlenmesi için dizini sıralama ayarlama veya daha sonra bilgiler filtreleme neden olur: bir kez zaman <xref:System.Data.DataView> oluşturulur, ve yeniden sıralama veya filtreleme özelliklerinden herhangi birini değiştirildiği.  
  
 İle sıralama ve filtreleme hakkında daha fazla bilgi için <xref:System.Data.DataView>, bkz: [DataView ile filtreleme](../../../../docs/framework/data/adonet/filtering-with-dataview-linq-to-dataset.md) ve [DataView ile sıralama](../../../../docs/framework/data/adonet/sorting-with-dataview-linq-to-dataset.md).  
  
## <a name="creating-dataview-from-a-linq-to-dataset-query"></a>DataView bir LINQ Sorgu veri kümesi oluşturma  
 A <xref:System.Data.DataView> nesne sonuçlarından oluşturulabilir bir [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] sorgu sonuçları, bir projeksiyon nerede <xref:System.Data.DataRow> nesneleri. Yeni oluşturulan <xref:System.Data.DataView> filtreleme ve sıralama oluşturulan gelen sorgu bilgilerinden devralır.  
  
> [!NOTE]
>  Çoğu durumda, filtreleme ve sıralama için kullanılan ifadeler yan etkileri olmamalıdır ve belirleyici olmalıdır. Ayrıca, ifadeleri herhangi içermemelidir sıralama ve filtreleme işlemleri olabileceğinden, yürütmeleri kümesi sayısına bağlı mantıksal kaç kez yürütüldü.  
  
 Oluşturma bir <xref:System.Data.DataView> anonim türler döndüren bir sorgu ya da birleştirme işlemleri gerçekleştirme sorguları desteklenmiyor.  
  
 Aşağıdaki sorgu işleçleri oluşturmak için kullanılan bir sorgu desteklenen <xref:System.Data.DataView>:  
  
- <xref:System.Data.EnumerableRowCollectionExtensions.Cast%2A>  
  
- <xref:System.Data.EnumerableRowCollectionExtensions.OrderBy%2A>  
  
- <xref:System.Data.EnumerableRowCollectionExtensions.OrderByDescending%2A>  
  
- <xref:System.Data.EnumerableRowCollectionExtensions.Select%2A>  
  
- <xref:System.Data.EnumerableRowCollectionExtensions.ThenBy%2A>  
  
- <xref:System.Data.EnumerableRowCollectionExtensions.ThenByDescending%2A>  
  
- <xref:System.Data.EnumerableRowCollectionExtensions.Where%2A>  
  
 Dikkat edin bir <xref:System.Data.DataView> içinden oluşturulan bir [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] sorgu <xref:System.Data.EnumerableRowCollectionExtensions.Select%2A> yöntemi sorguda adında gereken son yöntemi olması gerekir. Bu oluşturan aşağıdaki örnekte gösterildiği bir <xref:System.Data.DataView> çevrimiçi siparişler toplam süre göre sıralanır:  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQuery1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromquery1)]
 [!code-vb[DP DataView Samples#CreateLDVFromQuery1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromquery1)]  
  
 Dize tabanlı kullanabilirsiniz <xref:System.Data.DataView.RowFilter%2A> ve <xref:System.Data.DataView.Sort%2A> filtreleme ve sıralama özellikleri bir <xref:System.Data.DataView> bir sorgudan oluşturulduktan sonra. Bu sıralama temizler ve bilgi filtreleme sorgudan devralınan unutmayın. Aşağıdaki örnek, oluşturur bir <xref:System.Data.DataView> gelen bir [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] ile başlayan soyadlarına göre filtreleyen sorgu kullanıcının '. Dize tabanlı <xref:System.Data.DataView.Sort%2A> sırasını ve adlarını azalan düzende artan adların sıralanacak özelliğini ayarlayın:  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromquerystringsort)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromquerystringsort)]  
  
## <a name="creating-a-dataview-from-a-datatable"></a>Bir DataTable nesnesinden DataView oluşturma  
 Öğesinden oluşturulan yanı sıra bir [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] sorgu, bir <xref:System.Data.DataView> nesne öğesinden oluşturulabilir bir <xref:System.Data.DataTable> kullanarak <xref:System.Data.DataTableExtensions.AsDataView%2A> yöntemi.  
  
 Aşağıdaki örnek, oluşturur bir <xref:System.Data.DataView> veri kaynağı olarak ayarlar ve satış siparişi ayrıntısını tablo bir <xref:System.Windows.Forms.BindingSource> nesne. Bu nesne için bir proxy görevi gören bir <xref:System.Windows.Forms.DataGridView> denetimi.  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromTable](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromtable)]
 [!code-vb[DP DataView Samples#CreateLDVFromTable](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromtable)]  
  
 Temel filtreleme ve sıralama ayarlanabilir <xref:System.Data.DataView> gelen oluşturulduktan sonra bir <xref:System.Data.DataTable>. Aşağıdaki örnek, oluşturur bir <xref:System.Data.DataView> başvurun ve kümeleri <xref:System.Data.DataView.Sort%2A> adların sırasını ve adlarını azalan düzende artan sıralama özelliği:  
  
 [!code-csharp[DP DataView Samples#LDVStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvstringsort)]
 [!code-vb[DP DataView Samples#LDVStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvstringsort)]  
  
 Ancak, ayarı ile birlikte gelen bir performans kaybı yoktur <xref:System.Data.DataView.RowFilter%2A> veya <xref:System.Data.DataView.Sort%2A> sonra özellik <xref:System.Data.DataView> bir sorgudan oluşturuldu <xref:System.Data.DataView> filtreleme ve sıralama işlemleri desteklemek için bir dizin oluşturur. Ayarı <xref:System.Data.DataView.RowFilter%2A> veya <xref:System.Data.DataView.Sort%2A> özelliği yükü uygulamanıza ekleme ve performansı azaltarak veri dizini oluşturur. Mümkün olduğunda, ilk oluşturduğunuzda bilgi sıralama ve filtreleme belirtmek daha iyi <xref:System.Data.DataView> ve daha sonra değiştirmekten kaçının.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Bağlama ve LINQ to DataSet](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)
- [DataView ile Filtreleme](../../../../docs/framework/data/adonet/filtering-with-dataview-linq-to-dataset.md)
- [DataView ile Sıralama](../../../../docs/framework/data/adonet/sorting-with-dataview-linq-to-dataset.md)
