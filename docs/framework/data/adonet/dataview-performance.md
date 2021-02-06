---
description: 'Daha fazla bilgi edinin: DataView performansı'
title: DataView Performansı
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 90820e49-9d46-41f6-9a3d-6c0741bbd8eb
ms.openlocfilehash: 6319eb3846f116b0297df701e9a6abc6c1deb2b3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99651294"
---
# <a name="dataview-performance"></a><span data-ttu-id="24b61-103">DataView Performansı</span><span class="sxs-lookup"><span data-stu-id="24b61-103">DataView Performance</span></span>

<span data-ttu-id="24b61-104">Bu konuda <xref:System.Data.DataView.Find%2A> <xref:System.Data.DataView.FindRows%2A> , sınıfının ve yöntemlerinin ve <xref:System.Data.DataView> bir Web uygulamasında önbelleğe alma işleminin performans avantajları ele alınmaktadır <xref:System.Data.DataView> .</span><span class="sxs-lookup"><span data-stu-id="24b61-104">This topic discusses the performance benefits of using the <xref:System.Data.DataView.Find%2A> and <xref:System.Data.DataView.FindRows%2A> methods of the <xref:System.Data.DataView> class, and of caching a <xref:System.Data.DataView> in a Web application.</span></span>  
  
## <a name="find-and-findrows"></a><span data-ttu-id="24b61-105">Bul ve FindRows</span><span class="sxs-lookup"><span data-stu-id="24b61-105">Find and FindRows</span></span>  

 <span data-ttu-id="24b61-106"><xref:System.Data.DataView> bir dizin oluşturur.</span><span class="sxs-lookup"><span data-stu-id="24b61-106"><xref:System.Data.DataView> constructs an index.</span></span> <span data-ttu-id="24b61-107">Dizin, tablo veya görünümdeki bir veya daha fazla sütundan oluşturulan anahtarları içerir.</span><span class="sxs-lookup"><span data-stu-id="24b61-107">An index contains keys built from one or more columns in the table or view.</span></span> <span data-ttu-id="24b61-108">Bu anahtarlar, <xref:System.Data.DataView> anahtar değerleriyle ilişkili satır veya satırları hızlı ve verimli bir şekilde bulmasını sağlayan bir yapıda saklanır.</span><span class="sxs-lookup"><span data-stu-id="24b61-108">These keys are stored in a structure that enables the <xref:System.Data.DataView> to find the row or rows associated with the key values quickly and efficiently.</span></span> <span data-ttu-id="24b61-109">Filtre ve sıralama gibi dizin kullanan işlemler, bkz. önemli performans artışları.</span><span class="sxs-lookup"><span data-stu-id="24b61-109">Operations that use the index, such as filtering and sorting, see significant performance increases.</span></span> <span data-ttu-id="24b61-110">' A ait dizin, <xref:System.Data.DataView> her ikisi de <xref:System.Data.DataView> oluşturulduğunda ve sıralama ya da filtreleme bilgisi değiştirildiğinde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="24b61-110">The index for a <xref:System.Data.DataView> is built both when the <xref:System.Data.DataView> is created and when any of the sorting or filtering information is modified.</span></span> <span data-ttu-id="24b61-111">Oluşturma <xref:System.Data.DataView> ve daha sonra sıralama veya filtreleme bilgilerini ayarlama, dizinin en az iki kez oluşturulmasına neden olur: oluşturulduğunda bir kez <xref:System.Data.DataView> ve sıralama veya filtre özelliklerinden herhangi biri değiştirildiğinde.</span><span class="sxs-lookup"><span data-stu-id="24b61-111">Creating a <xref:System.Data.DataView> and then setting the sorting or filtering information later causes the index to be built at least twice: once when the <xref:System.Data.DataView> is created, and again when any of the sort or filter properties are modified.</span></span> <span data-ttu-id="24b61-112">Filtreleme ve sıralama hakkında daha fazla bilgi için <xref:System.Data.DataView> bkz. DataView [ile filtreleme](filtering-with-dataview-linq-to-dataset.md) ve [DataView ile sıralama](sorting-with-dataview-linq-to-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="24b61-112">For more information about filtering and sorting with <xref:System.Data.DataView>, see [Filtering with DataView](filtering-with-dataview-linq-to-dataset.md) and [Sorting with DataView](sorting-with-dataview-linq-to-dataset.md).</span></span>  
  
 <span data-ttu-id="24b61-113">Verilerin bir alt kümesinin dinamik görünümünü sağlamanın aksine, veriler üzerinde belirli bir sorgunun sonuçlarını döndürmek istiyorsanız, <xref:System.Data.DataView.Find%2A> özelliği ayarlamak yerine, veya <xref:System.Data.DataView.FindRows%2A> yöntemlerini kullanabilirsiniz <xref:System.Data.DataView> <xref:System.Data.DataView.RowFilter%2A> .</span><span class="sxs-lookup"><span data-stu-id="24b61-113">If you want to return the results of a particular query on the data, as opposed to providing a dynamic view of a subset of the data, you can use the <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> methods of the <xref:System.Data.DataView>, rather than setting the <xref:System.Data.DataView.RowFilter%2A> property.</span></span> <span data-ttu-id="24b61-114"><xref:System.Data.DataView.RowFilter%2A>Özelliği, bir bağlantılı denetimin filtrelenmiş sonuçları görüntülediği veriye dayalı bir uygulamada en iyi şekilde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="24b61-114">The <xref:System.Data.DataView.RowFilter%2A> property is best used in a data-bound application where a bound control displays filtered results.</span></span> <span data-ttu-id="24b61-115">Özelliği ayarlamak <xref:System.Data.DataView.RowFilter%2A> , verilerin dizinini yeniden oluşturur, uygulamanıza ek yük ekler ve performansı azaltır.</span><span class="sxs-lookup"><span data-stu-id="24b61-115">Setting the <xref:System.Data.DataView.RowFilter%2A> property rebuilds the index for the data, adding overhead to your application and decreasing performance.</span></span> <span data-ttu-id="24b61-116"><xref:System.Data.DataView.Find%2A>Ve <xref:System.Data.DataView.FindRows%2A> yöntemleri, dizinin yeniden oluşturulmasını gerektirmeden geçerli dizini kullanır.</span><span class="sxs-lookup"><span data-stu-id="24b61-116">The <xref:System.Data.DataView.Find%2A> and <xref:System.Data.DataView.FindRows%2A> methods use the current index without requiring the index to be rebuilt.</span></span> <span data-ttu-id="24b61-117"><xref:System.Data.DataView.Find%2A> <xref:System.Data.DataView.FindRows%2A> Yalnızca bir kez çağrıyorsa, var olanı kullanmanız gerekir <xref:System.Data.DataView> .</span><span class="sxs-lookup"><span data-stu-id="24b61-117">If you are going to call <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> only once, then you should use the existing <xref:System.Data.DataView>.</span></span> <span data-ttu-id="24b61-118">Arayacağım <xref:System.Data.DataView.Find%2A> veya <xref:System.Data.DataView.FindRows%2A> birden çok kez arıyorsanız, <xref:System.Data.DataView> arama yapmak istediğiniz sütunda dizini yeniden oluşturmak için yeni bir oluşturmanız ve ardından <xref:System.Data.DataView.Find%2A> veya yöntemlerini çağırmanız gerekir <xref:System.Data.DataView.FindRows%2A> .</span><span class="sxs-lookup"><span data-stu-id="24b61-118">If you are going to call <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> multiple times, you should create a new <xref:System.Data.DataView> to rebuild the index on the column you want to search on, and then call the <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> methods.</span></span> <span data-ttu-id="24b61-119">Ve yöntemleri hakkında daha fazla bilgi için <xref:System.Data.DataView.Find%2A> <xref:System.Data.DataView.FindRows%2A> bkz. [satırları bulma](./dataset-datatable-dataview/finding-rows.md).</span><span class="sxs-lookup"><span data-stu-id="24b61-119">For more information about the <xref:System.Data.DataView.Find%2A> and <xref:System.Data.DataView.FindRows%2A> methods, see [Finding Rows](./dataset-datatable-dataview/finding-rows.md).</span></span>  
  
 <span data-ttu-id="24b61-120">Aşağıdaki örnek, <xref:System.Data.DataView.Find%2A> en son "Zhu" adıyla bir iletişim bulmak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="24b61-120">The following example uses the <xref:System.Data.DataView.Find%2A> method to find a contact with the last name "Zhu".</span></span>  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryOrderByFind](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromqueryorderbyfind)]
 [!code-vb[DP DataView Samples#LDVFromQueryOrderByFind](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromqueryorderbyfind)]  
  
 <span data-ttu-id="24b61-121">Aşağıdaki örnek, <xref:System.Data.DataView.FindRows%2A> tüm kırmızı renkli ürünleri bulmak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="24b61-121">The following example uses the <xref:System.Data.DataView.FindRows%2A> method to find all the red colored products.</span></span>  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryFindRows](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromqueryfindrows)]
 [!code-vb[DP DataView Samples#LDVFromQueryFindRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromqueryfindrows)]  
  
## <a name="aspnet"></a><span data-ttu-id="24b61-122">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="24b61-122">ASP.NET</span></span>  

 <span data-ttu-id="24b61-123">ASP.NET, bellek içinde oluşturulacak kapsamlı sunucu kaynakları gerektiren nesneleri depolamanıza olanak tanıyan bir önbelleğe alma mekanizmasına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="24b61-123">ASP.NET has a caching mechanism that allows you to store objects that require extensive server resources to create in memory.</span></span> <span data-ttu-id="24b61-124">Bu tür kaynakların önbelleğe alınması, uygulamanızın performansını önemli ölçüde iyileştirebilir.</span><span class="sxs-lookup"><span data-stu-id="24b61-124">Caching these types of resources can significantly improve the performance of your application.</span></span> <span data-ttu-id="24b61-125">Önbelleğe alma, her bir <xref:System.Web.Caching.Cache> uygulama için özel önbellek örnekleriyle birlikte sınıfı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="24b61-125">Caching is implemented by the <xref:System.Web.Caching.Cache> class, with cache instances that are private to each application.</span></span> <span data-ttu-id="24b61-126">Yeni bir nesne oluşturmak <xref:System.Data.DataView> kaynak kullanımı yoğun olabileceğinden, Web sayfasında bu önbelleğe alma işlevini kullanarak Web <xref:System.Data.DataView> sayfası her yenilendiğinde yeniden oluşturulması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="24b61-126">Because creating a new <xref:System.Data.DataView> object can be resource intensive, you might want to use this caching functionality in Web applications so that the <xref:System.Data.DataView> does not have to be rebuilt every time the Web page is refreshed.</span></span>  
  
 <span data-ttu-id="24b61-127">Aşağıdaki örnekte, <xref:System.Data.DataView> bir sayfa yenilendiğinde verilerin yeniden sıralanması gerekmez diye önbelleğe alınır.</span><span class="sxs-lookup"><span data-stu-id="24b61-127">In the following example, the <xref:System.Data.DataView> is cached so that the data does not have to be re-sorted when the page is refreshed.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="24b61-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="24b61-128">See also</span></span>

- [<span data-ttu-id="24b61-129">Veri Bağlama ve LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="24b61-129">Data Binding and LINQ to DataSet</span></span>](data-binding-and-linq-to-dataset.md)
