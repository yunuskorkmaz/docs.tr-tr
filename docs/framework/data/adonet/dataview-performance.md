---
title: DataView Performansı
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 90820e49-9d46-41f6-9a3d-6c0741bbd8eb
ms.openlocfilehash: 7c81619bf4ac6ed084ea63349345dbf3b7f139b0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150694"
---
# <a name="dataview-performance"></a>DataView Performansı
Bu <xref:System.Data.DataView.Find%2A> konu, <xref:System.Data.DataView.FindRows%2A> <xref:System.Data.DataView> sınıfın yöntemlerini ve yöntemlerini kullanmanın ve bir <xref:System.Data.DataView> Web uygulamasında önbelleğe almanın performans avantajlarını tartışır.  
  
## <a name="find-and-findrows"></a>Bul ve BulSatırlar  
 <xref:System.Data.DataView>bir dizin inşa eder. Dizin, tablo veya görünümdeki bir veya daha fazla sütundan oluşturulmuş anahtarları içerir. Bu anahtarlar, anahtar değerleriyle ilişkili <xref:System.Data.DataView> satır veya satırları hızlı ve verimli bir şekilde bulmanızı sağlayan bir yapıda depolanır. Filtreleme ve sıralama gibi dizini kullanan işlemler, önemli performans artışları görür. A <xref:System.Data.DataView> dizini, hem oluşturulduğunda <xref:System.Data.DataView> hem de sıralama veya filtreleme bilgilerinden herhangi biri değiştirildiğinde oluşturulur. Bir <xref:System.Data.DataView> oluşturma ve daha sonra sıralama veya filtreleme bilgileri ayarı dizin en <xref:System.Data.DataView> az iki kez inşa edilmesine neden olur: bir kez oluşturulduğunda ve yine tür veya filtre özellikleri herhangi biri değiştirildiğinde. Filtreleme ve sıralama <xref:System.Data.DataView>hakkında daha fazla bilgi için [DataView ile Filtreleme](filtering-with-dataview-linq-to-dataset.md) ve [DataView ile Sıralama'ya](sorting-with-dataview-linq-to-dataset.md)bakın.  
  
 Verilerdeki belirli bir sorgunun sonuçlarını döndürmek istiyorsanız, verilerin bir alt kümesinin dinamik görünümünü sağlamak yerine, <xref:System.Data.DataView.Find%2A> <xref:System.Data.DataView.RowFilter%2A> özelliği <xref:System.Data.DataView.FindRows%2A> ayarlamak <xref:System.Data.DataView>yerine, bu sorgunun veya yöntemlerini kullanabilirsiniz. Özellik, <xref:System.Data.DataView.RowFilter%2A> bağlı denetimin filtreuygulanmış sonuçları gösterdiği veriye bağlı bir uygulamada en iyi şekilde kullanılır. <xref:System.Data.DataView.RowFilter%2A> Özelliği ayarlamak, uygulamanıza ek yükü ekleyerek ve performansı azaltarak, verilerin dizinini yeniden içerir. Ve <xref:System.Data.DataView.Find%2A> <xref:System.Data.DataView.FindRows%2A> yöntemler, dizinin yeniden oluşturulmasını gerektirmeden geçerli dizini kullanır. Eğer aramak <xref:System.Data.DataView.Find%2A> için gidiyoruz <xref:System.Data.DataView.FindRows%2A> ya da sadece bir <xref:System.Data.DataView>kez, o zaman mevcut kullanmalısınız. <xref:System.Data.DataView.Find%2A> Arama yapacaksanız veya <xref:System.Data.DataView.FindRows%2A> birden çok kez arayacaksanız, aramak istediğiniz sütunda dizini yeniden oluşturmak ve ardından <xref:System.Data.DataView> <xref:System.Data.DataView.Find%2A> veya <xref:System.Data.DataView.FindRows%2A> yöntemleri aramak için yeni bir dizin oluşturmanız gerekir. Ve <xref:System.Data.DataView.FindRows%2A> yöntemler hakkında <xref:System.Data.DataView.Find%2A> daha fazla bilgi için [Bkz. Satır Bulma.](./dataset-datatable-dataview/finding-rows.md)  
  
 Aşağıdaki örnek, <xref:System.Data.DataView.Find%2A> soyadı "Zhu" ile ilgili bir kişi bulmak için yöntemi kullanır.  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryOrderByFind](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromqueryorderbyfind)]
 [!code-vb[DP DataView Samples#LDVFromQueryOrderByFind](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromqueryorderbyfind)]  
  
 Aşağıdaki örnekte <xref:System.Data.DataView.FindRows%2A> tüm kırmızı renkli ürünleri bulmak için yöntem kullanır.  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryFindRows](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromqueryfindrows)]
 [!code-vb[DP DataView Samples#LDVFromQueryFindRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromqueryfindrows)]  
  
## <a name="aspnet"></a>ASP.NET  
 ASP.NET bellekte oluşturmak için geniş sunucu kaynakları gerektiren nesneleri depolamak için izin veren bir önbelleğe alma mekanizması vardır. Bu tür kaynakların önbelleğe alınmış edilmesi, uygulamanızın performansını önemli ölçüde artırabilir. Önbelleğe alma, <xref:System.Web.Caching.Cache> her uygulama için özel önbellek örnekleriyle sınıf tarafından uygulanır. Yeni <xref:System.Data.DataView> bir nesne oluşturmak kaynak yoğun olabileceğinden, Web sayfası her yenilendirilince yeniden oluşturulması gerekmesin diye bu önbelleğe alma işlevini Web uygulamalarında <xref:System.Data.DataView> kullanmak isteyebilirsiniz.  
  
 Aşağıdaki örnekte, <xref:System.Data.DataView> sayfa yenilendiğinde verilerin yeniden sıralanmaması için önbelleğe alındı.  
  
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
