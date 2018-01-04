---
title: "Satırları bulma"
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
ms.assetid: 5da300e2-74c0-4d13-9202-fc20ed8212d8
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: e9ede2dbf0718a4ca1d8025af3ce60c256afc867
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="finding-rows"></a><span data-ttu-id="ed7ef-102">Satırları bulma</span><span class="sxs-lookup"><span data-stu-id="ed7ef-102">Finding Rows</span></span>
<span data-ttu-id="ed7ef-103">Satırları sıralama anahtar değerlerine göre kullanarak arayabilirsiniz <xref:System.Data.DataView.Find%2A> ve <xref:System.Data.DataView.FindRows%2A> yöntemlerini <xref:System.Data.DataView>.</span><span class="sxs-lookup"><span data-stu-id="ed7ef-103">You can search for rows according to their sort key values by using the <xref:System.Data.DataView.Find%2A> and <xref:System.Data.DataView.FindRows%2A> methods of the <xref:System.Data.DataView>.</span></span> <span data-ttu-id="ed7ef-104">Arama büyük/küçük harfe duyarlılık değeri **Bul** ve **FindRows** yöntemleri tarafından belirlenir **CaseSensitive** temel özellik <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="ed7ef-104">The case sensitivity of search values in the **Find** and **FindRows** methods is determined by the **CaseSensitive** property of the underlying <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="ed7ef-105">Arama değerleri bir sonuç dönebilmek için var olan sıralama anahtarı değerleri tamamen eşleşmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="ed7ef-105">Search values must match existing sort key values in their entirety in order to return a result.</span></span>  
  
 <span data-ttu-id="ed7ef-106">**Bul** yöntemi dizini bir tamsayı döndürür <xref:System.Data.DataRowView> arama ölçütleriyle eşleşen.</span><span class="sxs-lookup"><span data-stu-id="ed7ef-106">The **Find** method returns an integer with the index of the <xref:System.Data.DataRowView> that matches the search criteria.</span></span> <span data-ttu-id="ed7ef-107">Birden fazla satır, yalnızca ilk eşleşen dizini arama ölçütleri eşleşirse **DataRowView** döndürülür.</span><span class="sxs-lookup"><span data-stu-id="ed7ef-107">If more than one row matches the search criteria, only the index of the first matching **DataRowView** is returned.</span></span> <span data-ttu-id="ed7ef-108">Herhangi bir eşleşme bulunmazsa, **Bul** -1 döndürür.</span><span class="sxs-lookup"><span data-stu-id="ed7ef-108">If no matches are found, **Find** returns -1.</span></span>  
  
 <span data-ttu-id="ed7ef-109">Birden çok satır ile arama sonuçları döndürmek için kullanın **FindRows** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ed7ef-109">To return search results that match multiple rows, use the **FindRows** method.</span></span> <span data-ttu-id="ed7ef-110">**FindRows** works olduğu gibi **Bul** şekilde döndürür dışında yöntemi, bir **DataRowView** tüm eşleşen satırları başvuran dizi **DataView**.</span><span class="sxs-lookup"><span data-stu-id="ed7ef-110">**FindRows** works just like the **Find** method, except that it returns a **DataRowView** array that references all matching rows in the **DataView**.</span></span> <span data-ttu-id="ed7ef-111">Herhangi bir eşleşme bulunmazsa, **DataRowView** dizi boş olacaktır.</span><span class="sxs-lookup"><span data-stu-id="ed7ef-111">If no matches are found, the **DataRowView** array will be empty.</span></span>  
  
 <span data-ttu-id="ed7ef-112">Kullanılacak **Bul** veya **FindRows** sıralama belirtmelisiniz yöntemleri ayarlayarak ya da sipariş **ApplyDefaultSort** için **true** veya kullanarak **Sıralama** özelliği.</span><span class="sxs-lookup"><span data-stu-id="ed7ef-112">To use the **Find** or **FindRows** methods you must specify a sort order either by setting **ApplyDefaultSort** to **true** or by using the **Sort** property.</span></span> <span data-ttu-id="ed7ef-113">Sıralama düzeni belirtilirse, özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="ed7ef-113">If no sort order is specified, an exception is thrown.</span></span>  
  
 <span data-ttu-id="ed7ef-114">**Bul** ve **FindRows** yöntemleri uzunluğunu eşleşen sıralama düzeni sütun sayısını giriş olarak bir dizi değere alın.</span><span class="sxs-lookup"><span data-stu-id="ed7ef-114">The **Find** and **FindRows** methods take an array of values as input whose length matches the number of columns in the sort order.</span></span> <span data-ttu-id="ed7ef-115">Tek bir sütun üzerinde sıralama söz konusu olduğunda, tek bir değer geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ed7ef-115">In the case of a sort on a single column, you can pass a single value.</span></span> <span data-ttu-id="ed7ef-116">Birden çok sütun içeren sıralama düzenleri için nesnelerinin bir dizisi geçirin.</span><span class="sxs-lookup"><span data-stu-id="ed7ef-116">For sort orders containing multiple columns, you pass an array of objects.</span></span> <span data-ttu-id="ed7ef-117">Birden çok sütun sıralama için belirtilen sütunların sırasını nesne dizideki eşleşmesi gerektiğini unutmayın **sıralama** özelliği **DataView**.</span><span class="sxs-lookup"><span data-stu-id="ed7ef-117">Note that for a sort on multiple columns, the values in the object array must match the order of the columns specified in the **Sort** property of the **DataView**.</span></span>  
  
 <span data-ttu-id="ed7ef-118">Aşağıdaki örnekte gösterildiği kod **Bul** karşı çağrılan yöntemi bir **DataView** bir tek sütun sıralama ile.</span><span class="sxs-lookup"><span data-stu-id="ed7ef-118">The following code example shows the **Find** method being called against a **DataView** with a single column sort order.</span></span>  
  
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
  
 <span data-ttu-id="ed7ef-119">Varsa, **sıralama** özelliği, birden çok sütun belirtir, tarafından belirtilen sırada bir nesne dizisinin her sütun için arama değerlerle geçmelidir **sıralama** özelliği, aşağıdaki kod örneğinde olduğu gibi.</span><span class="sxs-lookup"><span data-stu-id="ed7ef-119">If your **Sort** property specifies multiple columns, you must pass an object array with the search values for each column in the order specified by the **Sort** property, as in the following code example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ed7ef-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ed7ef-120">See Also</span></span>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataView>  
 [<span data-ttu-id="ed7ef-121">DataViews</span><span class="sxs-lookup"><span data-stu-id="ed7ef-121">DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [<span data-ttu-id="ed7ef-122">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="ed7ef-122">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
