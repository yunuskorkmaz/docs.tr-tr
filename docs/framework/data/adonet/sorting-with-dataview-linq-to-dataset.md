---
title: DataView ile sıralama (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 885b3b7b-51c1-42b3-bb29-b925f4f69a6f
ms.openlocfilehash: 2998de7dee34f9b5410bfe53988e0b7cfa797784
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634761"
---
# <a name="sorting-with-dataview-linq-to-dataset"></a>DataView ile sıralama (LINQ to DataSet)
Verileri belirli ölçütlere göre sıralama ve sonra verileri bir kullanıcı arabirimi denetimi aracılığıyla bir istemciye sunma özelliği, veri bağlamanın önemli bir yönüdür. <xref:System.Data.DataView>, verileri sıralamak ve belirli sıralama ölçütlerine göre sıralanmış veri satırlarını döndürmek için çeşitli yollar sağlar. Dize tabanlı sıralama özelliklerine ek olarak, <xref:System.Data.DataView> Sıralama ölçütleri için dil ile tümleşik sorgu (LINQ) ifadelerini de kullanmanıza imkan sağlar. LINQ ifadeleri, dize tabanlı sıralamaya kıyasla çok daha karmaşık ve güçlü sıralama işlemlerine izin verir. Bu konuda, <xref:System.Data.DataView>kullanarak sıralama için her iki yaklaşım da açıklanmaktadır.  
  
## <a name="creating-dataview-from-a-query-with-sorting-information"></a>Sıralama bilgileriyle bir sorgudan DataView oluşturma  
 Bir <xref:System.Data.DataView> nesnesi, bir LINQ to DataSet sorgusundan oluşturulabilir. Bu sorgu bir <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.OrderByDescending%2A>, <xref:System.Linq.Enumerable.ThenBy%2A>veya <xref:System.Linq.Enumerable.ThenByDescending%2A> yan tümcesi içeriyorsa, bu yan tümcelerdeki ifadeler, <xref:System.Data.DataView>verileri sıralamak için temel olarak kullanılır. Örneğin, sorgu `Order By…`ve `Then By…` yan tümceleri içeriyorsa, sonuçta elde edilen <xref:System.Data.DataView> verileri belirtilen her iki sütuna göre sıralamasına neden olur.  
  
 İfade tabanlı sıralama, daha basit dize tabanlı sıralamaya kıyasla daha güçlü ve karmaşık sıralama sağlar. Dize tabanlı ve ifade tabanlı sıralamanın birbirini dışlamadığını unutmayın. Dize tabanlı <xref:System.Data.DataView.Sort%2A> bir sorgudan bir <xref:System.Data.DataView> oluşturulduktan sonra ayarlandıysa, sorgudan çıkarılan ifade tabanlı filtre temizlenir ve sıfırlanamaz.  
  
 <xref:System.Data.DataView> Dizin, <xref:System.Data.DataView> oluşturulduğunda ve sıralama veya filtreleme bilgilerinin herhangi biri değiştirildiğinde oluşturulur. <xref:System.Data.DataView> oluşturulduğu ve sıralama bilgilerini değiştirmeden LINQ to DataSet sorgusunda sıralama ölçütü sağlayarak en iyi performansı elde edersiniz. Daha fazla bilgi için bkz. [DataView performansı](dataview-performance.md).  
  
> [!NOTE]
> Çoğu durumda, sıralama için kullanılan ifadelerin yan etkileri olmaması ve belirleyici olması gerekir. Ayrıca, sıralama işlemleri herhangi bir sayıda yürütülene kadar, ifadeler bir dizi yürütme sayısına bağlı herhangi bir mantığı içermemelidir.  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, SalesOrderHeader tablosunu sorgular ve döndürülen satırları sipariş tarihine göre sıralar; Bu sorgudan bir <xref:System.Data.DataView> oluşturur; ve <xref:System.Data.DataView> bir <xref:System.Windows.Forms.BindingSource>bağlar.  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryOrderBy](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromqueryorderby)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryOrderBy](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromqueryorderby)]  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, SalesOrderHeader tablosunu sorgular ve döndürülen satırı toplam tutara göre sıralar; Bu sorgudan bir <xref:System.Data.DataView> oluşturur; ve <xref:System.Data.DataView> bir <xref:System.Windows.Forms.BindingSource>bağlar.  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryOrderBy2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromqueryorderby2)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryOrderBy2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromqueryorderby2)]  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, SalesOrderDetail tablosunu sorgular ve döndürülen satırları sipariş miktarına göre ve satış siparişi koduna göre sıralar; Bu sorgudan bir <xref:System.Data.DataView> oluşturur; ve <xref:System.Data.DataView> bir <xref:System.Windows.Forms.BindingSource>bağlar.  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryOrderByThenBy](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromqueryorderbythenby)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryOrderByThenBy](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromqueryorderbythenby)]  
  
## <a name="using-the-string-based-sort-property"></a>Dize tabanlı sıralama özelliğini kullanma  
 <xref:System.Data.DataView> dize tabanlı sıralama işlevselliği LINQ to DataSet ile hala işe yarar. Bir <xref:System.Data.DataView> LINQ to DataSet sorgusundan oluşturulduktan sonra, <xref:System.Data.DataView>sıralamayı ayarlamak için <xref:System.Data.DataView.Sort%2A> özelliğini kullanabilirsiniz.  
  
 Dize tabanlı ve ifade tabanlı sıralama işlevselliği birbirini dışlıyor. <xref:System.Data.DataView.Sort%2A> özelliğinin ayarlanması, <xref:System.Data.DataView> oluşturulduğu sorgudan devralınan ifade tabanlı sıralamayı temizler.  
  
 Dize tabanlı <xref:System.Data.DataView.Sort%2A> filtreleme hakkında daha fazla bilgi için bkz. [verileri sıralama ve filtreleme](./dataset-datatable-dataview/sorting-and-filtering-data.md).  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, kişi tablosundan bir <xref:System.Data.DataView> oluşturur ve satırları son ada göre azalan düzende sıralar, ardından artan düzende ilk adı:  
  
 [!code-csharp[DP DataView Samples#LDVStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvstringsort)]
 [!code-vb[DP DataView Samples#LDVStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvstringsort)]  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, "S" harfiyle başlayan son adlarla Ilgili kişi tablosunu sorgular.  Bu sorgudan bir <xref:System.Data.DataView> oluşturulur ve bir <xref:System.Windows.Forms.BindingSource> nesnesine bağlanır.  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromquerystringsort)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromquerystringsort)]  
  
## <a name="clearing-the-sort"></a>Sıralamayı Temizleme  
 <xref:System.Data.DataView> sıralama bilgileri, <xref:System.Data.DataView.Sort%2A> özelliği kullanılarak ayarlandıktan sonra temizlenir. <xref:System.Data.DataView>sıralama bilgilerini temizlemek için iki yol vardır:  
  
- Ayarlama <xref:System.Data.DataView.Sort%2A> özelliğini `null`.  
  
- <xref:System.Data.DataView.Sort%2A> özelliğini boş bir dizeye ayarlayın.  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir sorgudan bir <xref:System.Data.DataView> oluşturur ve <xref:System.Data.DataView.Sort%2A> özelliğini boş bir dizeye ayarlayarak sıralamayı temizler:  
  
 [!code-csharp[DP DataView Samples#LDVClearSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearsort)]
 [!code-vb[DP DataView Samples#LDVClearSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearsort)]  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, kişi tablosundan bir <xref:System.Data.DataView> oluşturur ve <xref:System.Data.DataView.Sort%2A> özelliğini, son ada göre azalan sırada sıralanacak şekilde ayarlar. Sıralama bilgileri daha sonra <xref:System.Data.DataView.Sort%2A> özelliği `null`olarak ayarlanarak temizlenir:  
  
 [!code-csharp[DP DataView Samples#LDVClearSort2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearsort2)]
 [!code-vb[DP DataView Samples#LDVClearSort2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearsort2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Bağlama ve LINQ to DataSet](data-binding-and-linq-to-dataset.md)
- [DataView ile Filtreleme](filtering-with-dataview-linq-to-dataset.md)
- [Verileri Sıralama](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb546145(v=vs.120))
