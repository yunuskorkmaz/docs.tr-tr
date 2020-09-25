---
title: DataView ile sıralama (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 885b3b7b-51c1-42b3-bb29-b925f4f69a6f
ms.openlocfilehash: d80c00a4b06a31f61a521e7206c204c02106748a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91175284"
---
# <a name="sorting-with-dataview-linq-to-dataset"></a>DataView ile sıralama (LINQ to DataSet)

Verileri belirli ölçütlere göre sıralama ve sonra verileri bir kullanıcı arabirimi denetimi aracılığıyla bir istemciye sunma özelliği, veri bağlamanın önemli bir yönüdür. <xref:System.Data.DataView> verileri sıralamak ve belirli sıralama ölçütlerine göre sıralanmış veri satırlarını döndürmek için çeşitli yollar sağlar. Dize tabanlı sıralama yeteneklerine ek olarak, <xref:System.Data.DataView> Sıralama ölçütleri Için dil Ile tümleşik sorgu (LINQ) ifadelerini de kullanmanıza imkan sağlar. LINQ ifadeleri, dize tabanlı sıralamaya kıyasla çok daha karmaşık ve güçlü sıralama işlemlerine izin verir. Bu konuda, kullanarak sıralama için her iki yaklaşım da açıklanmaktadır <xref:System.Data.DataView> .  
  
## <a name="creating-dataview-from-a-query-with-sorting-information"></a>Sıralama bilgileriyle bir sorgudan DataView oluşturma  

 Bir <xref:System.Data.DataView> nesne, bir LINQ to DataSet sorgusundan oluşturulabilir. Bu sorgu bir,, <xref:System.Linq.Enumerable.OrderBy%2A> <xref:System.Linq.Enumerable.OrderByDescending%2A> <xref:System.Linq.Enumerable.ThenBy%2A> veya <xref:System.Linq.Enumerable.ThenByDescending%2A> yan tümce içeriyorsa, bu yan tümcelerdeki ifadeler, içindeki verileri sıralamaya yönelik temel olarak kullanılır <xref:System.Data.DataView> . Örneğin, sorgu `Order By…` ve `Then By…` yan tümceleri içeriyorsa, sonuçta <xref:System.Data.DataView> verileri belirtilen her iki sütuna göre sıraya alır.  
  
 İfade tabanlı sıralama, daha basit dize tabanlı sıralamaya kıyasla daha güçlü ve karmaşık sıralama sağlar. Dize tabanlı ve ifade tabanlı sıralamanın birbirini dışlamadığını unutmayın. Dize tabanlı, bir <xref:System.Data.DataView.Sort%2A> sorgudan oluşturulduktan sonra ayarlandıysa <xref:System.Data.DataView> , sorgudan çıkarılan ifade tabanlı filtre temizlenir ve sıfırlanamaz.  
  
 ' A ait dizin, <xref:System.Data.DataView> her ikisi de <xref:System.Data.DataView> oluşturulduğunda ve sıralama ya da filtreleme bilgisi değiştirildiğinde oluşturulur. Tarafından oluşturulan LINQ to DataSet sorgusunda sıralama ölçütlerini sağlayarak en iyi performansı elde edersiniz <xref:System.Data.DataView> ve sıralama bilgilerini daha sonra değiştirmez. Daha fazla bilgi için bkz. [DataView performansı](dataview-performance.md).  
  
> [!NOTE]
> Çoğu durumda, sıralama için kullanılan ifadelerin yan etkileri olmaması ve belirleyici olması gerekir. Ayrıca, sıralama işlemleri herhangi bir sayıda yürütülene kadar, ifadeler bir dizi yürütme sayısına bağlı herhangi bir mantığı içermemelidir.  
  
### <a name="example"></a>Örnek  

 Aşağıdaki örnek, SalesOrderHeader tablosunu sorgular ve döndürülen satırları sipariş tarihine göre sıralar; <xref:System.Data.DataView> Bu sorgudan bir oluşturur ve ' <xref:System.Data.DataView> a bağlar <xref:System.Windows.Forms.BindingSource> .  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryOrderBy](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromqueryorderby)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryOrderBy](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromqueryorderby)]  
  
### <a name="example"></a>Örnek  

 Aşağıdaki örnek, SalesOrderHeader tablosunu sorgular ve döndürülen satırı toplam tutara göre sıralar; <xref:System.Data.DataView> Bu sorgudan bir oluşturur ve ' <xref:System.Data.DataView> a bağlar <xref:System.Windows.Forms.BindingSource> .  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryOrderBy2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromqueryorderby2)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryOrderBy2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromqueryorderby2)]  
  
### <a name="example"></a>Örnek  

 Aşağıdaki örnek, SalesOrderDetail tablosunu sorgular ve döndürülen satırları sipariş miktarına göre ve satış siparişi koduna göre sıralar; <xref:System.Data.DataView> Bu sorgudan bir oluşturur ve ' <xref:System.Data.DataView> a bağlar <xref:System.Windows.Forms.BindingSource> .  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryOrderByThenBy](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromqueryorderbythenby)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryOrderByThenBy](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromqueryorderbythenby)]  
  
## <a name="using-the-string-based-sort-property"></a>Dize tabanlı sıralama özelliğini kullanma  

 Dize tabanlı sıralama işlevselliği <xref:System.Data.DataView> LINQ to DataSet ile hala işe yarar. Bir LINQ to DataSet sorgusundan oluşturulduktan sonra, <xref:System.Data.DataView> <xref:System.Data.DataView.Sort%2A> üzerinde sıralamayı ayarlamak için özelliğini kullanabilirsiniz <xref:System.Data.DataView> .  
  
 Dize tabanlı ve ifade tabanlı sıralama işlevselliği birbirini dışlıyor. Özelliği ayarlandığında <xref:System.Data.DataView.Sort%2A> , tarafından oluşturulan sorgudan devralınan ifade tabanlı sıralama temizlenir <xref:System.Data.DataView> .  
  
 Dize tabanlı filtreleme hakkında daha fazla bilgi için <xref:System.Data.DataView.Sort%2A> bkz. [verileri sıralama ve filtreleme](./dataset-datatable-dataview/sorting-and-filtering-data.md).  
  
### <a name="example"></a>Örnek  

 Takip eden örnek, <xref:System.Data.DataView> kişi tablosundan bir oluşturur ve satırları son ada göre azalan düzende sıralar, ardından ilk adı artan sırada yapar:  
  
 [!code-csharp[DP DataView Samples#LDVStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvstringsort)]
 [!code-vb[DP DataView Samples#LDVStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvstringsort)]  
  
### <a name="example"></a>Örnek  

 Aşağıdaki örnek, "S" harfiyle başlayan son adlarla Ilgili kişi tablosunu sorgular.  <xref:System.Data.DataView>Bu sorgudan oluşturulur ve bir <xref:System.Windows.Forms.BindingSource> nesneye bağlanır.  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromquerystringsort)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromquerystringsort)]  
  
## <a name="clearing-the-sort"></a>Sıralamayı Temizleme  

 Bir üzerinde sıralama bilgileri, <xref:System.Data.DataView> özelliği kullanılarak ayarlandıktan sonra temizlenir <xref:System.Data.DataView.Sort%2A> . İçindeki sıralama bilgilerini temizlemek için iki yol vardır <xref:System.Data.DataView> :  
  
- <xref:System.Data.DataView.Sort%2A>Özelliğini olarak ayarlayın `null` .  
  
- <xref:System.Data.DataView.Sort%2A>Özelliği boş bir dizeye ayarlayın.  
  
### <a name="example"></a>Örnek  

 Aşağıdaki örnek bir sorgudan bir <xref:System.Data.DataView> sorgu oluşturur ve bu özelliği boş bir dizeye ayarlayarak sıralamayı temizler <xref:System.Data.DataView.Sort%2A> :  
  
 [!code-csharp[DP DataView Samples#LDVClearSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearsort)]
 [!code-vb[DP DataView Samples#LDVClearSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearsort)]  
  
### <a name="example"></a>Örnek  

 Aşağıdaki örnek, <xref:System.Data.DataView> kişi tablosundan bir oluşturur ve <xref:System.Data.DataView.Sort%2A> özelliği, son ada göre azalan sırada sıralanacak şekilde ayarlar. Sıralama bilgileri, özelliği şu şekilde ayarlanarak temizlenir <xref:System.Data.DataView.Sort%2A> `null` :  
  
 [!code-csharp[DP DataView Samples#LDVClearSort2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearsort2)]
 [!code-vb[DP DataView Samples#LDVClearSort2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearsort2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Bağlama ve LINQ to DataSet](data-binding-and-linq-to-dataset.md)
- [DataView ile Filtreleme](filtering-with-dataview-linq-to-dataset.md)
- [Verileri Sıralama](/previous-versions/visualstudio/visual-studio-2013/bb546145(v=vs.120))
