---
title: DataView ile sıralama (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 885b3b7b-51c1-42b3-bb29-b925f4f69a6f
ms.openlocfilehash: 496d6f6ffef8d15e368979a67a8beed62ab86c38
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918187"
---
# <a name="sorting-with-dataview-linq-to-dataset"></a>DataView ile sıralama (LINQ to DataSet)
Verileri belirli ölçütlere göre sıralama ve sonra verileri bir kullanıcı arabirimi denetimi aracılığıyla bir istemciye sunma özelliği, veri bağlamanın önemli bir yönüdür. <xref:System.Data.DataView>verileri sıralamak ve belirli sıralama ölçütlerine göre sıralanmış veri satırlarını döndürmek için çeşitli yollar sağlar. Dize tabanlı sıralama yeteneklerine <xref:System.Data.DataView> ek olarak sıralama ölçütlerine yönelik ifadeler de kullanabilirsiniz. [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]ifadeler, dize tabanlı sıralamaya göre çok daha karmaşık ve güçlü sıralama işlemlerine izin verir. Bu konuda, kullanarak <xref:System.Data.DataView>sıralama için her iki yaklaşım da açıklanmaktadır.  
  
## <a name="creating-dataview-from-a-query-with-sorting-information"></a>Sıralama bilgileriyle bir sorgudan DataView oluşturma  
 Bir <xref:System.Data.DataView> nesne, bir LINQ to DataSet sorgusundan oluşturulabilir. Bu <xref:System.Linq.Enumerable.OrderBy%2A>sorgu bir <xref:System.Data.DataView>, <xref:System.Linq.Enumerable.OrderByDescending%2A>, veya <xref:System.Linq.Enumerable.ThenByDescending%2A> yan tümce içeriyorsa, bu yan tümcelerdeki ifadeler, içindeki verileri sıralamaya yönelik temel olarak kullanılır. <xref:System.Linq.Enumerable.ThenBy%2A> Örneğin, sorgu `Order By…`ve `Then By…` yan tümceleri içeriyorsa, sonuçta <xref:System.Data.DataView> verileri belirtilen her iki sütuna göre sıraya alır.  
  
 İfade tabanlı sıralama, daha basit dize tabanlı sıralamaya kıyasla daha güçlü ve karmaşık sıralama sağlar. Dize tabanlı ve ifade tabanlı sıralamanın birbirini dışlamadığını unutmayın. Dize tabanlı <xref:System.Data.DataView.Sort%2A> , bir sorgudan oluşturulduktan <xref:System.Data.DataView> sonra ayarlandıysa, sorgudan çıkarılan ifade tabanlı filtre temizlenir ve sıfırlanamaz.  
  
 ' A <xref:System.Data.DataView> ait dizin, her ikisi de <xref:System.Data.DataView> oluşturulduğunda ve sıralama ya da filtreleme bilgisi değiştirildiğinde oluşturulur. Tarafından oluşturulan LINQ to DataSet sorgusunda <xref:System.Data.DataView> sıralama ölçütlerini sağlayarak en iyi performansı elde edersiniz ve sıralama bilgilerini daha sonra değiştirmez. Daha fazla bilgi için bkz. [DataView performansı](../../../../docs/framework/data/adonet/dataview-performance.md).  
  
> [!NOTE]
> Çoğu durumda, sıralama için kullanılan ifadelerin yan etkileri olmaması ve belirleyici olması gerekir. Ayrıca, sıralama işlemleri herhangi bir sayıda yürütülene kadar, ifadeler bir dizi yürütme sayısına bağlı herhangi bir mantığı içermemelidir.  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, SalesOrderHeader tablosunu sorgular ve döndürülen satırları sipariş tarihine göre sıralar; Bu sorgudan <xref:System.Data.DataView> bir oluşturur ve ' a <xref:System.Data.DataView> <xref:System.Windows.Forms.BindingSource>bağlar.  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryOrderBy](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromqueryorderby)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryOrderBy](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromqueryorderby)]  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, SalesOrderHeader tablosunu sorgular ve döndürülen satırı toplam tutara göre sıralar; Bu sorgudan <xref:System.Data.DataView> bir oluşturur ve ' a <xref:System.Data.DataView> <xref:System.Windows.Forms.BindingSource>bağlar.  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryOrderBy2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromqueryorderby2)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryOrderBy2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromqueryorderby2)]  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, SalesOrderDetail tablosunu sorgular ve döndürülen satırları sipariş miktarına göre ve satış siparişi koduna göre sıralar; Bu sorgudan <xref:System.Data.DataView> bir oluşturur ve ' a <xref:System.Data.DataView> <xref:System.Windows.Forms.BindingSource>bağlar.  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryOrderByThenBy](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromqueryorderbythenby)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryOrderByThenBy](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromqueryorderbythenby)]  
  
## <a name="using-the-string-based-sort-property"></a>Dize tabanlı sıralama özelliğini kullanma  
 Dize tabanlı sıralama işlevselliği <xref:System.Data.DataView> LINQ to DataSet ile hala işe yarar. Bir <xref:System.Data.DataView> LINQ to DataSet sorgusundan oluşturulduktan sonra, üzerinde sıralamayı <xref:System.Data.DataView>ayarlamak için <xref:System.Data.DataView.Sort%2A> özelliğini kullanabilirsiniz.  
  
 Dize tabanlı ve ifade tabanlı sıralama işlevselliği birbirini dışlıyor. Özelliği ayarlandığında, <xref:System.Data.DataView> tarafından oluşturulan sorgudan devralınan ifade tabanlı sıralama temizlenir. <xref:System.Data.DataView.Sort%2A>  
  
 Dize tabanlı <xref:System.Data.DataView.Sort%2A> filtreleme hakkında daha fazla bilgi için bkz. [verileri sıralama ve filtreleme](../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md).  
  
### <a name="example"></a>Örnek  
 Takip eden örnek, kişi <xref:System.Data.DataView> tablosundan bir oluşturur ve satırları son ada göre azalan düzende sıralar, ardından ilk adı artan sırada yapar:  
  
 [!code-csharp[DP DataView Samples#LDVStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvstringsort)]
 [!code-vb[DP DataView Samples#LDVStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvstringsort)]  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, "S" harfiyle başlayan son adlarla Ilgili kişi tablosunu sorgular.  Bu sorgudan oluşturulur ve bir <xref:System.Windows.Forms.BindingSource> nesneye bağlanır. <xref:System.Data.DataView>  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromquerystringsort)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromquerystringsort)]  
  
## <a name="clearing-the-sort"></a>Sıralamayı Temizleme  
 Bir <xref:System.Data.DataView> üzerinde sıralama bilgileri, <xref:System.Data.DataView.Sort%2A> özelliği kullanılarak ayarlandıktan sonra temizlenir. İçindeki <xref:System.Data.DataView>sıralama bilgilerini temizlemek için iki yol vardır:  
  
- Ayarlama <xref:System.Data.DataView.Sort%2A> özelliğini `null`.  
  
- <xref:System.Data.DataView.Sort%2A> Özelliği boş bir dizeye ayarlayın.  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek bir sorgudan bir <xref:System.Data.DataView> sorgu oluşturur ve bu <xref:System.Data.DataView.Sort%2A> özelliği boş bir dizeye ayarlayarak sıralamayı temizler:  
  
 [!code-csharp[DP DataView Samples#LDVClearSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearsort)]
 [!code-vb[DP DataView Samples#LDVClearSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearsort)]  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, kişi tablosundan <xref:System.Data.DataView> bir oluşturur ve özelliği, <xref:System.Data.DataView.Sort%2A> son ada göre azalan sırada sıralanacak şekilde ayarlar. Sıralama bilgileri, <xref:System.Data.DataView.Sort%2A> özelliği şu şekilde `null`ayarlanarak temizlenir:  
  
 [!code-csharp[DP DataView Samples#LDVClearSort2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearsort2)]
 [!code-vb[DP DataView Samples#LDVClearSort2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearsort2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Bağlama ve LINQ to DataSet](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)
- [DataView ile Filtreleme](../../../../docs/framework/data/adonet/filtering-with-dataview-linq-to-dataset.md)
- [Verileri Sıralama](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb546145(v=vs.120))
