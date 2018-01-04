---
title: "DataView (LINQ-DataSet) sıralama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 885b3b7b-51c1-42b3-bb29-b925f4f69a6f
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: ae9ee83802b71eeab63fe5305b49d79a5cfaaf39
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="sorting-with-dataview-linq-to-dataset"></a>DataView (LINQ-DataSet) sıralama
Belirli bir ölçüte dayalı verileri sıralamak ve bir kullanıcı Arabirimi denetim üzerinden bir istemciye veri sunmak olanağı veri bağlama önemli bir yönüdür. <xref:System.Data.DataView>verileri sıralama ve veri satırı sıralama ölçüte göre sıralanmış dönmek için çeşitli yöntemler sağlar. Sıralama özellikleri, kendi dize tabanlı yanı sıra <xref:System.Data.DataView> kullanmanıza olanak tanır [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] ifadeleri sıralama ölçütleri için. [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]ifadeler dize tabanlıdır sıralama daha çok daha karmaşık ve güçlü sıralama işlemleri izin verir. Bu konuda kullanarak sıralama için her iki yaklaşım açıklanmaktadır <xref:System.Data.DataView>.  
  
## <a name="creating-dataview-from-a-query-with-sorting-information"></a>DataView bilgi sıralama ile bir sorgu oluşturma  
 A <xref:System.Data.DataView> nesnesi, gelen oluşturulabilir bir [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] sorgu. Bu sorgu içeriyorsa bir <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.OrderByDescending%2A>, <xref:System.Linq.Enumerable.ThenBy%2A>, veya <xref:System.Linq.Enumerable.ThenByDescending%2A> yan tümcesi bu yan tümceleri ifadelerinde verileri sıralamak için temel olarak kullanılır <xref:System.Data.DataView>. Sorgu içeriyorsa, örneğin, `Order By…`ve `Then By…` yan tümceleri, elde edilen <xref:System.Data.DataView> verileri belirtilen her iki sütuna göre sıralama.  
  
 İfade tabanlı sıralama daha basit sıralama dize tabanlıdır değerinden daha güçlü ve karmaşık sıralama sunar. Dize ve ifade tabanlı sıralama birbirini dışlayan dikkat edin. Varsa dize tabanlı <xref:System.Data.DataView.Sort%2A> sonra ayarlanmış bir <xref:System.Data.DataView> oluşturulur bir sorgudan sorgudan çıkarımı yapılan ifade tabanlı filtre kaldırılır ve sıfırlanamaz.  
  
 Dizini bir <xref:System.Data.DataView> hem olduğunda yerleşik <xref:System.Data.DataView> oluşturulur ve sıralama veya filtreleme herhangi birinde bilgi değiştirilir. Sıralama ölçütü olarak sağlayarak en iyi performansı elde [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] sorgu <xref:System.Data.DataView> oluşturulur ve sıralama Bilgi, daha sonra değiştirme değil. Daha fazla bilgi için bkz: [DataView performans](../../../../docs/framework/data/adonet/dataview-performance.md).  
  
> [!NOTE]
>  Çoğu durumda, sıralama için kullanılan ifadeleri yan etkileri olmamalıdır ve belirleyici olması gerekir. Ayrıca, ifadeleri herhangi içermemelidir sıralama işlemleri olabilir çünkü yürütmeleri, kümesi sayısına bağlıdır mantığı yürütülen tüm sayısı.  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, SalesOrderHeader tablosunu sorgular ve sipariş tarihi tarafından döndürülen satır siparişleri; oluşturur bir <xref:System.Data.DataView> Bu sorgudan; ve bağlar <xref:System.Data.DataView> için bir <xref:System.Windows.Forms.BindingSource>.  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryOrderBy](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromqueryorderby)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryOrderBy](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromqueryorderby)]  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, SalesOrderHeader tablosunu sorgular ve toplam miktarı tarafından döndürülen satır siparişleri; oluşturur bir <xref:System.Data.DataView> Bu sorgudan; ve bağlar <xref:System.Data.DataView> için bir <xref:System.Windows.Forms.BindingSource>.  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryOrderBy2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromqueryorderby2)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryOrderBy2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromqueryorderby2)]  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, satış siparişi ayrıntısını tablosunu sorgular ve miktar ve sonra sipariş kimliği tarafından döndürülen satır siparişleri; oluşturur bir <xref:System.Data.DataView> Bu sorgudan; ve bağlar <xref:System.Data.DataView> için bir <xref:System.Windows.Forms.BindingSource>.  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryOrderByThenBy](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromqueryorderbythenby)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryOrderByThenBy](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromqueryorderbythenby)]  
  
## <a name="using-the-string-based-sort-property"></a>Dize tabanlı sıralama özelliği kullanma  
 Dize tabanlı sıralama işlevlerini <xref:System.Data.DataView> ile çalışmaya devam ettiğinden [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]. Sonra bir <xref:System.Data.DataView> gelen oluşturulan bir [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] kullanabileceğiniz sorgu <xref:System.Data.DataView.Sort%2A> sıralama ayarlamak için özellik <xref:System.Data.DataView>.  
  
 Dize tabanlıdır ve ifade tabanlı işlevselliği sıralama karşılıklı olarak birbirini dışlar. Ayarı <xref:System.Data.DataView.Sort%2A> özelliği, ifade tabanlı olmadığını temizleyin sıralama devralınan sorgudan, <xref:System.Data.DataView> oluşturulduğu.  
  
 Dize tabanlı hakkında daha fazla bilgi için <xref:System.Data.DataView.Sort%2A> filtreleme, bkz: [sıralama ve filtreleme verilerini](../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md).  
  
### <a name="example"></a>Örnek  
 İzleme örnekte bir <xref:System.Data.DataView> kişiden tablo ve satırları sipariş sonra ad artan azalan son adına göre sıralar:  
  
 [!code-csharp[DP DataView Samples#LDVStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvstringsort)]
 [!code-vb[DP DataView Samples#LDVStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvstringsort)]  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnekte "S" harfiyle başlayan son adlarını kişi tabloyu sorgular.  A <xref:System.Data.DataView> Bu sorgudan oluşturulur ve bağlı bir <xref:System.Windows.Forms.BindingSource> nesnesi.  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromquerystringsort)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromquerystringsort)]  
  
## <a name="clearing-the-sort"></a>Sıralama temizleme  
 Sıralama bilgileri bir <xref:System.Data.DataView> kullanarak ayarlandıktan sonra temizlenebilir <xref:System.Data.DataView.Sort%2A> özelliği. Sıralama bilgileri temizlemek için iki yolla <xref:System.Data.DataView>:  
  
-   Ayarlama <xref:System.Data.DataView.Sort%2A> özelliğine `null`.  
  
-   Ayarlama <xref:System.Data.DataView.Sort%2A> boş bir dize özelliği.  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnekte bir <xref:System.Data.DataView> sorgudan ve ayarlayarak sıralama temizler <xref:System.Data.DataView.Sort%2A> boş bir dize özelliği:  
  
 [!code-csharp[DP DataView Samples#LDVClearSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearsort)]
 [!code-vb[DP DataView Samples#LDVClearSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearsort)]  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnekte bir <xref:System.Data.DataView> başvurun ve ayarlar <xref:System.Data.DataView.Sort%2A> azalan düzende son ada göre sıralamak için özellik. Ayarlayarak sıralama bilgileri temizlenir <xref:System.Data.DataView.Sort%2A> özelliğine `null`:  
  
 [!code-csharp[DP DataView Samples#LDVClearSort2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearsort2)]
 [!code-vb[DP DataView Samples#LDVClearSort2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearsort2)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri Bağlama ve LINQ to DataSet](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)  
 [DataView ile Filtreleme](../../../../docs/framework/data/adonet/filtering-with-dataview-linq-to-dataset.md)  
 [Verileri Sıralama](http://msdn.microsoft.com/library/6d76e2d7-b418-49b5-ac78-2bcd61169c48)
