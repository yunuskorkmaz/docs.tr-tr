---
title: (LINQ to DataSet) DataView ile sıralama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 885b3b7b-51c1-42b3-bb29-b925f4f69a6f
ms.openlocfilehash: 4d000fd392b653f294a1d749f769f4e3bde5110d
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67504285"
---
# <a name="sorting-with-dataview-linq-to-dataset"></a>(LINQ to DataSet) DataView ile sıralama
Verileri belirli ölçütlere göre sıralayın ve ardından bir UI denetimine üzerinden bir istemciye verileri sunmak olanağı, veri bağlama, önemli bir yönüdür. <xref:System.Data.DataView> verileri sıralama ve sıralama ölçüte göre sıralanmış veri satırları döndürmek için birçok yol sağlar. Yetenekleri, sıralama, dize tabanlı ek olarak <xref:System.Data.DataView> ayrıca kullanmanızı sağlayan [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] sıralama ölçütü ifadeleri. [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] ifadeler dize tabanlıdır sıralama daha çok daha karmaşık ve güçlü sıralama işlemleri için izin verin. Bu konu, her iki yaklaşım kullanarak sıralama açıklar <xref:System.Data.DataView>.  
  
## <a name="creating-dataview-from-a-query-with-sorting-information"></a>Bir sorgunun sıralama bilgileri ile DataView oluşturma  
 A <xref:System.Data.DataView> nesne oluşturulan veri kümesini sorgulamak için bir LINQ. Bu sorgu içeriyorsa bir <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.OrderByDescending%2A>, <xref:System.Linq.Enumerable.ThenBy%2A>, veya <xref:System.Linq.Enumerable.ThenByDescending%2A> yan tümcesi ifadeleri bu yan tümceleri içinde verileri sıralama için temel olarak kullanılır <xref:System.Data.DataView>. Sorgu içeriyorsa, örneğin, `Order By…`ve `Then By…` yan tümceleri, ortaya çıkan <xref:System.Data.DataView> verileri belirtilen her iki sütuna göre sıralama.  
  
 İfade tabanlı sıralama daha basit sıralama dize tabanlı değerinden daha güçlü ve karmaşık sıralama sunar. Dize tabanlı not edin ve ifade tabanlı sıralama karşılıklı olarak birbirini dışlar. Dize tabanlı <xref:System.Data.DataView.Sort%2A> sonra ayarlanmış bir <xref:System.Data.DataView> oluşturulan bir sorgunun sorgudan çıkarılan ifade tabanlı filtre kaldırılır ve sıfırlanamaz.  
  
 Dizin için bir <xref:System.Data.DataView> hem zaman yerleşik <xref:System.Data.DataView> oluşturulur ve herhangi bir sıralama veya filtreleme bilgileri değiştirilir. Sıralama sağlayarak en iyi performansı elde LINQ to DataSet ölçütlerinde sorgu <xref:System.Data.DataView> oluşturulur ve sıralama Bilgi, daha sonra değiştirme değil. Daha fazla bilgi için [DataView performansı](../../../../docs/framework/data/adonet/dataview-performance.md).  
  
> [!NOTE]
>  Çoğu durumda, sıralama için kullanılan ifadeler yan etkileri olmamalıdır ve belirleyici olmalıdır. Ayrıca, ifadeleri herhangi içermemelidir yürütülen herhangi sayıda mantıksal sıralama işlemleri olabileceğinden, yürütmeleri kümesi sayısına bağlıdır.  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, SalesOrderHeader tabloyu sorgular ve sipariş tarihi tarafından döndürülen satırlar sıralar; oluşturur bir <xref:System.Data.DataView> Bu sorgudan; ve bağlar <xref:System.Data.DataView> için bir <xref:System.Windows.Forms.BindingSource>.  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryOrderBy](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromqueryorderby)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryOrderBy](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromqueryorderby)]  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, SalesOrderHeader tabloyu sorgular ve döndürülen satır tarafından toplam tutarın siparişler; oluşturur bir <xref:System.Data.DataView> Bu sorgudan; ve bağlar <xref:System.Data.DataView> için bir <xref:System.Windows.Forms.BindingSource>.  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryOrderBy2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromqueryorderby2)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryOrderBy2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromqueryorderby2)]  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, satış siparişi ayrıntısını tabloyu sorgular ve dönen satırlar miktar ve ardından satış siparişi kodu göre sıralar; oluşturur bir <xref:System.Data.DataView> Bu sorgudan; ve bağlar <xref:System.Data.DataView> için bir <xref:System.Windows.Forms.BindingSource>.  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryOrderByThenBy](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromqueryorderbythenby)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryOrderByThenBy](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromqueryorderbythenby)]  
  
## <a name="using-the-string-based-sort-property"></a>Dize tabanlı sıralama özelliğini kullanma  
 Dize tabanlı sıralama işlevlerini <xref:System.Data.DataView> LINQ to DataSet ile çalışır. Sonra bir <xref:System.Data.DataView> oluşturuldu bir LINQ to DataSet sorgusunda kullanabileceğiniz <xref:System.Data.DataView.Sort%2A> üzerinde sıralama ayarlamak için özellik <xref:System.Data.DataView>.  
  
 Dize tabanlı ve ifade tabanlı işlevleri sıralama birbirini dışlar. Ayarı <xref:System.Data.DataView.Sort%2A> özelliği, ifade tabanlı olmadığını Temizle sıralama devralınan sorgudan, <xref:System.Data.DataView> oluşturulduğu.  
  
 Dize tabanlı hakkında daha fazla bilgi için <xref:System.Data.DataView.Sort%2A> filtreleme, bkz: [sıralama ve filtreleme veri](../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md).  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnekte oluşturur bir <xref:System.Data.DataView> kişiden tablo ve sıra ve artan düzende ad azalan soyadına göre satırları sıralar:  
  
 [!code-csharp[DP DataView Samples#LDVStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvstringsort)]
 [!code-vb[DP DataView Samples#LDVStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvstringsort)]  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, "S" harfi ile başlayan son adlarını kişi tabloyu sorgular.  A <xref:System.Data.DataView> Bu sorgudan oluşturulan ve bağlı bir <xref:System.Windows.Forms.BindingSource> nesne.  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromquerystringsort)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromquerystringsort)]  
  
## <a name="clearing-the-sort"></a>Sıralama temizleme  
 Sıralama bilgileri bir <xref:System.Data.DataView> kullanarak ayarlandıktan sonra temizlenebilir <xref:System.Data.DataView.Sort%2A> özelliği. Sıralama bilgileri temizlemek için iki yolla <xref:System.Data.DataView>:  
  
- Ayarlama <xref:System.Data.DataView.Sort%2A> özelliğini `null`.  
  
- Ayarlama <xref:System.Data.DataView.Sort%2A> boş bir dize özelliği.  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, oluşturur bir <xref:System.Data.DataView> sorgudan ve sıralama ayarlayarak temizler <xref:System.Data.DataView.Sort%2A> boş bir dize özelliğini:  
  
 [!code-csharp[DP DataView Samples#LDVClearSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearsort)]
 [!code-vb[DP DataView Samples#LDVClearSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearsort)]  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, oluşturur bir <xref:System.Data.DataView> başvurun ve kümeleri <xref:System.Data.DataView.Sort%2A> azalan düzende soyadına göre sıralamak için özellik. Ayarlayarak sıralama bilgileri temizlenir <xref:System.Data.DataView.Sort%2A> özelliğini `null`:  
  
 [!code-csharp[DP DataView Samples#LDVClearSort2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearsort2)]
 [!code-vb[DP DataView Samples#LDVClearSort2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearsort2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Bağlama ve LINQ to DataSet](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)
- [DataView ile Filtreleme](../../../../docs/framework/data/adonet/filtering-with-dataview-linq-to-dataset.md)
- [Verileri Sıralama](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb546145(v=vs.120))
