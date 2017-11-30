---
title: "Sorgu sonucu disk belleği"
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
ms.assetid: fa360c46-e5f8-411e-a711-46997771133d
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: b4a51eec840b74d04aaab97226191b2ed30d8826
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="paging-through-a-query-result"></a><span data-ttu-id="8ce42-102">Sorgu sonucu disk belleği</span><span class="sxs-lookup"><span data-stu-id="8ce42-102">Paging Through a Query Result</span></span>
<span data-ttu-id="8ce42-103">Disk belleği sorgu sonucu aracılığıyla veri veya sayfalarının daha küçük alt kümeler halinde bir sorgunun sonuçlarını döndürme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="8ce42-103">Paging through a query result is the process of returning the results of a query in smaller subsets of data, or pages.</span></span> <span data-ttu-id="8ce42-104">Bu küçük, yönetilmesi kolay öbekleri bir kullanıcıya sonuçları görüntülemek için yaygın bir uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="8ce42-104">This is a common practice for displaying results to a user in small, easy-to-manage chunks.</span></span>  
  
 <span data-ttu-id="8ce42-105">**DataAdapter** yalnızca bir sayfa aşırı aracılığıyla veri döndürmek için bir olanağı sağlar **doldurun** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8ce42-105">The **DataAdapter** provides a facility for returning only a page of data, through overloads of the **Fill** method.</span></span> <span data-ttu-id="8ce42-106">Ancak, bu büyük sorgu sonuçları olduğundan, disk belleği en iyi seçenek olmayabilir rağmen **DataAdapter** hedef doldurur <xref:System.Data.DataTable> veya <xref:System.Data.DataSet> kayıtlarla yalnızca istenen, geri dönmek için kaynaklar tüm sorgu hala kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8ce42-106">However, this might not be the best choice for paging through large query results because, although the **DataAdapter** fills the target <xref:System.Data.DataTable> or <xref:System.Data.DataSet> with only the requested records, the resources to return the entire query are still used.</span></span> <span data-ttu-id="8ce42-107">Tüm sorgu döndürülecek kaynakların kullanmadan bir veri kaynağından veri sayfasının dönmek için yalnızca bu gerekli döndürülen satır azaltan ek sorgunuzu ölçütleri belirtin.</span><span class="sxs-lookup"><span data-stu-id="8ce42-107">To return a page of data from a data source without using the resources to return the entire query, specify additional criteria for your query that reduce the rows returned to only those required.</span></span>  
  
 <span data-ttu-id="8ce42-108">Kullanılacak **doldurun** , verilerin bir sayfaya dönmek için yöntemi belirtin bir **startRecord** veri sayfasındaki ilk kaydı için parametre ve bir **maxRecords** parametre sayısı veri sayfasındaki kaydeder.</span><span class="sxs-lookup"><span data-stu-id="8ce42-108">To use the **Fill** method to return a page of data, specify a **startRecord** parameter, for the first record in the page of data, and a **maxRecords** parameter, for the number of records in the page of data.</span></span>  
  
 <span data-ttu-id="8ce42-109">Aşağıdaki kod örneğinde nasıl kullanılacağını gösterir **doldurun** sayfa boyutu beş kayıt olduğu bir sorgu sonucunun ilk sayfasına dönmek için yöntem.</span><span class="sxs-lookup"><span data-stu-id="8ce42-109">The following code example shows how to use the **Fill** method to return the first page of a query result where the page size is five records.</span></span>  
  
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
  
 <span data-ttu-id="8ce42-110">Önceki örnekte, **DataSet** yalnızca beş kaydeder, ancak tüm ile doldurulur **siparişleri** tablo döndürülür.</span><span class="sxs-lookup"><span data-stu-id="8ce42-110">In the previous example, the **DataSet** is only filled with five records, but the entire **Orders** table is returned.</span></span> <span data-ttu-id="8ce42-111">Doldurmak için **DataSet** aynı beş kayıtları, ancak yalnızca dönüş beş kayıt, üst kullanın ve aşağıdaki kod örneğinde olduğu gibi SQL deyimindeki WHERE yan tümcelerini.</span><span class="sxs-lookup"><span data-stu-id="8ce42-111">To fill the **DataSet** with those same five records, but only return five records, use the TOP and WHERE clauses in your SQL statement, as in the following code example.</span></span>  
  
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
  
 <span data-ttu-id="8ce42-112">Bu şekilde sorgu sonuçlarında üzerinden disk belleği, benzersiz kimliği kayıtlarının, sonraki sayfaya dönmek için komutu aşağıdaki kod örneğinde gösterildiği gibi geçirmek için satır siparişleri benzersiz tanımlayıcı korumak, unutmayın.</span><span class="sxs-lookup"><span data-stu-id="8ce42-112">Note that, when paging through the query results in this way, you must preserve the unique identifier that orders the rows, in order to pass the unique ID to the command to return the next page of records, as shown in the following code example.</span></span>  
  
```vb  
Dim lastRecord As String = _  
  dataSet.Tables("Orders").Rows(pageSize - 1)("OrderID").ToString()  
```  
  
```csharp  
string lastRecord =   
  dataSet.Tables["Orders"].Rows[pageSize - 1]["OrderID"].ToString();  
```  
  
 <span data-ttu-id="8ce42-113">Aşırı yüklemesini kullanarak kayıtların sonraki sayfaya dönmek için **doldurun** yönteminin alan **startRecord** ve **maxRecords** parametreleri, geçerli kayıt dizini tarafından Artır Sayfa boyutunu ve doldurma tablo.</span><span class="sxs-lookup"><span data-stu-id="8ce42-113">To return the next page of records using the overload of the **Fill** method that takes the **startRecord** and **maxRecords** parameters, increment the current record index by the page size and fill the table.</span></span> <span data-ttu-id="8ce42-114">Veritabanı sunucusu yalnızca bir sayfa kaydı eklenir olsa bile tüm sorgu sonuçlarını döndürür unutmayın **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="8ce42-114">Remember that the database server returns the entire query results even though only one page of records is added to the **DataSet**.</span></span> <span data-ttu-id="8ce42-115">Veri sonraki sayfa ile doldurulur önce aşağıdaki kod örneğinde tablo satırları temizlenir.</span><span class="sxs-lookup"><span data-stu-id="8ce42-115">In the following code example, the table rows are cleared before they are filled with the next page of data.</span></span> <span data-ttu-id="8ce42-116">Belirli bir veritabanı sunucusuna dönüşleri azaltmasını için yerel önbellekteki döndürülen satır sayısını korumak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ce42-116">You might want to preserve a certain number of returned rows in a local cache to reduce trips to the database server.</span></span>  
  
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
  
 <span data-ttu-id="8ce42-117">Tüm sorgu döndürme veritabanı sunucusu olmadan kayıtların sonraki sayfaya dönmek için SELECT deyimi kısıtlayıcı ölçütü belirtin.</span><span class="sxs-lookup"><span data-stu-id="8ce42-117">To return the next page of records without having the database server return the entire query, specify restrictive criteria to the SELECT statement.</span></span> <span data-ttu-id="8ce42-118">Önceki örnekte döndürülen son kaydı korunur olduğundan, WHERE yan tümcesinde sorgu için bir başlangıç noktası belirtmek için aşağıdaki kod örneğinde gösterildiği gibi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ce42-118">Because the preceding example preserved the last record returned, you can use it in the WHERE clause to specify a starting point for the query, as shown in the following code example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8ce42-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8ce42-119">See Also</span></span>  
 [<span data-ttu-id="8ce42-120">DataAdapters ve DataReader</span><span class="sxs-lookup"><span data-stu-id="8ce42-120">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="8ce42-121">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="8ce42-121">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
