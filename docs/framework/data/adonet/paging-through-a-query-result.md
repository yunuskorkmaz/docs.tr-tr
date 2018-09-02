---
title: Bir sorgu sonucunu sayfalama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fa360c46-e5f8-411e-a711-46997771133d
ms.openlocfilehash: 5d86095586af273f62980fcf8ddf10804b1cfa5a
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43406816"
---
# <a name="paging-through-a-query-result"></a><span data-ttu-id="5651e-102">Bir sorgu sonucunu sayfalama</span><span class="sxs-lookup"><span data-stu-id="5651e-102">Paging Through a Query Result</span></span>
<span data-ttu-id="5651e-103">Bir sorgu sonucunu sayfalama bir sorgunun sonuçlarını veri sayfaları ve daha küçük alt kümelerini döndürme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="5651e-103">Paging through a query result is the process of returning the results of a query in smaller subsets of data, or pages.</span></span> <span data-ttu-id="5651e-104">Bu, kolay yönetilmesi, küçük öbekler halinde bir kullanıcı için sonuçları görüntülemek için yaygın bir uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="5651e-104">This is a common practice for displaying results to a user in small, easy-to-manage chunks.</span></span>  
  
 <span data-ttu-id="5651e-105">**DataAdapter** verilerine aşırı yüklemeleri yalnızca bir sayfanın döndürmek için bir olanak sağlar. **dolgu** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5651e-105">The **DataAdapter** provides a facility for returning only a page of data, through overloads of the **Fill** method.</span></span> <span data-ttu-id="5651e-106">Ancak, bu büyük sorgu sonuçları için disk belleği için en iyi seçim olmayabilir ancak **DataAdapter** hedef doldurur <xref:System.Data.DataTable> veya <xref:System.Data.DataSet> yalnızca istenen kayıtları döndürmek için kaynaklar ile tüm sorgu yine de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5651e-106">However, this might not be the best choice for paging through large query results because, although the **DataAdapter** fills the target <xref:System.Data.DataTable> or <xref:System.Data.DataSet> with only the requested records, the resources to return the entire query are still used.</span></span> <span data-ttu-id="5651e-107">Tüm sorgu döndürülecek kaynakların kullanmadan bir veri kaynağından veri sayfasını döndürmek için yalnızca bu gerekli için döndürülen satırları Azalt sorgunuz için ek ölçüt belirtin.</span><span class="sxs-lookup"><span data-stu-id="5651e-107">To return a page of data from a data source without using the resources to return the entire query, specify additional criteria for your query that reduce the rows returned to only those required.</span></span>  
  
 <span data-ttu-id="5651e-108">Kullanmak için **doldurun** yöntemi, verilerin bir sayfaya dönmek için belirtin bir **startRecord** veri sayfasında ilk kayıt için bir parametre ve bir **maxRecords** sayısı parametresi kayıt sayfasında veri.</span><span class="sxs-lookup"><span data-stu-id="5651e-108">To use the **Fill** method to return a page of data, specify a **startRecord** parameter, for the first record in the page of data, and a **maxRecords** parameter, for the number of records in the page of data.</span></span>  
  
 <span data-ttu-id="5651e-109">Aşağıdaki kod örneği kullanma işlemini gösterir **dolgu** sayfa boyutunu beş kayıtların bulunduğu bir sorgu sonucunun ilk sayfaya dönmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5651e-109">The following code example shows how to use the **Fill** method to return the first page of a query result where the page size is five records.</span></span>  
  
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
  
 <span data-ttu-id="5651e-110">Önceki örnekte, **veri kümesi** yalnızca beş kaydeder, ancak tüm ile doldurulmuş **siparişler** tablo döndürülür.</span><span class="sxs-lookup"><span data-stu-id="5651e-110">In the previous example, the **DataSet** is only filled with five records, but the entire **Orders** table is returned.</span></span> <span data-ttu-id="5651e-111">Doldurmak için **veri kümesi** aynı beş kayıtları, ancak yalnızca dönüş beş kayıt, üst kullanın ve aşağıdaki kod örneğinde olduğu gibi SQL deyiminde WHERE yan tümcelerini.</span><span class="sxs-lookup"><span data-stu-id="5651e-111">To fill the **DataSet** with those same five records, but only return five records, use the TOP and WHERE clauses in your SQL statement, as in the following code example.</span></span>  
  
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
  
 <span data-ttu-id="5651e-112">Bu şekilde sorgu sonuçları aracılığıyla disk belleği, satırları benzersiz kimliği kayıtlarının, sonraki sayfaya dönmek için aşağıdaki kod örneğinde gösterildiği gibi Command'e için siparişleri benzersiz tanımlayıcısı korumak, unutmayın.</span><span class="sxs-lookup"><span data-stu-id="5651e-112">Note that, when paging through the query results in this way, you must preserve the unique identifier that orders the rows, in order to pass the unique ID to the command to return the next page of records, as shown in the following code example.</span></span>  
  
```vb  
Dim lastRecord As String = _  
  dataSet.Tables("Orders").Rows(pageSize - 1)("OrderID").ToString()  
```  
  
```csharp  
string lastRecord =   
  dataSet.Tables["Orders"].Rows[pageSize - 1]["OrderID"].ToString();  
```  
  
 <span data-ttu-id="5651e-113">Sonraki aşırı yüklemesini kullanarak kayıt sayfasına dönmek için **dolgu** gereken yöntemini **startRecord** ve **maxRecords** parametreleri geçerli kayıt dizine göre artırın Sayfa boyutunu ve doldurma tablo.</span><span class="sxs-lookup"><span data-stu-id="5651e-113">To return the next page of records using the overload of the **Fill** method that takes the **startRecord** and **maxRecords** parameters, increment the current record index by the page size and fill the table.</span></span> <span data-ttu-id="5651e-114">Veritabanı sunucusu yalnızca bir sayfa kaydı eklenir olsa bile tüm sorgu sonuçlarını döndürür unutmayın **veri kümesi**.</span><span class="sxs-lookup"><span data-stu-id="5651e-114">Remember that the database server returns the entire query results even though only one page of records is added to the **DataSet**.</span></span> <span data-ttu-id="5651e-115">Aşağıdaki kod örneğinde, veri sonraki sayfa ile doldurulmuş önce tablo satırları temizlenir.</span><span class="sxs-lookup"><span data-stu-id="5651e-115">In the following code example, the table rows are cleared before they are filled with the next page of data.</span></span> <span data-ttu-id="5651e-116">Belirli bir veritabanı sunucuya azaltmak için bir yerel önbellekteki döndürülen satır sayısını korumak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5651e-116">You might want to preserve a certain number of returned rows in a local cache to reduce trips to the database server.</span></span>  
  
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
  
 <span data-ttu-id="5651e-117">Veritabanı sunucusu tüm sorgu zorunda kalmadan kayıtları sonraki sayfasına dönmek için SELECT deyimi kısıtlayıcı ölçütü belirtin.</span><span class="sxs-lookup"><span data-stu-id="5651e-117">To return the next page of records without having the database server return the entire query, specify restrictive criteria to the SELECT statement.</span></span> <span data-ttu-id="5651e-118">Yukarıdaki örnekte, döndürülen en son kaydını korunur olduğundan, WHERE yan tümcesindeki sorgu için bir başlangıç noktası belirtmek için aşağıdaki kod örneğinde gösterildiği gibi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5651e-118">Because the preceding example preserved the last record returned, you can use it in the WHERE clause to specify a starting point for the query, as shown in the following code example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5651e-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5651e-119">See Also</span></span>  
 [<span data-ttu-id="5651e-120">DataAdapters ve DataReaders</span><span class="sxs-lookup"><span data-stu-id="5651e-120">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="5651e-121">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="5651e-121">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
