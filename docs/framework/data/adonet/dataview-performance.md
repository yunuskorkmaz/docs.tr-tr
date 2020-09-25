---
title: DataView Performansı
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 90820e49-9d46-41f6-9a3d-6c0741bbd8eb
ms.openlocfilehash: b2483becce31ab75d8b55b7a642c4ada83da59f6
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183357"
---
# <a name="dataview-performance"></a>DataView Performansı

Bu konuda <xref:System.Data.DataView.Find%2A> <xref:System.Data.DataView.FindRows%2A> , sınıfının ve yöntemlerinin ve <xref:System.Data.DataView> bir Web uygulamasında önbelleğe alma işleminin performans avantajları ele alınmaktadır <xref:System.Data.DataView> .  
  
## <a name="find-and-findrows"></a>Bul ve FindRows  

 <xref:System.Data.DataView> bir dizin oluşturur. Dizin, tablo veya görünümdeki bir veya daha fazla sütundan oluşturulan anahtarları içerir. Bu anahtarlar, <xref:System.Data.DataView> anahtar değerleriyle ilişkili satır veya satırları hızlı ve verimli bir şekilde bulmasını sağlayan bir yapıda saklanır. Filtre ve sıralama gibi dizin kullanan işlemler, bkz. önemli performans artışları. ' A ait dizin, <xref:System.Data.DataView> her ikisi de <xref:System.Data.DataView> oluşturulduğunda ve sıralama ya da filtreleme bilgisi değiştirildiğinde oluşturulur. Oluşturma <xref:System.Data.DataView> ve daha sonra sıralama veya filtreleme bilgilerini ayarlama, dizinin en az iki kez oluşturulmasına neden olur: oluşturulduğunda bir kez <xref:System.Data.DataView> ve sıralama veya filtre özelliklerinden herhangi biri değiştirildiğinde. Filtreleme ve sıralama hakkında daha fazla bilgi için <xref:System.Data.DataView> bkz. DataView [ile filtreleme](filtering-with-dataview-linq-to-dataset.md) ve [DataView ile sıralama](sorting-with-dataview-linq-to-dataset.md).  
  
 Verilerin bir alt kümesinin dinamik görünümünü sağlamanın aksine, veriler üzerinde belirli bir sorgunun sonuçlarını döndürmek istiyorsanız, <xref:System.Data.DataView.Find%2A> özelliği ayarlamak yerine, veya <xref:System.Data.DataView.FindRows%2A> yöntemlerini kullanabilirsiniz <xref:System.Data.DataView> <xref:System.Data.DataView.RowFilter%2A> . <xref:System.Data.DataView.RowFilter%2A>Özelliği, bir bağlantılı denetimin filtrelenmiş sonuçları görüntülediği veriye dayalı bir uygulamada en iyi şekilde kullanılır. Özelliği ayarlamak <xref:System.Data.DataView.RowFilter%2A> , verilerin dizinini yeniden oluşturur, uygulamanıza ek yük ekler ve performansı azaltır. <xref:System.Data.DataView.Find%2A>Ve <xref:System.Data.DataView.FindRows%2A> yöntemleri, dizinin yeniden oluşturulmasını gerektirmeden geçerli dizini kullanır. <xref:System.Data.DataView.Find%2A> <xref:System.Data.DataView.FindRows%2A> Yalnızca bir kez çağrıyorsa, var olanı kullanmanız gerekir <xref:System.Data.DataView> . Arayacağım <xref:System.Data.DataView.Find%2A> veya <xref:System.Data.DataView.FindRows%2A> birden çok kez arıyorsanız, <xref:System.Data.DataView> arama yapmak istediğiniz sütunda dizini yeniden oluşturmak için yeni bir oluşturmanız ve ardından <xref:System.Data.DataView.Find%2A> veya yöntemlerini çağırmanız gerekir <xref:System.Data.DataView.FindRows%2A> . Ve yöntemleri hakkında daha fazla bilgi için <xref:System.Data.DataView.Find%2A> <xref:System.Data.DataView.FindRows%2A> bkz. [satırları bulma](./dataset-datatable-dataview/finding-rows.md).  
  
 Aşağıdaki örnek, <xref:System.Data.DataView.Find%2A> en son "Zhu" adıyla bir iletişim bulmak için yöntemini kullanır.  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryOrderByFind](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromqueryorderbyfind)]
 [!code-vb[DP DataView Samples#LDVFromQueryOrderByFind](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromqueryorderbyfind)]  
  
 Aşağıdaki örnek, <xref:System.Data.DataView.FindRows%2A> tüm kırmızı renkli ürünleri bulmak için yöntemini kullanır.  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryFindRows](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromqueryfindrows)]
 [!code-vb[DP DataView Samples#LDVFromQueryFindRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromqueryfindrows)]  
  
## <a name="aspnet"></a>ASP.NET  

 ASP.NET, bellek içinde oluşturulacak kapsamlı sunucu kaynakları gerektiren nesneleri depolamanıza olanak tanıyan bir önbelleğe alma mekanizmasına sahiptir. Bu tür kaynakların önbelleğe alınması, uygulamanızın performansını önemli ölçüde iyileştirebilir. Önbelleğe alma, her bir <xref:System.Web.Caching.Cache> uygulama için özel önbellek örnekleriyle birlikte sınıfı tarafından uygulanır. Yeni bir nesne oluşturmak <xref:System.Data.DataView> kaynak kullanımı yoğun olabileceğinden, Web sayfasında bu önbelleğe alma işlevini kullanarak Web <xref:System.Data.DataView> sayfası her yenilendiğinde yeniden oluşturulması gerekmez.  
  
 Aşağıdaki örnekte, <xref:System.Data.DataView> bir sayfa yenilendiğinde verilerin yeniden sıralanması gerekmez diye önbelleğe alınır.  
  
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
