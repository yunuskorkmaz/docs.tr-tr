---
title: Satırları Bulma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5da300e2-74c0-4d13-9202-fc20ed8212d8
ms.openlocfilehash: cfd4587f0dde7687ecf88bf6b31c44b90a2287ca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151149"
---
# <a name="finding-rows"></a><span data-ttu-id="0f0c0-102">Satırları Bulma</span><span class="sxs-lookup"><span data-stu-id="0f0c0-102">Finding Rows</span></span>
<span data-ttu-id="0f0c0-103">Satırları sıralama anahtar değerlerine göre, <xref:System.Data.DataView.Find%2A> <xref:System.Data.DataView.FindRows%2A> <xref:System.Data.DataView>'nin yöntemlerini ve yöntemlerini kullanarak arayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0f0c0-103">You can search for rows according to their sort key values by using the <xref:System.Data.DataView.Find%2A> and <xref:System.Data.DataView.FindRows%2A> methods of the <xref:System.Data.DataView>.</span></span> <span data-ttu-id="0f0c0-104">**Find** ve **FindRows** yöntemlerindeki arama değerlerinin durum duyarlılığı, altta yatan <xref:System.Data.DataTable> **CaseSensitive** özelliği tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="0f0c0-104">The case sensitivity of search values in the **Find** and **FindRows** methods is determined by the **CaseSensitive** property of the underlying <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="0f0c0-105">Arama değerleri, bir sonucu döndürmek için varolan anahtar değerleri tam olarak eşleştirmelidir.</span><span class="sxs-lookup"><span data-stu-id="0f0c0-105">Search values must match existing sort key values in their entirety in order to return a result.</span></span>  
  
 <span data-ttu-id="0f0c0-106">**Bul** yöntemi, arama ölçütleriyle <xref:System.Data.DataRowView> eşleşen dizinin isini içeren bir arayıcı döndürür.</span><span class="sxs-lookup"><span data-stu-id="0f0c0-106">The **Find** method returns an integer with the index of the <xref:System.Data.DataRowView> that matches the search criteria.</span></span> <span data-ttu-id="0f0c0-107">Birden fazla satır arama ölçütleriyle eşleşirse, yalnızca ilk eşleşen **DataRowView** dizini döndürülür.</span><span class="sxs-lookup"><span data-stu-id="0f0c0-107">If more than one row matches the search criteria, only the index of the first matching **DataRowView** is returned.</span></span> <span data-ttu-id="0f0c0-108">Eşleşme bulunmazsa, **Find** -1 döndürür bulun.</span><span class="sxs-lookup"><span data-stu-id="0f0c0-108">If no matches are found, **Find** returns -1.</span></span>  
  
 <span data-ttu-id="0f0c0-109">Birden çok satırla eşleşen arama sonuçlarını döndürmek için **FindRows** yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="0f0c0-109">To return search results that match multiple rows, use the **FindRows** method.</span></span> <span data-ttu-id="0f0c0-110">**FindRows,** **DataView'daki**tüm eşleşen satırlara başvuran bir **DataRowView** dizisini döndürmesi dışında, **Bul** yöntemi gibi çalışır.</span><span class="sxs-lookup"><span data-stu-id="0f0c0-110">**FindRows** works just like the **Find** method, except that it returns a **DataRowView** array that references all matching rows in the **DataView**.</span></span> <span data-ttu-id="0f0c0-111">Eşler bulunmazsa, **DataRowView** dizisi boş olur.</span><span class="sxs-lookup"><span data-stu-id="0f0c0-111">If no matches are found, the **DataRowView** array will be empty.</span></span>  
  
 <span data-ttu-id="0f0c0-112">**Find** or **FindRows** yöntemlerini kullanmak **için, ApplyDefaultSort'u** **doğru** olarak ayarlayarak veya **Sıralama** özelliğini kullanarak bir sıralama sırası belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="0f0c0-112">To use the **Find** or **FindRows** methods you must specify a sort order either by setting **ApplyDefaultSort** to **true** or by using the **Sort** property.</span></span> <span data-ttu-id="0f0c0-113">Sıralama sırası belirtilmemişse, bir özel durum atılır.</span><span class="sxs-lookup"><span data-stu-id="0f0c0-113">If no sort order is specified, an exception is thrown.</span></span>  
  
 <span data-ttu-id="0f0c0-114">**Find** and **FindRows** yöntemleri, uzunlukları sıralama sırasındaki sütun sayısıyla eşleşen giriş olarak bir dizi değer alır.</span><span class="sxs-lookup"><span data-stu-id="0f0c0-114">The **Find** and **FindRows** methods take an array of values as input whose length matches the number of columns in the sort order.</span></span> <span data-ttu-id="0f0c0-115">Tek bir sütunda bir sıralama durumunda, tek bir değer geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0f0c0-115">In the case of a sort on a single column, you can pass a single value.</span></span> <span data-ttu-id="0f0c0-116">Birden çok sütun içeren sıralama siparişleri için, bir dizi nesne geçersiniz.</span><span class="sxs-lookup"><span data-stu-id="0f0c0-116">For sort orders containing multiple columns, you pass an array of objects.</span></span> <span data-ttu-id="0f0c0-117">Birden çok sütundaki sıralama için nesne dizisindeki değerlerin **DataView'ın** **Sıralama** özelliğinde belirtilen sütunların sırasına uyması gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="0f0c0-117">Note that for a sort on multiple columns, the values in the object array must match the order of the columns specified in the **Sort** property of the **DataView**.</span></span>  
  
 <span data-ttu-id="0f0c0-118">Aşağıdaki kod örneği, tek bir sütun sıralama sırasına sahip bir **DataView'a** karşı çağrılan **Bul** yöntemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="0f0c0-118">The following code example shows the **Find** method being called against a **DataView** with a single column sort order.</span></span>  
  
```vb  
Dim custView As DataView = _  
  New DataView(custDS.Tables("Customers"), "", _  
  "CompanyName", DataViewRowState.CurrentRows)  
  
Dim rowIndex As Integer = custView.Find("The Cracker Box")  
  
If rowIndex = -1 Then  
  Console.WriteLine("No match found.")  
Else  
  Console.WriteLine("{0}, {1}", _  
    custView(rowIndex)("CustomerID").ToString(), _  
    custView(rowIndex)("CompanyName").ToString())  
End If  
```  
  
```csharp  
DataView custView = new DataView(custDS.Tables["Customers"], "",
  "CompanyName", DataViewRowState.CurrentRows);  
  
int rowIndex = custView.Find("The Cracker Box");  
  
if (rowIndex == -1)  
  Console.WriteLine("No match found.");  
else  
  Console.WriteLine("{0}, {1}",  
    custView[rowIndex]["CustomerID"].ToString(),  
    custView[rowIndex]["CompanyName"].ToString());  
```  
  
 <span data-ttu-id="0f0c0-119">**Sıralama** özelliğiniz birden çok sütun belirtse, aşağıdaki kod örneğinde olduğu gibi **Sıralama** özelliği tarafından belirtilen sırada her sütun için arama değerlerini içeren bir nesne dizisini geçmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="0f0c0-119">If your **Sort** property specifies multiple columns, you must pass an object array with the search values for each column in the order specified by the **Sort** property, as in the following code example.</span></span>  
  
```vb  
Dim custView As DataView = _  
  New DataView(custDS.Tables("Customers"), "", _  
  "CompanyName, ContactName", _  
  DataViewRowState.CurrentRows)  
  
Dim foundRows() As DataRowView = _  
  custView.FindRows(New object() {"The Cracker Box", "Liu Wong"})  
  
If foundRows.Length = 0 Then  
  Console.WriteLine("No match found.")  
Else  
  Dim myDRV As DataRowView  
  For Each myDRV In foundRows  
    Console.WriteLine("{0}, {1}", _  
      myDRV("CompanyName").ToString(), myDRV("ContactName").ToString())  
  Next  
End If  
```  
  
```csharp  
DataView custView = new DataView(custDS.Tables["Customers"], "",  
  "CompanyName, ContactName",  
  DataViewRowState.CurrentRows);  
  
DataRowView[] foundRows =
  custView.FindRows(new object[] {"The Cracker Box", "Liu Wong"});  
  
if (foundRows.Length == 0)  
  Console.WriteLine("No match found.");  
else  
  foreach (DataRowView myDRV in foundRows)  
    Console.WriteLine("{0}, {1}", myDRV["CompanyName"].ToString(),
      myDRV["ContactName"].ToString());  
```  
  
## <a name="see-also"></a><span data-ttu-id="0f0c0-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0f0c0-120">See also</span></span>

- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- [<span data-ttu-id="0f0c0-121">DataViews</span><span class="sxs-lookup"><span data-stu-id="0f0c0-121">DataViews</span></span>](dataviews.md)
- [<span data-ttu-id="0f0c0-122">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="0f0c0-122">ADO.NET Overview</span></span>](../ado-net-overview.md)
