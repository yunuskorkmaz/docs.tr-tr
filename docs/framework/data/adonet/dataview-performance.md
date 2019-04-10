---
title: DataView Performansı
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 90820e49-9d46-41f6-9a3d-6c0741bbd8eb
ms.openlocfilehash: f0a85232b753eed891cded4b0fb1154269b30dc9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59224122"
---
# <a name="dataview-performance"></a>DataView Performansı
Bu konuda performans kullanmanın avantajları anlatılmaktadır <xref:System.Data.DataView.Find%2A> ve <xref:System.Data.DataView.FindRows%2A> yöntemlerinin <xref:System.Data.DataView> sınıfı ve önbelleğe alma bir <xref:System.Data.DataView> bir Web uygulaması.  
  
## <a name="find-and-findrows"></a>Bul ve FindRows  
 <xref:System.Data.DataView> bir dizin oluşturur. Bir dizin tablosu veya görünümündeki bir veya daha fazla sütun oluşturulmuş anahtarları içerir. Bu anahtarları sağlayan bir yapı içinde depolanan <xref:System.Data.DataView> hızla ve verimli bir şekilde anahtar değerleriyle ilişkili satırları ve satır bulunamadı. Filtreleme ve sıralama, gibi ve dizin kullanan işlemleri önemli performans artışları bakın. Dizin için bir <xref:System.Data.DataView> hem zaman yerleşik <xref:System.Data.DataView> oluşturulur ve herhangi bir sıralama veya filtreleme bilgileri değiştirilir. Oluşturma bir <xref:System.Data.DataView> ve en az iki kere derlenmesi için dizini sıralama ayarlama veya daha sonra bilgiler filtreleme neden olur: bir kez zaman <xref:System.Data.DataView> oluşturulur, ve yeniden sıralama veya filtreleme özelliklerinden herhangi birini değiştirildiği. İle sıralama ve filtreleme hakkında daha fazla bilgi için <xref:System.Data.DataView>, bkz: [DataView ile filtreleme](../../../../docs/framework/data/adonet/filtering-with-dataview-linq-to-dataset.md) ve [DataView ile sıralama](../../../../docs/framework/data/adonet/sorting-with-dataview-linq-to-dataset.md).  
  
 Şirket veriler için karşılıklı verilerin bir alt kümesini, dinamik bir görünüm, kullandığınız sağlayan belirli bir sorgunun sonuçlarını döndürmek isterseniz <xref:System.Data.DataView.Find%2A> veya <xref:System.Data.DataView.FindRows%2A> yöntemlerinin <xref:System.Data.DataView>, ayar yerine <xref:System.Data.DataView.RowFilter%2A> özelliği. <xref:System.Data.DataView.RowFilter%2A> Özelliği en iyi şekilde kullanılır verilere bağlı uygulamada nereye bağlantılı denetim filtrelenmiş sonuçları görüntüler. Ayarı <xref:System.Data.DataView.RowFilter%2A> özelliği yükü uygulamanıza ekleme ve performansı azaltarak veri dizini oluşturur. <xref:System.Data.DataView.Find%2A> Ve <xref:System.Data.DataView.FindRows%2A> yöntemlerini yeniden oluşturulması için dizini gerek kalmadan geçerli dizini kullanın. Çağırmak için kullanacaksanız <xref:System.Data.DataView.Find%2A> veya <xref:System.Data.DataView.FindRows%2A> yalnızca bir kez daha sonra mevcut kullanmalısınız <xref:System.Data.DataView>. Çağırmak için kullanacaksanız <xref:System.Data.DataView.Find%2A> veya <xref:System.Data.DataView.FindRows%2A> birden çok kez, yeni bir oluşturmanız gerekir <xref:System.Data.DataView> üzerinde arama yapın ve ardından çağırmak için istediğiniz sütunu dizini yeniden <xref:System.Data.DataView.Find%2A> veya <xref:System.Data.DataView.FindRows%2A> yöntemleri. Hakkında daha fazla bilgi için <xref:System.Data.DataView.Find%2A> ve <xref:System.Data.DataView.FindRows%2A> yöntemleri bkz [satırları bulma](../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md).  
  
 Aşağıdaki örnekte <xref:System.Data.DataView.Find%2A> Soyadı "Zhu" ile bir kişiyi bulmak için yöntemi.  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryOrderByFind](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromqueryorderbyfind)]
 [!code-vb[DP DataView Samples#LDVFromQueryOrderByFind](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromqueryorderbyfind)]  
  
 Aşağıdaki örnekte <xref:System.Data.DataView.FindRows%2A> renkli ürünleri kırmızı bulmak için yöntemi.  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryFindRows](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromqueryfindrows)]
 [!code-vb[DP DataView Samples#LDVFromQueryFindRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromqueryfindrows)]  
  
## <a name="aspnet"></a>ASP.NET  
 ASP.NET bellekte oluşturmaya yönelik kapsamlı sunucu kaynakları gerektiren nesneleri depolamak izin veren bir önbelleğe alma mekanizması vardır. Bu kaynak türlerinin önbelleğe alma, uygulamanızın performansını önemli ölçüde artırabilir. Önbelleğe alma tarafından gerçekleştirilir <xref:System.Web.Caching.Cache> sınıfıyla her uygulamaya özel önbellek örnekleri. Yeni bir oluşturma çünkü <xref:System.Data.DataView> nesne kaynak yoğunluğu olabilir, bunu kullanmak önbelleğe alma işlevinin Web uygulamalarında isteyebilirsiniz böylece <xref:System.Data.DataView> Web sayfa her yenilendiğinde yeniden oluşturulması gerekmez.  
  
 Aşağıdaki örnekte, <xref:System.Data.DataView> böylece veriler, Sayfa yenilendiğinde yeniden sırılanacığını yok önbelleğe alınır.  
  
```vb  
If (Cache("ordersView") = Nothing) Then  
  
Dim dataSet As New DataSet()  
  
   FillDataSet(dataSet)  
  
   Dim orders As DataTable = dataSet.Tables("SalesOrderHeader")  
  
   Dim query = _  
                    From order In orders.AsEnumerable() _  
                    Where order.Field(Of Boolean)("OnlineOrderFlag") = True _  
                    Order By order.Field(Of Decimal)("TotalDue") _  
                    Select order  
  
   Dim view As DataView = query.AsDataView()  
  
   Cache.Insert("ordersView", view)  
  
End If  
  
Dim ordersView = CType(Cache("ordersView"), DataView)  
  
GridView1.DataSource = ordersView  
GridView1.DataBind()  
```  
  
```csharp  
if (Cache["ordersView"] == null)  
{  
   // Fill the DataSet.                  
   DataSet dataSet = FillDataSet();  
  
   DataTable orders = dataSet.Tables["SalesOrderHeader"];  
  
   EnumerableRowCollection<DataRow> query =  
                        from order in orders.AsEnumerable()  
                        where order.Field<bool>("OnlineOrderFlag") == true  
                        orderby order.Field<decimal>("TotalDue")  
                        select order;  
  
   DataView view = query.AsDataView();  
   Cache.Insert("ordersView", view);  
}  
  
DataView ordersView = (DataView)Cache["ordersView"];  
  
GridView1.DataSource = ordersView;  
GridView1.DataBind();  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Bağlama ve LINQ to DataSet](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)
