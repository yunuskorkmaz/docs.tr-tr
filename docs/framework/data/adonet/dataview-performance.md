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
# <a name="dataview-performance"></a><span data-ttu-id="6c3a6-102">DataView Performansı</span><span class="sxs-lookup"><span data-stu-id="6c3a6-102">DataView Performance</span></span>
<span data-ttu-id="6c3a6-103">Bu <xref:System.Data.DataView.Find%2A> konu, <xref:System.Data.DataView.FindRows%2A> <xref:System.Data.DataView> sınıfın yöntemlerini ve yöntemlerini kullanmanın ve bir <xref:System.Data.DataView> Web uygulamasında önbelleğe almanın performans avantajlarını tartışır.</span><span class="sxs-lookup"><span data-stu-id="6c3a6-103">This topic discusses the performance benefits of using the <xref:System.Data.DataView.Find%2A> and <xref:System.Data.DataView.FindRows%2A> methods of the <xref:System.Data.DataView> class, and of caching a <xref:System.Data.DataView> in a Web application.</span></span>  
  
## <a name="find-and-findrows"></a><span data-ttu-id="6c3a6-104">Bul ve BulSatırlar</span><span class="sxs-lookup"><span data-stu-id="6c3a6-104">Find and FindRows</span></span>  
 <span data-ttu-id="6c3a6-105"><xref:System.Data.DataView>bir dizin inşa eder.</span><span class="sxs-lookup"><span data-stu-id="6c3a6-105"><xref:System.Data.DataView> constructs an index.</span></span> <span data-ttu-id="6c3a6-106">Dizin, tablo veya görünümdeki bir veya daha fazla sütundan oluşturulmuş anahtarları içerir.</span><span class="sxs-lookup"><span data-stu-id="6c3a6-106">An index contains keys built from one or more columns in the table or view.</span></span> <span data-ttu-id="6c3a6-107">Bu anahtarlar, anahtar değerleriyle ilişkili <xref:System.Data.DataView> satır veya satırları hızlı ve verimli bir şekilde bulmanızı sağlayan bir yapıda depolanır.</span><span class="sxs-lookup"><span data-stu-id="6c3a6-107">These keys are stored in a structure that enables the <xref:System.Data.DataView> to find the row or rows associated with the key values quickly and efficiently.</span></span> <span data-ttu-id="6c3a6-108">Filtreleme ve sıralama gibi dizini kullanan işlemler, önemli performans artışları görür.</span><span class="sxs-lookup"><span data-stu-id="6c3a6-108">Operations that use the index, such as filtering and sorting, see significant performance increases.</span></span> <span data-ttu-id="6c3a6-109">A <xref:System.Data.DataView> dizini, hem oluşturulduğunda <xref:System.Data.DataView> hem de sıralama veya filtreleme bilgilerinden herhangi biri değiştirildiğinde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6c3a6-109">The index for a <xref:System.Data.DataView> is built both when the <xref:System.Data.DataView> is created and when any of the sorting or filtering information is modified.</span></span> <span data-ttu-id="6c3a6-110">Bir <xref:System.Data.DataView> oluşturma ve daha sonra sıralama veya filtreleme bilgileri ayarı dizin en <xref:System.Data.DataView> az iki kez inşa edilmesine neden olur: bir kez oluşturulduğunda ve yine tür veya filtre özellikleri herhangi biri değiştirildiğinde.</span><span class="sxs-lookup"><span data-stu-id="6c3a6-110">Creating a <xref:System.Data.DataView> and then setting the sorting or filtering information later causes the index to be built at least twice: once when the <xref:System.Data.DataView> is created, and again when any of the sort or filter properties are modified.</span></span> <span data-ttu-id="6c3a6-111">Filtreleme ve sıralama <xref:System.Data.DataView>hakkında daha fazla bilgi için [DataView ile Filtreleme](filtering-with-dataview-linq-to-dataset.md) ve [DataView ile Sıralama'ya](sorting-with-dataview-linq-to-dataset.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="6c3a6-111">For more information about filtering and sorting with <xref:System.Data.DataView>, see [Filtering with DataView](filtering-with-dataview-linq-to-dataset.md) and [Sorting with DataView](sorting-with-dataview-linq-to-dataset.md).</span></span>  
  
 <span data-ttu-id="6c3a6-112">Verilerdeki belirli bir sorgunun sonuçlarını döndürmek istiyorsanız, verilerin bir alt kümesinin dinamik görünümünü sağlamak yerine, <xref:System.Data.DataView.Find%2A> <xref:System.Data.DataView.RowFilter%2A> özelliği <xref:System.Data.DataView.FindRows%2A> ayarlamak <xref:System.Data.DataView>yerine, bu sorgunun veya yöntemlerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6c3a6-112">If you want to return the results of a particular query on the data, as opposed to providing a dynamic view of a subset of the data, you can use the <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> methods of the <xref:System.Data.DataView>, rather than setting the <xref:System.Data.DataView.RowFilter%2A> property.</span></span> <span data-ttu-id="6c3a6-113">Özellik, <xref:System.Data.DataView.RowFilter%2A> bağlı denetimin filtreuygulanmış sonuçları gösterdiği veriye bağlı bir uygulamada en iyi şekilde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6c3a6-113">The <xref:System.Data.DataView.RowFilter%2A> property is best used in a data-bound application where a bound control displays filtered results.</span></span> <span data-ttu-id="6c3a6-114"><xref:System.Data.DataView.RowFilter%2A> Özelliği ayarlamak, uygulamanıza ek yükü ekleyerek ve performansı azaltarak, verilerin dizinini yeniden içerir.</span><span class="sxs-lookup"><span data-stu-id="6c3a6-114">Setting the <xref:System.Data.DataView.RowFilter%2A> property rebuilds the index for the data, adding overhead to your application and decreasing performance.</span></span> <span data-ttu-id="6c3a6-115">Ve <xref:System.Data.DataView.Find%2A> <xref:System.Data.DataView.FindRows%2A> yöntemler, dizinin yeniden oluşturulmasını gerektirmeden geçerli dizini kullanır.</span><span class="sxs-lookup"><span data-stu-id="6c3a6-115">The <xref:System.Data.DataView.Find%2A> and <xref:System.Data.DataView.FindRows%2A> methods use the current index without requiring the index to be rebuilt.</span></span> <span data-ttu-id="6c3a6-116">Eğer aramak <xref:System.Data.DataView.Find%2A> için gidiyoruz <xref:System.Data.DataView.FindRows%2A> ya da sadece bir <xref:System.Data.DataView>kez, o zaman mevcut kullanmalısınız.</span><span class="sxs-lookup"><span data-stu-id="6c3a6-116">If you are going to call <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> only once, then you should use the existing <xref:System.Data.DataView>.</span></span> <span data-ttu-id="6c3a6-117"><xref:System.Data.DataView.Find%2A> Arama yapacaksanız veya <xref:System.Data.DataView.FindRows%2A> birden çok kez arayacaksanız, aramak istediğiniz sütunda dizini yeniden oluşturmak ve ardından <xref:System.Data.DataView> <xref:System.Data.DataView.Find%2A> veya <xref:System.Data.DataView.FindRows%2A> yöntemleri aramak için yeni bir dizin oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6c3a6-117">If you are going to call <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> multiple times, you should create a new <xref:System.Data.DataView> to rebuild the index on the column you want to search on, and then call the <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> methods.</span></span> <span data-ttu-id="6c3a6-118">Ve <xref:System.Data.DataView.FindRows%2A> yöntemler hakkında <xref:System.Data.DataView.Find%2A> daha fazla bilgi için [Bkz. Satır Bulma.](./dataset-datatable-dataview/finding-rows.md)</span><span class="sxs-lookup"><span data-stu-id="6c3a6-118">For more information about the <xref:System.Data.DataView.Find%2A> and <xref:System.Data.DataView.FindRows%2A> methods, see [Finding Rows](./dataset-datatable-dataview/finding-rows.md).</span></span>  
  
 <span data-ttu-id="6c3a6-119">Aşağıdaki örnek, <xref:System.Data.DataView.Find%2A> soyadı "Zhu" ile ilgili bir kişi bulmak için yöntemi kullanır.</span><span class="sxs-lookup"><span data-stu-id="6c3a6-119">The following example uses the <xref:System.Data.DataView.Find%2A> method to find a contact with the last name "Zhu".</span></span>  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryOrderByFind](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromqueryorderbyfind)]
 [!code-vb[DP DataView Samples#LDVFromQueryOrderByFind](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromqueryorderbyfind)]  
  
 <span data-ttu-id="6c3a6-120">Aşağıdaki örnekte <xref:System.Data.DataView.FindRows%2A> tüm kırmızı renkli ürünleri bulmak için yöntem kullanır.</span><span class="sxs-lookup"><span data-stu-id="6c3a6-120">The following example uses the <xref:System.Data.DataView.FindRows%2A> method to find all the red colored products.</span></span>  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryFindRows](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromqueryfindrows)]
 [!code-vb[DP DataView Samples#LDVFromQueryFindRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromqueryfindrows)]  
  
## <a name="aspnet"></a><span data-ttu-id="6c3a6-121">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="6c3a6-121">ASP.NET</span></span>  
 <span data-ttu-id="6c3a6-122">ASP.NET bellekte oluşturmak için geniş sunucu kaynakları gerektiren nesneleri depolamak için izin veren bir önbelleğe alma mekanizması vardır.</span><span class="sxs-lookup"><span data-stu-id="6c3a6-122">ASP.NET has a caching mechanism that allows you to store objects that require extensive server resources to create in memory.</span></span> <span data-ttu-id="6c3a6-123">Bu tür kaynakların önbelleğe alınmış edilmesi, uygulamanızın performansını önemli ölçüde artırabilir.</span><span class="sxs-lookup"><span data-stu-id="6c3a6-123">Caching these types of resources can significantly improve the performance of your application.</span></span> <span data-ttu-id="6c3a6-124">Önbelleğe alma, <xref:System.Web.Caching.Cache> her uygulama için özel önbellek örnekleriyle sınıf tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="6c3a6-124">Caching is implemented by the <xref:System.Web.Caching.Cache> class, with cache instances that are private to each application.</span></span> <span data-ttu-id="6c3a6-125">Yeni <xref:System.Data.DataView> bir nesne oluşturmak kaynak yoğun olabileceğinden, Web sayfası her yenilendirilince yeniden oluşturulması gerekmesin diye bu önbelleğe alma işlevini Web uygulamalarında <xref:System.Data.DataView> kullanmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6c3a6-125">Because creating a new <xref:System.Data.DataView> object can be resource intensive, you might want to use this caching functionality in Web applications so that the <xref:System.Data.DataView> does not have to be rebuilt every time the Web page is refreshed.</span></span>  
  
 <span data-ttu-id="6c3a6-126">Aşağıdaki örnekte, <xref:System.Data.DataView> sayfa yenilendiğinde verilerin yeniden sıralanmaması için önbelleğe alındı.</span><span class="sxs-lookup"><span data-stu-id="6c3a6-126">In the following example, the <xref:System.Data.DataView> is cached so that the data does not have to be re-sorted when the page is refreshed.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6c3a6-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6c3a6-127">See also</span></span>

- [<span data-ttu-id="6c3a6-128">Veri Bağlama ve LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="6c3a6-128">Data Binding and LINQ to DataSet</span></span>](data-binding-and-linq-to-dataset.md)
