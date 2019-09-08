---
title: Sorgu Sonucunu Sayfalama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fa360c46-e5f8-411e-a711-46997771133d
ms.openlocfilehash: 1dbaa159314bf7bb05ff75287f601f619834fd7c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794618"
---
# <a name="paging-through-a-query-result"></a><span data-ttu-id="be7b2-102">Sorgu Sonucunu Sayfalama</span><span class="sxs-lookup"><span data-stu-id="be7b2-102">Paging Through a Query Result</span></span>
<span data-ttu-id="be7b2-103">Sorgu sonucu ile sayfalama, bir sorgunun sonuçlarını, verilerin veya sayfaların küçük alt kümelerine döndürme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="be7b2-103">Paging through a query result is the process of returning the results of a query in smaller subsets of data, or pages.</span></span> <span data-ttu-id="be7b2-104">Bu, sonuçları küçük ve kolay Yönetilecek öbeklerde bir kullanıcıya görüntülemek için yaygın bir uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="be7b2-104">This is a common practice for displaying results to a user in small, easy-to-manage chunks.</span></span>  
  
 <span data-ttu-id="be7b2-105">**DataAdapter** , **Fill** yönteminin aşırı yüklemeleri aracılığıyla yalnızca bir veri sayfası döndürmek için bir özellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="be7b2-105">The **DataAdapter** provides a facility for returning only a page of data, through overloads of the **Fill** method.</span></span> <span data-ttu-id="be7b2-106">Ancak, bu, büyük sorgu sonuçları aracılığıyla disk belleği için en iyi seçim olmayabilir çünkü **DataAdapter** , hedefi <xref:System.Data.DataTable> ya <xref:System.Data.DataSet> da yalnızca istenen kayıtlarla doldurmakla birlikte, tüm sorguyu döndürecek kaynaklar hala kullanılmaktadır .</span><span class="sxs-lookup"><span data-stu-id="be7b2-106">However, this might not be the best choice for paging through large query results because, although the **DataAdapter** fills the target <xref:System.Data.DataTable> or <xref:System.Data.DataSet> with only the requested records, the resources to return the entire query are still used.</span></span> <span data-ttu-id="be7b2-107">Tüm sorguyu döndürmek için kaynakları kullanmadan bir veri kaynağından veri sayfası döndürmek için, sorgunuz için yalnızca gerekli olanlarla döndürülen satırları azaltan ek ölçütler belirtin.</span><span class="sxs-lookup"><span data-stu-id="be7b2-107">To return a page of data from a data source without using the resources to return the entire query, specify additional criteria for your query that reduce the rows returned to only those required.</span></span>  
  
 <span data-ttu-id="be7b2-108">Bir veri sayfası döndürmek için **Fill** metodunu kullanmak için, veri sayfasındaki ilk kayıt Için bir **startRecord** parametresi ve veri sayfasındaki kayıt sayısı için de **MaxRecords** parametresi belirtin.</span><span class="sxs-lookup"><span data-stu-id="be7b2-108">To use the **Fill** method to return a page of data, specify a **startRecord** parameter, for the first record in the page of data, and a **maxRecords** parameter, for the number of records in the page of data.</span></span>  
  
 <span data-ttu-id="be7b2-109">Aşağıdaki kod örneği, sayfa boyutunun beş kayıt olduğu bir sorgu sonucunun ilk sayfasını döndürmek için **Fill** yönteminin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="be7b2-109">The following code example shows how to use the **Fill** method to return the first page of a query result where the page size is five records.</span></span>  
  
```vb  
Dim currentIndex As Integer = 0  
Dim pageSize As Integer = 5  
  
Dim orderSQL As String = "SELECT * FROM dbo.Orders ORDER BY OrderID"  
' Assumes that connection is a valid SqlConnection object.  
Dim adapter As SqlDataAdapter = _  
  New SqlDataAdapter(orderSQL, connection)  
  
Dim dataSet As DataSet = New DataSet()  
adapter.Fill(dataSet, currentIndex, pageSize, "Orders")  
```  
  
```csharp  
int currentIndex = 0;  
int pageSize = 5;  
  
string orderSQL = "SELECT * FROM Orders ORDER BY OrderID";  
// Assumes that connection is a valid SqlConnection object.  
SqlDataAdapter adapter = new SqlDataAdapter(orderSQL, connection);  
  
DataSet dataSet = new DataSet();  
adapter.Fill(dataSet, currentIndex, pageSize, "Orders");  
```  
  
 <span data-ttu-id="be7b2-110">Önceki örnekte, **DataSet** yalnızca beş kayıtla doldurulmuştur, ancak tüm **Orders** tablosu döndürülür.</span><span class="sxs-lookup"><span data-stu-id="be7b2-110">In the previous example, the **DataSet** is only filled with five records, but the entire **Orders** table is returned.</span></span> <span data-ttu-id="be7b2-111">**Veri kümesini** aynı beş kayıtla doldurmanız, ancak yalnızca beş kayıt döndürmek için, aşağıdaki kod örneğinde olduğu gibi SQL DEYIMINIZDE top ve WHERE yan tümcelerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="be7b2-111">To fill the **DataSet** with those same five records, but only return five records, use the TOP and WHERE clauses in your SQL statement, as in the following code example.</span></span>  
  
```vb  
Dim pageSize As Integer = 5  
  
Dim orderSQL As String = "SELECT TOP " & pageSize & _  
  " * FROM Orders ORDER BY OrderID"  
Dim adapter As SqlDataAdapter = _  
  New SqlDataAdapter(orderSQL, connection)  
  
Dim dataSet As DataSet = New DataSet()  
adapter.Fill(dataSet, "Orders")   
```  
  
```csharp  
int pageSize = 5;  
  
string orderSQL = "SELECT TOP " + pageSize +   
  " * FROM Orders ORDER BY OrderID";  
SqlDataAdapter adapter = new SqlDataAdapter(orderSQL, connection);  
  
DataSet dataSet = new DataSet();  
adapter.Fill(dataSet, "Orders");  
```  
  
 <span data-ttu-id="be7b2-112">Sorgu ile disk belleği bu şekilde sonuçlanırsa, aşağıdaki kod örneğinde gösterildiği gibi, bir sonraki kayıt sayfasını döndürmek için özel KIMLIĞI komuta geçirmek üzere satırları sipariş eden benzersiz tanımlayıcıyı korumanız gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="be7b2-112">Note that, when paging through the query results in this way, you must preserve the unique identifier that orders the rows, in order to pass the unique ID to the command to return the next page of records, as shown in the following code example.</span></span>  
  
```vb  
Dim lastRecord As String = _  
  dataSet.Tables("Orders").Rows(pageSize - 1)("OrderID").ToString()  
```  
  
```csharp  
string lastRecord =   
  dataSet.Tables["Orders"].Rows[pageSize - 1]["OrderID"].ToString();  
```  
  
 <span data-ttu-id="be7b2-113">**StartRecord** ve **MaxRecords** parametrelerini alan **Fill** yönteminin aşırı yüklemesini kullanarak bir sonraki kayıt sayfasını döndürmek için, geçerli kayıt dizinini sayfa boyutuna göre artırın ve tabloyu girin.</span><span class="sxs-lookup"><span data-stu-id="be7b2-113">To return the next page of records using the overload of the **Fill** method that takes the **startRecord** and **maxRecords** parameters, increment the current record index by the page size and fill the table.</span></span> <span data-ttu-id="be7b2-114">**Veri kümesine**yalnızca bir kayıt sayfası eklense bile, veritabanı sunucusunun tüm sorgu sonuçlarını döndürdüğünü unutmayın.</span><span class="sxs-lookup"><span data-stu-id="be7b2-114">Remember that the database server returns the entire query results even though only one page of records is added to the **DataSet**.</span></span> <span data-ttu-id="be7b2-115">Aşağıdaki kod örneğinde, tablo satırları sonraki veri sayfasıyla doldurulmadan önce temizlenir.</span><span class="sxs-lookup"><span data-stu-id="be7b2-115">In the following code example, the table rows are cleared before they are filled with the next page of data.</span></span> <span data-ttu-id="be7b2-116">Veritabanı sunucusuna yapılan gelişleri azaltmak için bir yerel önbellekte belirli sayıda döndürülen satırı korumak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="be7b2-116">You might want to preserve a certain number of returned rows in a local cache to reduce trips to the database server.</span></span>  
  
```vb  
currentIndex = currentIndex + pageSize  
  
dataSet.Tables("Orders").Rows.Clear()  
  
adapter.Fill(dataSet, currentIndex, pageSize, "Orders")  
```  
  
```csharp  
currentIndex += pageSize;  
  
dataSet.Tables["Orders"].Rows.Clear();  
  
adapter.Fill(dataSet, currentIndex, pageSize, "Orders");  
```  
  
 <span data-ttu-id="be7b2-117">Veritabanı sunucusunun tüm sorguyu döndürmesi gerekmeden sonraki kayıt sayfasını döndürmek için, SELECT ifadesiyle sınırlayıcı kriterleri belirtin.</span><span class="sxs-lookup"><span data-stu-id="be7b2-117">To return the next page of records without having the database server return the entire query, specify restrictive criteria to the SELECT statement.</span></span> <span data-ttu-id="be7b2-118">Yukarıdaki örnek döndürülen son kaydı korunduğu için, aşağıdaki kod örneğinde gösterildiği gibi, sorgu için bir başlangıç noktası belirtmek üzere WHERE yan tümcesinde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="be7b2-118">Because the preceding example preserved the last record returned, you can use it in the WHERE clause to specify a starting point for the query, as shown in the following code example.</span></span>  
  
```vb  
orderSQL = "SELECT TOP " & pageSize & _  
  " * FROM Orders WHERE OrderID > " & lastRecord & " ORDER BY OrderID"  
adapter.SelectCommand.CommandText = orderSQL  
  
dataSet.Tables("Orders").Rows.Clear()  
  
adapter.Fill(dataSet, "Orders")  
```  
  
```csharp  
orderSQL = "SELECT TOP " + pageSize +   
  " * FROM Orders WHERE OrderID > " + lastRecord + " ORDER BY OrderID";  
adapter.SelectCommand.CommandText = orderSQL;  
  
dataSet.Tables["Orders"].Rows.Clear();  
  
adapter.Fill(dataSet, "Orders");  
```  
  
## <a name="see-also"></a><span data-ttu-id="be7b2-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="be7b2-119">See also</span></span>

- [<span data-ttu-id="be7b2-120">DataAdapters ve DataReaders</span><span class="sxs-lookup"><span data-stu-id="be7b2-120">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="be7b2-121">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="be7b2-121">ADO.NET Overview</span></span>](ado-net-overview.md)
