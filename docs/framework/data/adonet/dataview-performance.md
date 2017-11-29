---
title: "DataView performansı"
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
ms.assetid: 90820e49-9d46-41f6-9a3d-6c0741bbd8eb
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 3b1f702740b1085302e413120f2bdd23c1613b25
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="dataview-performance"></a>DataView performansı
Bu konu kullanarak performans yararlarını açıklar <xref:System.Data.DataView.Find%2A> ve <xref:System.Data.DataView.FindRows%2A> yöntemlerinin <xref:System.Data.DataView> sınıfı ve önbelleğe alma bir <xref:System.Data.DataView> bir Web uygulaması.  
  
## <a name="find-and-findrows"></a>Bul ve FindRows  
 <xref:System.Data.DataView>bir dizin oluşturur. Bir dizin, bir veya daha fazla sütun tablo veya Görünüm oluşturulmuş anahtarları içerir. Bu anahtarları sağlayan bir yapısında depolanmış <xref:System.Data.DataView> hızlı ve verimli bir şekilde anahtar değerleriyle ilişkili satırları ve satır bulunamadı. Filtreleme ve sıralama, gibi dizin kullanan işlemler signifcant performans artışı bakın. Dizini bir <xref:System.Data.DataView> hem olduğunda yerleşik <xref:System.Data.DataView> oluşturulur ve sıralama veya filtreleme herhangi birinde bilgi değiştirilir. Oluşturma bir <xref:System.Data.DataView> ve en az iki kez oluşturulacak dizin sıralama ayarlama veya bilgileri daha sonra filtreleme neden olur: sonra zaman <xref:System.Data.DataView> oluşturulduğu ve yeniden sıralama veya filtre özelliklerden herhangi biri değiştirildiği. Sıralama ve filtreleme hakkında daha fazla bilgi için <xref:System.Data.DataView>, bkz: [DataView ile filtreleme](../../../../docs/framework/data/adonet/filtering-with-dataview-linq-to-dataset.md) ve [DataView ile sıralama](../../../../docs/framework/data/adonet/sorting-with-dataview-linq-to-dataset.md).  
  
 Bir veri alt kümesini, dinamik bir görünümü, kullandığınız sağlanması karşılıklı için olarak veriler üzerinde belirli bir sorgu sonuçlarını döndürmek istiyorsanız <xref:System.Data.DataView.Find%2A> veya <xref:System.Data.DataView.FindRows%2A> yöntemlerinin <xref:System.Data.DataView>, ayar yerine <xref:System.Data.DataView.RowFilter%2A> özelliği. <xref:System.Data.DataView.RowFilter%2A> Özelliği en iyi kullanılır verilere bağlı uygulamada burada bağlantılı denetim filtrelenen sonuçları görüntüler. Ayar <xref:System.Data.DataView.RowFilter%2A> özelliği veri yükü uygulamanıza ekleme ve performans azaltmak için dizini yeniden oluşturur. <xref:System.Data.DataView.Find%2A> Ve <xref:System.Data.DataView.FindRows%2A> yöntemleri yeniden oluşturulması için dizin gerek kalmadan geçerli dizini kullanın. Çağrı kullanacaksanız <xref:System.Data.DataView.Find%2A> veya <xref:System.Data.DataView.FindRows%2A> yalnızca bir kez daha sonra varolan kullanmanız gereken <xref:System.Data.DataView>. Çağrı kullanacaksanız <xref:System.Data.DataView.Find%2A> veya <xref:System.Data.DataView.FindRows%2A> birden çok kez, yeni bir oluşturmalısınız <xref:System.Data.DataView> arayın ve ardından arama yapmak istediğiniz sütunu dizini yeniden oluşturmak için <xref:System.Data.DataView.Find%2A> veya <xref:System.Data.DataView.FindRows%2A> yöntemleri. Hakkında daha fazla bilgi için <xref:System.Data.DataView.Find%2A> ve <xref:System.Data.DataView.FindRows%2A> yöntemleri bkz [bulma satırları](../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md).  
  
 Aşağıdaki örnek kullanır <xref:System.Data.DataView.Find%2A> Soyadı "Zhu" kişiyle bulmak için yöntem.  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryOrderByFind](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromqueryorderbyfind)]
 [!code-vb[DP DataView Samples#LDVFromQueryOrderByFind](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromqueryorderbyfind)]  
  
 Aşağıdaki örnek kullanır <xref:System.Data.DataView.FindRows%2A> tüm kırmızı bulmak için yöntem renkli ürünler.  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryFindRows](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromqueryfindrows)]
 [!code-vb[DP DataView Samples#LDVFromQueryFindRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromqueryfindrows)]  
  
## <a name="aspnet"></a>ASP.NET  
 ASP.NET bellekte oluşturmak için kapsamlı sunucu kaynaklarını gerektiren nesnelerini depolamak izin veren bir önbelleğe alma mekanizması vardır. Bu türdeki kaynağı önbelleğe alma, uygulamanızın performansını önemli ölçüde artırabilir. Önbelleğe alma tarafından gerçekleştirilir <xref:System.Web.Caching.Cache> sınıfıyla her uygulama için özel önbelleği örnekleri. Yeni bir oluşturma çünkü <xref:System.Data.DataView> nesne yoğun kaynak olabilir, bunu kullanmak önbelleğe alma işlevinin Web uygulamalarında isteyebilirsiniz böylece <xref:System.Data.DataView> Web sayfası her yenilendiğinde yeniden gerekmez.  
  
 Aşağıdaki örnekte, <xref:System.Data.DataView> verileri, Sayfa yenilendiğinde yeniden sıralanması gerekmez. böylece önbelleğe alınır.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri bağlama ve LINQ-DataSet](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)
