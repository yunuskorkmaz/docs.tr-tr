---
title: DataView performansı
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 90820e49-9d46-41f6-9a3d-6c0741bbd8eb
ms.openlocfilehash: 41b9e51e804d88227b8812124d25eae21838fc6d
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53610456"
---
# <a name="dataview-performance"></a><span data-ttu-id="ea3a9-102">DataView performansı</span><span class="sxs-lookup"><span data-stu-id="ea3a9-102">DataView Performance</span></span>
<span data-ttu-id="ea3a9-103">Bu konuda performans kullanmanın avantajları anlatılmaktadır <xref:System.Data.DataView.Find%2A> ve <xref:System.Data.DataView.FindRows%2A> yöntemlerinin <xref:System.Data.DataView> sınıfı ve önbelleğe alma bir <xref:System.Data.DataView> bir Web uygulaması.</span><span class="sxs-lookup"><span data-stu-id="ea3a9-103">This topic discusses the performance benefits of using the <xref:System.Data.DataView.Find%2A> and <xref:System.Data.DataView.FindRows%2A> methods of the <xref:System.Data.DataView> class, and of caching a <xref:System.Data.DataView> in a Web application.</span></span>  
  
## <a name="find-and-findrows"></a><span data-ttu-id="ea3a9-104">Bul ve FindRows</span><span class="sxs-lookup"><span data-stu-id="ea3a9-104">Find and FindRows</span></span>  
 <span data-ttu-id="ea3a9-105"><xref:System.Data.DataView> bir dizin oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ea3a9-105"><xref:System.Data.DataView> constructs an index.</span></span> <span data-ttu-id="ea3a9-106">Bir dizin tablosu veya görünümündeki bir veya daha fazla sütun oluşturulmuş anahtarları içerir.</span><span class="sxs-lookup"><span data-stu-id="ea3a9-106">An index contains keys built from one or more columns in the table or view.</span></span> <span data-ttu-id="ea3a9-107">Bu anahtarları sağlayan bir yapı içinde depolanan <xref:System.Data.DataView> hızla ve verimli bir şekilde anahtar değerleriyle ilişkili satırları ve satır bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="ea3a9-107">These keys are stored in a structure that enables the <xref:System.Data.DataView> to find the row or rows associated with the key values quickly and efficiently.</span></span> <span data-ttu-id="ea3a9-108">Filtreleme ve sıralama, gibi ve dizin kullanan işlemleri önemli performans artışları bakın.</span><span class="sxs-lookup"><span data-stu-id="ea3a9-108">Operations that use the index, such as filtering and sorting, see significant performance increases.</span></span> <span data-ttu-id="ea3a9-109">Dizin için bir <xref:System.Data.DataView> hem zaman yerleşik <xref:System.Data.DataView> oluşturulur ve herhangi bir sıralama veya filtreleme bilgileri değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="ea3a9-109">The index for a <xref:System.Data.DataView> is built both when the <xref:System.Data.DataView> is created and when any of the sorting or filtering information is modified.</span></span> <span data-ttu-id="ea3a9-110">Oluşturma bir <xref:System.Data.DataView> ve en az iki kere derlenmesi için dizini sıralama ayarlama veya daha sonra bilgiler filtreleme neden olur: bir kez zaman <xref:System.Data.DataView> oluşturulur, ve yeniden sıralama veya filtreleme özelliklerinden herhangi birini değiştirildiği.</span><span class="sxs-lookup"><span data-stu-id="ea3a9-110">Creating a <xref:System.Data.DataView> and then setting the sorting or filtering information later causes the index to be built at least twice: once when the <xref:System.Data.DataView> is created, and again when any of the sort or filter properties are modified.</span></span> <span data-ttu-id="ea3a9-111">İle sıralama ve filtreleme hakkında daha fazla bilgi için <xref:System.Data.DataView>, bkz: [DataView ile filtreleme](../../../../docs/framework/data/adonet/filtering-with-dataview-linq-to-dataset.md) ve [DataView ile sıralama](../../../../docs/framework/data/adonet/sorting-with-dataview-linq-to-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="ea3a9-111">For more information about filtering and sorting with <xref:System.Data.DataView>, see [Filtering with DataView](../../../../docs/framework/data/adonet/filtering-with-dataview-linq-to-dataset.md) and [Sorting with DataView](../../../../docs/framework/data/adonet/sorting-with-dataview-linq-to-dataset.md).</span></span>  
  
 <span data-ttu-id="ea3a9-112">Şirket veriler için karşılıklı verilerin bir alt kümesini, dinamik bir görünüm, kullandığınız sağlayan belirli bir sorgunun sonuçlarını döndürmek isterseniz <xref:System.Data.DataView.Find%2A> veya <xref:System.Data.DataView.FindRows%2A> yöntemlerinin <xref:System.Data.DataView>, ayar yerine <xref:System.Data.DataView.RowFilter%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="ea3a9-112">If you want to return the results of a particular query on the data, as opposed to providing a dynamic view of a subset of the data, you can use the <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> methods of the <xref:System.Data.DataView>, rather than setting the <xref:System.Data.DataView.RowFilter%2A> property.</span></span> <span data-ttu-id="ea3a9-113"><xref:System.Data.DataView.RowFilter%2A> Özelliği en iyi şekilde kullanılır verilere bağlı uygulamada nereye bağlantılı denetim filtrelenmiş sonuçları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="ea3a9-113">The <xref:System.Data.DataView.RowFilter%2A> property is best used in a data-bound application where a bound control displays filtered results.</span></span> <span data-ttu-id="ea3a9-114">Ayarı <xref:System.Data.DataView.RowFilter%2A> özelliği yükü uygulamanıza ekleme ve performansı azaltarak veri dizini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ea3a9-114">Setting the <xref:System.Data.DataView.RowFilter%2A> property rebuilds the index for the data, adding overhead to your application and decreasing performance.</span></span> <span data-ttu-id="ea3a9-115"><xref:System.Data.DataView.Find%2A> Ve <xref:System.Data.DataView.FindRows%2A> yöntemlerini yeniden oluşturulması için dizini gerek kalmadan geçerli dizini kullanın.</span><span class="sxs-lookup"><span data-stu-id="ea3a9-115">The <xref:System.Data.DataView.Find%2A> and <xref:System.Data.DataView.FindRows%2A> methods use the current index without requiring the index to be rebuilt.</span></span> <span data-ttu-id="ea3a9-116">Çağırmak için kullanacaksanız <xref:System.Data.DataView.Find%2A> veya <xref:System.Data.DataView.FindRows%2A> yalnızca bir kez daha sonra mevcut kullanmalısınız <xref:System.Data.DataView>.</span><span class="sxs-lookup"><span data-stu-id="ea3a9-116">If you are going to call <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> only once, then you should use the existing <xref:System.Data.DataView>.</span></span> <span data-ttu-id="ea3a9-117">Çağırmak için kullanacaksanız <xref:System.Data.DataView.Find%2A> veya <xref:System.Data.DataView.FindRows%2A> birden çok kez, yeni bir oluşturmanız gerekir <xref:System.Data.DataView> üzerinde arama yapın ve ardından çağırmak için istediğiniz sütunu dizini yeniden <xref:System.Data.DataView.Find%2A> veya <xref:System.Data.DataView.FindRows%2A> yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="ea3a9-117">If you are going to call <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> multiple times, you should create a new <xref:System.Data.DataView> to rebuild the index on the column you want to search on, and then call the <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> methods.</span></span> <span data-ttu-id="ea3a9-118">Hakkında daha fazla bilgi için <xref:System.Data.DataView.Find%2A> ve <xref:System.Data.DataView.FindRows%2A> yöntemleri bkz [satırları bulma](../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md).</span><span class="sxs-lookup"><span data-stu-id="ea3a9-118">For more information about the <xref:System.Data.DataView.Find%2A> and <xref:System.Data.DataView.FindRows%2A> methods, see [Finding Rows](../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md).</span></span>  
  
 <span data-ttu-id="ea3a9-119">Aşağıdaki örnekte <xref:System.Data.DataView.Find%2A> Soyadı "Zhu" ile bir kişiyi bulmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ea3a9-119">The following example uses the <xref:System.Data.DataView.Find%2A> method to find a contact with the last name "Zhu".</span></span>  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryOrderByFind](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromqueryorderbyfind)]
 [!code-vb[DP DataView Samples#LDVFromQueryOrderByFind](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromqueryorderbyfind)]  
  
 <span data-ttu-id="ea3a9-120">Aşağıdaki örnekte <xref:System.Data.DataView.FindRows%2A> renkli ürünleri kırmızı bulmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ea3a9-120">The following example uses the <xref:System.Data.DataView.FindRows%2A> method to find all the red colored products.</span></span>  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryFindRows](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromqueryfindrows)]
 [!code-vb[DP DataView Samples#LDVFromQueryFindRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromqueryfindrows)]  
  
## <a name="aspnet"></a><span data-ttu-id="ea3a9-121">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="ea3a9-121">ASP.NET</span></span>  
 <span data-ttu-id="ea3a9-122">ASP.NET bellekte oluşturmaya yönelik kapsamlı sunucu kaynakları gerektiren nesneleri depolamak izin veren bir önbelleğe alma mekanizması vardır.</span><span class="sxs-lookup"><span data-stu-id="ea3a9-122">ASP.NET has a caching mechanism that allows you to store objects that require extensive server resources to create in memory.</span></span> <span data-ttu-id="ea3a9-123">Bu kaynak türlerinin önbelleğe alma, uygulamanızın performansını önemli ölçüde artırabilir.</span><span class="sxs-lookup"><span data-stu-id="ea3a9-123">Caching these types of resources can significantly improve the performance of your application.</span></span> <span data-ttu-id="ea3a9-124">Önbelleğe alma tarafından gerçekleştirilir <xref:System.Web.Caching.Cache> sınıfıyla her uygulamaya özel önbellek örnekleri.</span><span class="sxs-lookup"><span data-stu-id="ea3a9-124">Caching is implemented by the <xref:System.Web.Caching.Cache> class, with cache instances that are private to each application.</span></span> <span data-ttu-id="ea3a9-125">Yeni bir oluşturma çünkü <xref:System.Data.DataView> nesne kaynak yoğunluğu olabilir, bunu kullanmak önbelleğe alma işlevinin Web uygulamalarında isteyebilirsiniz böylece <xref:System.Data.DataView> Web sayfa her yenilendiğinde yeniden oluşturulması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="ea3a9-125">Because creating a new <xref:System.Data.DataView> object can be resource intensive, you might want to use this caching functionality in Web applications so that the <xref:System.Data.DataView> does not have to be rebuilt every time the Web page is refreshed.</span></span>  
  
 <span data-ttu-id="ea3a9-126">Aşağıdaki örnekte, <xref:System.Data.DataView> böylece veriler, Sayfa yenilendiğinde yeniden sırılanacığını yok önbelleğe alınır.</span><span class="sxs-lookup"><span data-stu-id="ea3a9-126">In the following example, the <xref:System.Data.DataView> is cached so that the data does not have to be re-sorted when the page is refreshed.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ea3a9-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ea3a9-127">See Also</span></span>  
 [<span data-ttu-id="ea3a9-128">Veri Bağlama ve LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="ea3a9-128">Data Binding and LINQ to DataSet</span></span>](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)
