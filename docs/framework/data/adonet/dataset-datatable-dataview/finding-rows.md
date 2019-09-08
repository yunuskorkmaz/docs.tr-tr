---
title: Satırları Bulma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5da300e2-74c0-4d13-9202-fc20ed8212d8
ms.openlocfilehash: ad10557a55b498fe004bff6ce89801e975e7138b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786324"
---
# <a name="finding-rows"></a><span data-ttu-id="56bef-102">Satırları Bulma</span><span class="sxs-lookup"><span data-stu-id="56bef-102">Finding Rows</span></span>
<span data-ttu-id="56bef-103"><xref:System.Data.DataView.Find%2A> Ve<xref:System.Data.DataView.FindRows%2A> yöntemlerini<xref:System.Data.DataView>kullanarak sıralama anahtarı değerlerine göre satırları arayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="56bef-103">You can search for rows according to their sort key values by using the <xref:System.Data.DataView.Find%2A> and <xref:System.Data.DataView.FindRows%2A> methods of the <xref:System.Data.DataView>.</span></span> <span data-ttu-id="56bef-104">**Find** ve **FindRows** metotlarındaki arama değerlerinin büyük/küçük harf duyarlılığı, temeldeki <xref:System.Data.DataTable>öğesinin **CaseSensitive** özelliğine göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="56bef-104">The case sensitivity of search values in the **Find** and **FindRows** methods is determined by the **CaseSensitive** property of the underlying <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="56bef-105">Bir sonuç döndürmek için, arama değerleri, mevcut sıralama anahtarı değerleriyle eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="56bef-105">Search values must match existing sort key values in their entirety in order to return a result.</span></span>  
  
 <span data-ttu-id="56bef-106">**Find** yöntemi, arama ölçütleriyle eşleşen öğesinin <xref:System.Data.DataRowView> diziniyle bir tamsayı döndürür.</span><span class="sxs-lookup"><span data-stu-id="56bef-106">The **Find** method returns an integer with the index of the <xref:System.Data.DataRowView> that matches the search criteria.</span></span> <span data-ttu-id="56bef-107">Arama ölçütleriyle eşleşen birden fazla satır varsa, yalnızca ilk eşleşen **DataRowView** 'ın dizini döndürülür.</span><span class="sxs-lookup"><span data-stu-id="56bef-107">If more than one row matches the search criteria, only the index of the first matching **DataRowView** is returned.</span></span> <span data-ttu-id="56bef-108">Eşleşme bulunmazsa, **bul** -1 döndürür.</span><span class="sxs-lookup"><span data-stu-id="56bef-108">If no matches are found, **Find** returns -1.</span></span>  
  
 <span data-ttu-id="56bef-109">Birden çok satırla eşleşen arama sonuçları döndürmek için **FindRows** yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="56bef-109">To return search results that match multiple rows, use the **FindRows** method.</span></span> <span data-ttu-id="56bef-110">**FindRows** , **Find** yöntemi gibi çalışarak, **DataView**Içindeki tüm eşleşen satırlara başvuran bir **DataRowView** dizisi döndürür.</span><span class="sxs-lookup"><span data-stu-id="56bef-110">**FindRows** works just like the **Find** method, except that it returns a **DataRowView** array that references all matching rows in the **DataView**.</span></span> <span data-ttu-id="56bef-111">Hiçbir eşleşme bulunmazsa, **DataRowView** dizisi boş olur.</span><span class="sxs-lookup"><span data-stu-id="56bef-111">If no matches are found, the **DataRowView** array will be empty.</span></span>  
  
 <span data-ttu-id="56bef-112">**Find** veya **FindRows** yöntemlerini kullanmak için, **ApplyDefaultSort** ' i **true** olarak ayarlayarak ya da **Sort** özelliğini kullanarak bir sıralama düzeni belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="56bef-112">To use the **Find** or **FindRows** methods you must specify a sort order either by setting **ApplyDefaultSort** to **true** or by using the **Sort** property.</span></span> <span data-ttu-id="56bef-113">Sıralama düzeni belirtilmemişse, bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="56bef-113">If no sort order is specified, an exception is thrown.</span></span>  
  
 <span data-ttu-id="56bef-114">**Find** ve **FindRows** yöntemleri, uzunluğu sıralama düzeninde olan sütun sayısıyla eşleşen girdi olarak bir dizi değer alır.</span><span class="sxs-lookup"><span data-stu-id="56bef-114">The **Find** and **FindRows** methods take an array of values as input whose length matches the number of columns in the sort order.</span></span> <span data-ttu-id="56bef-115">Tek bir sütunda sıralama söz konusu olduğunda tek bir değer geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="56bef-115">In the case of a sort on a single column, you can pass a single value.</span></span> <span data-ttu-id="56bef-116">Birden çok sütun içeren sıralama düzenleri için bir nesne dizisi geçirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="56bef-116">For sort orders containing multiple columns, you pass an array of objects.</span></span> <span data-ttu-id="56bef-117">Birden çok sütunda sıralama için, nesne dizisindeki değerlerin **DataView**'ın **Sort** özelliğinde belirtilen sütunların sırasıyla eşleşmesi gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="56bef-117">Note that for a sort on multiple columns, the values in the object array must match the order of the columns specified in the **Sort** property of the **DataView**.</span></span>  
  
 <span data-ttu-id="56bef-118">Aşağıdaki kod örneğinde, tek sütunlu sıralama düzeninde bir **DataView** Ile çağrılan **Find** yöntemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="56bef-118">The following code example shows the **Find** method being called against a **DataView** with a single column sort order.</span></span>  
  
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
  
 <span data-ttu-id="56bef-119">**Sıralama** özelliği birden çok sütun belirtiyorsa, her bir sütunun arama değerleriyle birlikte, aşağıdaki kod örneğinde olduğu gibi **sıralama** özelliği tarafından belirtilen sırada bir nesne dizisi geçirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="56bef-119">If your **Sort** property specifies multiple columns, you must pass an object array with the search values for each column in the order specified by the **Sort** property, as in the following code example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="56bef-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="56bef-120">See also</span></span>

- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- [<span data-ttu-id="56bef-121">DataViews</span><span class="sxs-lookup"><span data-stu-id="56bef-121">DataViews</span></span>](dataviews.md)
- [<span data-ttu-id="56bef-122">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="56bef-122">ADO.NET Overview</span></span>](../ado-net-overview.md)
