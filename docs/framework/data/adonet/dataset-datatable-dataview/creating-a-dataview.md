---
description: 'Daha fazla bilgi edinin: DataView oluşturma'
title: DataView Oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b1cc02d1-23b1-4439-a998-0da1899f3442
ms.openlocfilehash: e9614e7ee9aae58c4dc57f856a959bd3624dac03
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725031"
---
# <a name="creating-a-dataview"></a><span data-ttu-id="97a53-103">DataView Oluşturma</span><span class="sxs-lookup"><span data-stu-id="97a53-103">Creating a DataView</span></span>

<span data-ttu-id="97a53-104">Oluşturmak için iki yol vardır <xref:System.Data.DataView> .</span><span class="sxs-lookup"><span data-stu-id="97a53-104">There are two ways to create a <xref:System.Data.DataView>.</span></span> <span data-ttu-id="97a53-105">**DataView** oluşturucusunu kullanabilir veya özelliğine bir başvuru oluşturabilirsiniz <xref:System.Data.DataTable.DefaultView%2A> <xref:System.Data.DataTable> .</span><span class="sxs-lookup"><span data-stu-id="97a53-105">You can use the **DataView** constructor, or you can create a reference to the <xref:System.Data.DataTable.DefaultView%2A> property of the <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="97a53-106">**DataView** Oluşturucusu boş olabilir veya tek bir bağımsız değişken olarak bir **DataTable** ya da filtre ölçütü, sıralama ölçütü ve bir satır durumu **filtresiyle birlikte bir DataTable alabilir** .</span><span class="sxs-lookup"><span data-stu-id="97a53-106">The **DataView** constructor can be empty, or it can take either a **DataTable** as a single argument, or a **DataTable** along with filter criteria, sort criteria, and a row state filter.</span></span> <span data-ttu-id="97a53-107">**DataView** ile kullanılabilecek ek bağımsız değişkenler hakkında daha fazla bilgi için bkz. [verileri sıralama ve filtreleme](sorting-and-filtering-data.md).</span><span class="sxs-lookup"><span data-stu-id="97a53-107">For more information about the additional arguments available for use with the **DataView**, see [Sorting and Filtering Data](sorting-and-filtering-data.md).</span></span>  
  
 <span data-ttu-id="97a53-108">**DataView dizini** her Ikisi de **DataView** oluşturulduğunda oluşturulduğundan ve **sıralama**, **RowFilter** veya **RowStateFilter** özelliklerinin herhangi biri değiştirildiğinde, **DataView** oluştururken Oluşturucu bağımsız değişken olarak herhangi bir ilk sıralama düzeni veya filtreleme ölçütü sağlayarak en iyi performansı elde edersiniz.</span><span class="sxs-lookup"><span data-stu-id="97a53-108">Because the index for a **DataView** is built both when the **DataView** is created, and when any of the **Sort**, **RowFilter**, or **RowStateFilter** properties are modified, you achieve best performance by supplying any initial sort order or filtering criteria as constructor arguments when you create the **DataView**.</span></span> <span data-ttu-id="97a53-109">Sort veya Filter ölçütlerini belirtmeden bir **DataView** oluşturma, sonra **sıralama**, **RowFilter** veya **RowStateFilter** özelliklerini ayarlama, dizinin en az iki kez oluşturulmasına neden olur: **DataView** oluşturulduğunda ve sıralama ya da filtre özelliklerinden herhangi biri değiştirildiğinde yeniden.</span><span class="sxs-lookup"><span data-stu-id="97a53-109">Creating a **DataView** without specifying sort or filter criteria and then setting the **Sort**, **RowFilter**, or **RowStateFilter** properties later causes the index to be built at least twice: once when the **DataView** is created, and again when any of the sort or filter properties are modified.</span></span>  
  
 <span data-ttu-id="97a53-110">Herhangi bir bağımsız değişken kullanmayan oluşturucuyu kullanarak bir **DataView** oluşturursanız, **tablo** özelliği ayarlanana kadar **DataView** 'ı kullanabileceksiniz.</span><span class="sxs-lookup"><span data-stu-id="97a53-110">Note that if you create a **DataView** using the constructor that does not take any arguments, you will not be able to use the **DataView** until you have set the **Table** property.</span></span>  
  
 <span data-ttu-id="97a53-111">Aşağıdaki kod örneği, **DataView** oluşturucuyu kullanarak bir **DataView** oluşturmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="97a53-111">The following code example demonstrates how to create a **DataView** using the **DataView** constructor.</span></span> <span data-ttu-id="97a53-112">**DataTable** Ile birlikte **RowFilter**, **Sort** sütunu ve **DataViewRowState** sağlanır.</span><span class="sxs-lookup"><span data-stu-id="97a53-112">A **RowFilter**, **Sort** column, and **DataViewRowState** are supplied along with the **DataTable**.</span></span>  
  
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
  
 <span data-ttu-id="97a53-113">Aşağıdaki kod örneği, tablosunun **DefaultView** özelliğini kullanarak bir **DataTable** 'ın varsayılan **DataView** öğesine nasıl başvuru alınacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="97a53-113">The following code example demonstrates how to obtain a reference to the default **DataView** of a **DataTable** using the **DefaultView** property of the table.</span></span>  
  
```vb  
Dim custDV As DataView = custDS.Tables("Customers").DefaultView  
```  
  
```csharp  
DataView custDV = custDS.Tables["Customers"].DefaultView;  
```  
  
## <a name="see-also"></a><span data-ttu-id="97a53-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="97a53-114">See also</span></span>

- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- [<span data-ttu-id="97a53-115">DataViews</span><span class="sxs-lookup"><span data-stu-id="97a53-115">DataViews</span></span>](dataviews.md)
- [<span data-ttu-id="97a53-116">Verileri Sıralama ve Filtreleme</span><span class="sxs-lookup"><span data-stu-id="97a53-116">Sorting and Filtering Data</span></span>](sorting-and-filtering-data.md)
- [<span data-ttu-id="97a53-117">DataTables</span><span class="sxs-lookup"><span data-stu-id="97a53-117">DataTables</span></span>](datatables.md)
- [<span data-ttu-id="97a53-118">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="97a53-118">ADO.NET Overview</span></span>](../ado-net-overview.md)
