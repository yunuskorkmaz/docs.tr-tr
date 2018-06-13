---
title: DataView performansı
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 90820e49-9d46-41f6-9a3d-6c0741bbd8eb
ms.openlocfilehash: df7c5525738d23a1489bfeec75d2c6b1dbd29e94
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32762786"
---
# <a name="dataview-performance"></a><span data-ttu-id="52207-102">DataView performansı</span><span class="sxs-lookup"><span data-stu-id="52207-102">DataView Performance</span></span>
<span data-ttu-id="52207-103">Bu konu kullanarak performans yararlarını açıklar <xref:System.Data.DataView.Find%2A> ve <xref:System.Data.DataView.FindRows%2A> yöntemlerinin <xref:System.Data.DataView> sınıfı ve önbelleğe alma bir <xref:System.Data.DataView> bir Web uygulaması.</span><span class="sxs-lookup"><span data-stu-id="52207-103">This topic discusses the performance benefits of using the <xref:System.Data.DataView.Find%2A> and <xref:System.Data.DataView.FindRows%2A> methods of the <xref:System.Data.DataView> class, and of caching a <xref:System.Data.DataView> in a Web application.</span></span>  
  
## <a name="find-and-findrows"></a><span data-ttu-id="52207-104">Bul ve FindRows</span><span class="sxs-lookup"><span data-stu-id="52207-104">Find and FindRows</span></span>  
 <span data-ttu-id="52207-105"><xref:System.Data.DataView> bir dizin oluşturur.</span><span class="sxs-lookup"><span data-stu-id="52207-105"><xref:System.Data.DataView> constructs an index.</span></span> <span data-ttu-id="52207-106">Bir dizin, bir veya daha fazla sütun tablo veya Görünüm oluşturulmuş anahtarları içerir.</span><span class="sxs-lookup"><span data-stu-id="52207-106">An index contains keys built from one or more columns in the table or view.</span></span> <span data-ttu-id="52207-107">Bu anahtarları sağlayan bir yapısında depolanmış <xref:System.Data.DataView> hızlı ve verimli bir şekilde anahtar değerleriyle ilişkili satırları ve satır bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="52207-107">These keys are stored in a structure that enables the <xref:System.Data.DataView> to find the row or rows associated with the key values quickly and efficiently.</span></span> <span data-ttu-id="52207-108">Filtreleme ve sıralama, gibi dizin kullanan işlemler signifcant performans artışı bakın.</span><span class="sxs-lookup"><span data-stu-id="52207-108">Operations that use the index, such as filtering and sorting, see signifcant performance increases.</span></span> <span data-ttu-id="52207-109">Dizini bir <xref:System.Data.DataView> hem olduğunda yerleşik <xref:System.Data.DataView> oluşturulur ve sıralama veya filtreleme herhangi birinde bilgi değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="52207-109">The index for a <xref:System.Data.DataView> is built both when the <xref:System.Data.DataView> is created and when any of the sorting or filtering information is modified.</span></span> <span data-ttu-id="52207-110">Oluşturma bir <xref:System.Data.DataView> ve en az iki kez oluşturulacak dizin sıralama ayarlama veya bilgileri daha sonra filtreleme neden olur: sonra zaman <xref:System.Data.DataView> oluşturulduğu ve yeniden sıralama veya filtre özelliklerden herhangi biri değiştirildiği.</span><span class="sxs-lookup"><span data-stu-id="52207-110">Creating a <xref:System.Data.DataView> and then setting the sorting or filtering information later causes the index to be built at least twice: once when the <xref:System.Data.DataView> is created, and again when any of the sort or filter properties are modified.</span></span> <span data-ttu-id="52207-111">Sıralama ve filtreleme hakkında daha fazla bilgi için <xref:System.Data.DataView>, bkz: [DataView ile filtreleme](../../../../docs/framework/data/adonet/filtering-with-dataview-linq-to-dataset.md) ve [DataView ile sıralama](../../../../docs/framework/data/adonet/sorting-with-dataview-linq-to-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="52207-111">For more information about filtering and sorting with <xref:System.Data.DataView>, see [Filtering with DataView](../../../../docs/framework/data/adonet/filtering-with-dataview-linq-to-dataset.md) and [Sorting with DataView](../../../../docs/framework/data/adonet/sorting-with-dataview-linq-to-dataset.md).</span></span>  
  
 <span data-ttu-id="52207-112">Bir veri alt kümesini, dinamik bir görünümü, kullandığınız sağlanması karşılıklı için olarak veriler üzerinde belirli bir sorgu sonuçlarını döndürmek istiyorsanız <xref:System.Data.DataView.Find%2A> veya <xref:System.Data.DataView.FindRows%2A> yöntemlerinin <xref:System.Data.DataView>, ayar yerine <xref:System.Data.DataView.RowFilter%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="52207-112">If you want to return the results of a particular query on the data, as opposed to providing a dynamic view of a subset of the data, you can use the <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> methods of the <xref:System.Data.DataView>, rather than setting the <xref:System.Data.DataView.RowFilter%2A> property.</span></span> <span data-ttu-id="52207-113"><xref:System.Data.DataView.RowFilter%2A> Özelliği en iyi kullanılır verilere bağlı uygulamada burada bağlantılı denetim filtrelenen sonuçları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="52207-113">The <xref:System.Data.DataView.RowFilter%2A> property is best used in a data-bound application where a bound control displays filtered results.</span></span> <span data-ttu-id="52207-114">Ayar <xref:System.Data.DataView.RowFilter%2A> özelliği veri yükü uygulamanıza ekleme ve performans azaltmak için dizini yeniden oluşturur.</span><span class="sxs-lookup"><span data-stu-id="52207-114">Setting the <xref:System.Data.DataView.RowFilter%2A> property rebuilds the index for the data, adding overhead to your application and decreasing performance.</span></span> <span data-ttu-id="52207-115"><xref:System.Data.DataView.Find%2A> Ve <xref:System.Data.DataView.FindRows%2A> yöntemleri yeniden oluşturulması için dizin gerek kalmadan geçerli dizini kullanın.</span><span class="sxs-lookup"><span data-stu-id="52207-115">The <xref:System.Data.DataView.Find%2A> and <xref:System.Data.DataView.FindRows%2A> methods use the current index without requiring the index to be rebuilt.</span></span> <span data-ttu-id="52207-116">Çağrı kullanacaksanız <xref:System.Data.DataView.Find%2A> veya <xref:System.Data.DataView.FindRows%2A> yalnızca bir kez daha sonra varolan kullanmanız gereken <xref:System.Data.DataView>.</span><span class="sxs-lookup"><span data-stu-id="52207-116">If you are going to call <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> only once, then you should use the existing <xref:System.Data.DataView>.</span></span> <span data-ttu-id="52207-117">Çağrı kullanacaksanız <xref:System.Data.DataView.Find%2A> veya <xref:System.Data.DataView.FindRows%2A> birden çok kez, yeni bir oluşturmalısınız <xref:System.Data.DataView> arayın ve ardından arama yapmak istediğiniz sütunu dizini yeniden oluşturmak için <xref:System.Data.DataView.Find%2A> veya <xref:System.Data.DataView.FindRows%2A> yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="52207-117">If you are going to call <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> multiple times, you should create a new <xref:System.Data.DataView> to rebuild the index on the column you want to search on, and then call the <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> methods.</span></span> <span data-ttu-id="52207-118">Hakkında daha fazla bilgi için <xref:System.Data.DataView.Find%2A> ve <xref:System.Data.DataView.FindRows%2A> yöntemleri bkz [bulma satırları](../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md).</span><span class="sxs-lookup"><span data-stu-id="52207-118">For more information about the <xref:System.Data.DataView.Find%2A> and <xref:System.Data.DataView.FindRows%2A> methods, see [Finding Rows](../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md).</span></span>  
  
 <span data-ttu-id="52207-119">Aşağıdaki örnek kullanır <xref:System.Data.DataView.Find%2A> Soyadı "Zhu" kişiyle bulmak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="52207-119">The following example uses the <xref:System.Data.DataView.Find%2A> method to find a contact with the last name "Zhu".</span></span>  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryOrderByFind](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromqueryorderbyfind)]
 [!code-vb[DP DataView Samples#LDVFromQueryOrderByFind](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromqueryorderbyfind)]  
  
 <span data-ttu-id="52207-120">Aşağıdaki örnek kullanır <xref:System.Data.DataView.FindRows%2A> tüm kırmızı bulmak için yöntem renkli ürünler.</span><span class="sxs-lookup"><span data-stu-id="52207-120">The following example uses the <xref:System.Data.DataView.FindRows%2A> method to find all the red colored products.</span></span>  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryFindRows](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromqueryfindrows)]
 [!code-vb[DP DataView Samples#LDVFromQueryFindRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromqueryfindrows)]  
  
## <a name="aspnet"></a><span data-ttu-id="52207-121">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="52207-121">ASP.NET</span></span>  
 <span data-ttu-id="52207-122">ASP.NET bellekte oluşturmak için kapsamlı sunucu kaynaklarını gerektiren nesnelerini depolamak izin veren bir önbelleğe alma mekanizması vardır.</span><span class="sxs-lookup"><span data-stu-id="52207-122">ASP.NET has a caching mechanism that allows you to store objects that require extensive server resources to create in memory.</span></span> <span data-ttu-id="52207-123">Bu türdeki kaynağı önbelleğe alma, uygulamanızın performansını önemli ölçüde artırabilir.</span><span class="sxs-lookup"><span data-stu-id="52207-123">Caching these types of resources can significantly improve the performance of your application.</span></span> <span data-ttu-id="52207-124">Önbelleğe alma tarafından gerçekleştirilir <xref:System.Web.Caching.Cache> sınıfıyla her uygulama için özel önbelleği örnekleri.</span><span class="sxs-lookup"><span data-stu-id="52207-124">Caching is implemented by the <xref:System.Web.Caching.Cache> class, with cache instances that are private to each application.</span></span> <span data-ttu-id="52207-125">Yeni bir oluşturma çünkü <xref:System.Data.DataView> nesne yoğun kaynak olabilir, bunu kullanmak önbelleğe alma işlevinin Web uygulamalarında isteyebilirsiniz böylece <xref:System.Data.DataView> Web sayfası her yenilendiğinde yeniden gerekmez.</span><span class="sxs-lookup"><span data-stu-id="52207-125">Because creating a new <xref:System.Data.DataView> object can be resource intensive, you might want to use this caching functionality in Web applications so that the <xref:System.Data.DataView> does not have to be rebuilt every time the Web page is refreshed.</span></span>  
  
 <span data-ttu-id="52207-126">Aşağıdaki örnekte, <xref:System.Data.DataView> verileri, Sayfa yenilendiğinde yeniden sıralanması gerekmez. böylece önbelleğe alınır.</span><span class="sxs-lookup"><span data-stu-id="52207-126">In the following example, the <xref:System.Data.DataView> is cached so that the data does not have to be re-sorted when the page is refreshed.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="52207-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="52207-127">See Also</span></span>  
 [<span data-ttu-id="52207-128">Veri Bağlama ve LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="52207-128">Data Binding and LINQ to DataSet</span></span>](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)
