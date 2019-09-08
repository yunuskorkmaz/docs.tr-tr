---
title: DataView Oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b1cc02d1-23b1-4439-a998-0da1899f3442
ms.openlocfilehash: 3e1c31dac458594eee70ddd99469aca7cf63b848
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785482"
---
# <a name="creating-a-dataview"></a><span data-ttu-id="7ddfd-102">DataView Oluşturma</span><span class="sxs-lookup"><span data-stu-id="7ddfd-102">Creating a DataView</span></span>
<span data-ttu-id="7ddfd-103">Oluşturmak için iki yol vardır <xref:System.Data.DataView>.</span><span class="sxs-lookup"><span data-stu-id="7ddfd-103">There are two ways to create a <xref:System.Data.DataView>.</span></span> <span data-ttu-id="7ddfd-104">**DataView** oluşturucusunu kullanabilir veya <xref:System.Data.DataTable.DefaultView%2A> özelliğine <xref:System.Data.DataTable>bir başvuru oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7ddfd-104">You can use the **DataView** constructor, or you can create a reference to the <xref:System.Data.DataTable.DefaultView%2A> property of the <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="7ddfd-105">**DataView** Oluşturucusu boş olabilir veya tek bir bağımsız değişken olarak bir **DataTable** ya da filtre ölçütü, sıralama ölçütü ve bir satır durumu **filtresiyle birlikte bir DataTable alabilir** .</span><span class="sxs-lookup"><span data-stu-id="7ddfd-105">The **DataView** constructor can be empty, or it can take either a **DataTable** as a single argument, or a **DataTable** along with filter criteria, sort criteria, and a row state filter.</span></span> <span data-ttu-id="7ddfd-106">**DataView**ile kullanılabilecek ek bağımsız değişkenler hakkında daha fazla bilgi için bkz. [verileri sıralama ve filtreleme](sorting-and-filtering-data.md).</span><span class="sxs-lookup"><span data-stu-id="7ddfd-106">For more information about the additional arguments available for use with the **DataView**, see [Sorting and Filtering Data](sorting-and-filtering-data.md).</span></span>  
  
 <span data-ttu-id="7ddfd-107">**DataView dizini** her Ikisi de **DataView** oluşturulduğunda oluşturulduğundan ve **sıralama**, **RowFilter**veya **RowStateFilter** özelliklerinden herhangi biri değiştirildiğinde, herhangi bir başlangıç sağlayarak en iyi performansı elde edersiniz **DataView**oluştururken Oluşturucu bağımsız değişkenleri olarak sıralamayı veya filtreleme ölçütlerini sıralayın.</span><span class="sxs-lookup"><span data-stu-id="7ddfd-107">Because the index for a **DataView** is built both when the **DataView** is created, and when any of the **Sort**, **RowFilter**, or **RowStateFilter** properties are modified, you achieve best performance by supplying any initial sort order or filtering criteria as constructor arguments when you create the **DataView**.</span></span> <span data-ttu-id="7ddfd-108">Sıralama veya filtre ölçütlerini belirtmeden bir **DataView** oluşturma, sonra **sıralama**, **RowFilter**veya **RowStateFilter** özelliklerinin daha sonra ayarlanması dizinin en az iki kez oluşturulmasına neden olur: **DataView** olduğunda sıralama veya filtre özelliklerinden herhangi biri değiştirildiğinde, ve yeniden oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="7ddfd-108">Creating a **DataView** without specifying sort or filter criteria and then setting the **Sort**, **RowFilter**, or **RowStateFilter** properties later causes the index to be built at least twice: once when the **DataView** is created, and again when any of the sort or filter properties are modified.</span></span>  
  
 <span data-ttu-id="7ddfd-109">Herhangi bir bağımsız değişken kullanmayan oluşturucuyu kullanarak bir **DataView** oluşturursanız, **tablo** özelliği ayarlanana kadar **DataView** 'ı kullanabileceksiniz.</span><span class="sxs-lookup"><span data-stu-id="7ddfd-109">Note that if you create a **DataView** using the constructor that does not take any arguments, you will not be able to use the **DataView** until you have set the **Table** property.</span></span>  
  
 <span data-ttu-id="7ddfd-110">Aşağıdaki kod örneği, **DataView** oluşturucuyu kullanarak bir **DataView** oluşturmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="7ddfd-110">The following code example demonstrates how to create a **DataView** using the **DataView** constructor.</span></span> <span data-ttu-id="7ddfd-111">**DataTable**Ile birlikte **RowFilter**, **Sort** sütunu ve **DataViewRowState** sağlanır.</span><span class="sxs-lookup"><span data-stu-id="7ddfd-111">A **RowFilter**, **Sort** column, and **DataViewRowState** are supplied along with the **DataTable**.</span></span>  
  
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
  
 <span data-ttu-id="7ddfd-112">Aşağıdaki kod örneği, tablosunun **DefaultView** özelliğini kullanarak bir **DataTable** 'ın varsayılan **DataView** öğesine nasıl başvuru alınacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="7ddfd-112">The following code example demonstrates how to obtain a reference to the default **DataView** of a **DataTable** using the **DefaultView** property of the table.</span></span>  
  
```vb  
Dim custDV As DataView = custDS.Tables("Customers").DefaultView  
```  
  
```csharp  
DataView custDV = custDS.Tables["Customers"].DefaultView;  
```  
  
## <a name="see-also"></a><span data-ttu-id="7ddfd-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7ddfd-113">See also</span></span>

- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- [<span data-ttu-id="7ddfd-114">DataViews</span><span class="sxs-lookup"><span data-stu-id="7ddfd-114">DataViews</span></span>](dataviews.md)
- [<span data-ttu-id="7ddfd-115">Verileri Sıralama ve Filtreleme</span><span class="sxs-lookup"><span data-stu-id="7ddfd-115">Sorting and Filtering Data</span></span>](sorting-and-filtering-data.md)
- [<span data-ttu-id="7ddfd-116">DataTables</span><span class="sxs-lookup"><span data-stu-id="7ddfd-116">DataTables</span></span>](datatables.md)
- [<span data-ttu-id="7ddfd-117">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="7ddfd-117">ADO.NET Overview</span></span>](../ado-net-overview.md)
