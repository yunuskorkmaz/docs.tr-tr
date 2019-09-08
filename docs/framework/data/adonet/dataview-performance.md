---
title: DataView Performansı
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 90820e49-9d46-41f6-9a3d-6c0741bbd8eb
ms.openlocfilehash: 51ea09965c423f04c220260248c3501e061820cb
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784146"
---
# <a name="dataview-performance"></a>DataView Performansı
Bu konuda, <xref:System.Data.DataView.Find%2A> <xref:System.Data.DataView> sınıfının ve yöntemlerinin ve <xref:System.Data.DataView.FindRows%2A> bir <xref:System.Data.DataView> Web uygulamasında önbelleğe alma işleminin performans avantajları ele alınmaktadır.  
  
## <a name="find-and-findrows"></a>Bul ve FindRows  
 <xref:System.Data.DataView>bir dizin oluşturur. Dizin, tablo veya görünümdeki bir veya daha fazla sütundan oluşturulan anahtarları içerir. Bu anahtarlar, <xref:System.Data.DataView> anahtar değerleriyle ilişkili satır veya satırları hızlı ve verimli bir şekilde bulmasını sağlayan bir yapıda saklanır. Filtre ve sıralama gibi dizin kullanan işlemler, bkz. önemli performans artışları. ' A <xref:System.Data.DataView> ait dizin, her ikisi de <xref:System.Data.DataView> oluşturulduğunda ve sıralama ya da filtreleme bilgisi değiştirildiğinde oluşturulur. Oluşturma ve daha sonra sıralama veya filtreleme bilgilerini ayarlama, dizinin en az iki kez oluşturulmasına neden olur: oluşturulduğunda bir kez <xref:System.Data.DataView> ve sıralama veya filtre özelliklerinden herhangi biri değiştirildiğinde. <xref:System.Data.DataView> Filtreleme ve sıralama <xref:System.Data.DataView>hakkında daha fazla bilgi için bkz. DataView [ile filtreleme](filtering-with-dataview-linq-to-dataset.md) ve [DataView ile sıralama](sorting-with-dataview-linq-to-dataset.md).  
  
 Verilerin bir alt kümesinin dinamik görünümünü sağlamanın aksine, veriler üzerinde belirli bir sorgunun sonuçlarını döndürmek <xref:System.Data.DataView.Find%2A> istiyorsanız, <xref:System.Data.DataView.RowFilter%2A> özelliği ayarlamak yerine, veya <xref:System.Data.DataView.FindRows%2A> yöntemlerini <xref:System.Data.DataView>kullanabilirsiniz. Özelliği <xref:System.Data.DataView.RowFilter%2A> , bir bağlantılı denetimin filtrelenmiş sonuçları görüntülediği veriye dayalı bir uygulamada en iyi şekilde kullanılır. <xref:System.Data.DataView.RowFilter%2A> Özelliği ayarlamak, verilerin dizinini yeniden oluşturur, uygulamanıza ek yük ekler ve performansı azaltır. Ve <xref:System.Data.DataView.Find%2A> yöntemleri <xref:System.Data.DataView.FindRows%2A> , dizinin yeniden oluşturulmasını gerektirmeden geçerli dizini kullanır. Yalnızca bir kez çağrıyorsa <xref:System.Data.DataView.Find%2A> <xref:System.Data.DataView>, var olanı kullanmanız gerekir. <xref:System.Data.DataView.FindRows%2A> Arayacağım <xref:System.Data.DataView.Find%2A> veya <xref:System.Data.DataView.FindRows%2A> birden çok kez arıyorsanız, arama <xref:System.Data.DataView.Find%2A> yapmak istediğiniz sütunda dizini yeniden oluşturmak <xref:System.Data.DataView> için yeni bir oluşturmanız ve ardından veya <xref:System.Data.DataView.FindRows%2A> yöntemlerini çağırmanız gerekir. <xref:System.Data.DataView.Find%2A> Ve<xref:System.Data.DataView.FindRows%2A> yöntemleri hakkında daha fazla bilgi için bkz. [satırları bulma](./dataset-datatable-dataview/finding-rows.md).  
  
 Aşağıdaki örnek, en son <xref:System.Data.DataView.Find%2A> "Zhu" adıyla bir iletişim bulmak için yöntemini kullanır.  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryOrderByFind](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromqueryorderbyfind)]
 [!code-vb[DP DataView Samples#LDVFromQueryOrderByFind](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromqueryorderbyfind)]  
  
 Aşağıdaki örnek, tüm kırmızı <xref:System.Data.DataView.FindRows%2A> renkli ürünleri bulmak için yöntemini kullanır.  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryFindRows](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromqueryfindrows)]
 [!code-vb[DP DataView Samples#LDVFromQueryFindRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromqueryfindrows)]  
  
## <a name="aspnet"></a>ASP.NET  
 ASP.NET, bellek içinde oluşturulacak kapsamlı sunucu kaynakları gerektiren nesneleri depolamanıza olanak tanıyan bir önbelleğe alma mekanizmasına sahiptir. Bu tür kaynakların önbelleğe alınması, uygulamanızın performansını önemli ölçüde iyileştirebilir. Önbelleğe alma, her bir <xref:System.Web.Caching.Cache> uygulama için özel önbellek örnekleriyle birlikte sınıfı tarafından uygulanır. Yeni <xref:System.Data.DataView> bir nesne oluşturmak kaynak kullanımı yoğun olabileceğinden, Web sayfasında bu önbelleğe alma işlevini <xref:System.Data.DataView> kullanarak Web sayfası her yenilendiğinde yeniden oluşturulması gerekmez.  
  
 Aşağıdaki örnekte <xref:System.Data.DataView> , bir sayfa yenilendiğinde verilerin yeniden sıralanması gerekmez diye önbelleğe alınır.  
  
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

- [Veri Bağlama ve LINQ to DataSet](data-binding-and-linq-to-dataset.md)
