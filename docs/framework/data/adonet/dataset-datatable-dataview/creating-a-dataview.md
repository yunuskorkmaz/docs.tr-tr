---
title: DataView Oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b1cc02d1-23b1-4439-a998-0da1899f3442
ms.openlocfilehash: 9d21b17068ff3ce5b0bd3990144383d7f9ded2f9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151344"
---
# <a name="creating-a-dataview"></a><span data-ttu-id="e1fb0-102">DataView Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e1fb0-102">Creating a DataView</span></span>
<span data-ttu-id="e1fb0-103">Bir <xref:System.Data.DataView>.</span><span class="sxs-lookup"><span data-stu-id="e1fb0-103">There are two ways to create a <xref:System.Data.DataView>.</span></span> <span data-ttu-id="e1fb0-104">DataView oluşturucuyu kullanabilir veya **'nin** özelliğine <xref:System.Data.DataTable.DefaultView%2A> bir başvuru <xref:System.Data.DataTable>oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e1fb0-104">You can use the **DataView** constructor, or you can create a reference to the <xref:System.Data.DataTable.DefaultView%2A> property of the <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="e1fb0-105">**DataView** oluşturucu boş olabilir veya filtre ölçütleri, sıralama ölçütleri ve satır durumu filtresiyle birlikte bir DataTable'ı tek bir bağımsız değişken olarak veya **DataTable'ı** alabilir. **DataTable**</span><span class="sxs-lookup"><span data-stu-id="e1fb0-105">The **DataView** constructor can be empty, or it can take either a **DataTable** as a single argument, or a **DataTable** along with filter criteria, sort criteria, and a row state filter.</span></span> <span data-ttu-id="e1fb0-106">**DataView**ile kullanılabilir ek bağımsız değişkenler hakkında daha fazla bilgi için [bkz.](sorting-and-filtering-data.md)</span><span class="sxs-lookup"><span data-stu-id="e1fb0-106">For more information about the additional arguments available for use with the **DataView**, see [Sorting and Filtering Data](sorting-and-filtering-data.md).</span></span>  
  
 <span data-ttu-id="e1fb0-107">**DataView** için dizin hem **DataView** oluşturulduğunda ve **Sıralama,** Satır Filtresi veya **RowStateFilter**özelliklerinden herhangi biri değiştirildiğinde, **DataView'ı**oluştururken herhangi bir ilk sıralama siparişi veya filtreleme ölçütlerini oluşturucu bağımsız değişkenler olarak sağlayarak en iyi performansı elde edeyim. **RowStateFilter**</span><span class="sxs-lookup"><span data-stu-id="e1fb0-107">Because the index for a **DataView** is built both when the **DataView** is created, and when any of the **Sort**, **RowFilter**, or **RowStateFilter** properties are modified, you achieve best performance by supplying any initial sort order or filtering criteria as constructor arguments when you create the **DataView**.</span></span> <span data-ttu-id="e1fb0-108">Sıralama veya filtre ölçütleri belirtmeden **bir DataView** oluşturma ve ardından **Sıralama,** **Satır Filtresi**veya **RowStateFilter** özelliklerini ayarlamak daha sonra dizinin en az iki kez oluşturulmasına neden olur: **DataView** oluşturulduğunda ve sıralama veya filtre özelliklerinden herhangi biri değiştirildiğinde tekrar.</span><span class="sxs-lookup"><span data-stu-id="e1fb0-108">Creating a **DataView** without specifying sort or filter criteria and then setting the **Sort**, **RowFilter**, or **RowStateFilter** properties later causes the index to be built at least twice: once when the **DataView** is created, and again when any of the sort or filter properties are modified.</span></span>  
  
 <span data-ttu-id="e1fb0-109">Herhangi bir bağımsız **değişken** kullanmayan bir Veri Görünümü oluşturursanız, **Tablo** özelliğini ayarlayana kadar **DataView'ı** kullanamadığınızı unutmayın.</span><span class="sxs-lookup"><span data-stu-id="e1fb0-109">Note that if you create a **DataView** using the constructor that does not take any arguments, you will not be able to use the **DataView** until you have set the **Table** property.</span></span>  
  
 <span data-ttu-id="e1fb0-110">Aşağıdaki kod örneği, **DataView** oluşturucuyu kullanarak bir **DataView'ın** nasıl oluşturulabildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="e1fb0-110">The following code example demonstrates how to create a **DataView** using the **DataView** constructor.</span></span> <span data-ttu-id="e1fb0-111">**Bir RowFilter**, **Sıralama** sütunu ve **DataViewRowState** **DataTable**ile birlikte sağlanır.</span><span class="sxs-lookup"><span data-stu-id="e1fb0-111">A **RowFilter**, **Sort** column, and **DataViewRowState** are supplied along with the **DataTable**.</span></span>  
  
```vb  
Dim custDV As DataView = New DataView(custDS.Tables("Customers"), _  
    "Country = 'USA'", _  
    "ContactName", _  
    DataViewRowState.CurrentRows)  
```  
  
```csharp  
DataView custDV = new DataView(custDS.Tables["Customers"],
    "Country = 'USA'",
    "ContactName",
    DataViewRowState.CurrentRows);  
```  
  
 <span data-ttu-id="e1fb0-112">Aşağıdaki kod örneği, tablonun **Varsayılan Görünümü** özelliğini kullanarak bir **DataTable'ın** varsayılan **DataTable Görünümü'ne** nasıl başvuru alınabildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="e1fb0-112">The following code example demonstrates how to obtain a reference to the default **DataView** of a **DataTable** using the **DefaultView** property of the table.</span></span>  
  
```vb  
Dim custDV As DataView = custDS.Tables("Customers").DefaultView  
```  
  
```csharp  
DataView custDV = custDS.Tables["Customers"].DefaultView;  
```  
  
## <a name="see-also"></a><span data-ttu-id="e1fb0-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e1fb0-113">See also</span></span>

- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- [<span data-ttu-id="e1fb0-114">DataViews</span><span class="sxs-lookup"><span data-stu-id="e1fb0-114">DataViews</span></span>](dataviews.md)
- [<span data-ttu-id="e1fb0-115">Verileri Sıralama ve Filtreleme</span><span class="sxs-lookup"><span data-stu-id="e1fb0-115">Sorting and Filtering Data</span></span>](sorting-and-filtering-data.md)
- [<span data-ttu-id="e1fb0-116">DataTables</span><span class="sxs-lookup"><span data-stu-id="e1fb0-116">DataTables</span></span>](datatables.md)
- [<span data-ttu-id="e1fb0-117">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e1fb0-117">ADO.NET Overview</span></span>](../ado-net-overview.md)
