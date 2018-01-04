---
title: "DataView oluşturma"
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
ms.assetid: b1cc02d1-23b1-4439-a998-0da1899f3442
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 53cbfc5097c28c0677a164f817cfe14927814d75
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="creating-a-dataview"></a><span data-ttu-id="9b66f-102">DataView oluşturma</span><span class="sxs-lookup"><span data-stu-id="9b66f-102">Creating a DataView</span></span>
<span data-ttu-id="9b66f-103">Oluşturmanın iki yolu vardır bir <xref:System.Data.DataView>.</span><span class="sxs-lookup"><span data-stu-id="9b66f-103">There are two ways to create a <xref:System.Data.DataView>.</span></span> <span data-ttu-id="9b66f-104">Kullanabileceğiniz **DataView** Oluşturucusu veya bir başvuru oluşturabilirsiniz <xref:System.Data.DataTable.DefaultView%2A> özelliği <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="9b66f-104">You can use the **DataView** constructor, or you can create a reference to the <xref:System.Data.DataTable.DefaultView%2A> property of the <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="9b66f-105">**DataView** Oluşturucusu boş olabilir veya ya da alabilir bir **DataTable** tek bir bağımsız değişken olarak veya bir **DataTable** filtre ölçütü, sıralama ölçütü ve bir satır ile birlikte Durum Filtresi.</span><span class="sxs-lookup"><span data-stu-id="9b66f-105">The **DataView** constructor can be empty, or it can take either a **DataTable** as a single argument, or a **DataTable** along with filter criteria, sort criteria, and a row state filter.</span></span> <span data-ttu-id="9b66f-106">İle kullanılmak üzere kullanılabilir ek değişkenleri hakkında daha fazla bilgi için **DataView**, bkz: [sıralama ve filtreleme verilerini](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md).</span><span class="sxs-lookup"><span data-stu-id="9b66f-106">For more information about the additional arguments available for use with the **DataView**, see [Sorting and Filtering Data](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md).</span></span>  
  
 <span data-ttu-id="9b66f-107">Çünkü dizini bir **DataView** hem olduğunda yerleşik **DataView** oluşturulduğu ve herhangi biri seçildiğinde **sıralama**, **RowFilter**, veya  **RowStateFilter** özellikleri değiştirildiğinde, tüm başlangıç sıralama düzeni sağlayan veya oluşturduğunuzda filtreleme ölçütleri oluşturucu bağımsız değişken olarak en iyi performans elde **DataView**.</span><span class="sxs-lookup"><span data-stu-id="9b66f-107">Because the index for a **DataView** is built both when the **DataView** is created, and when any of the **Sort**, **RowFilter**, or **RowStateFilter** properties are modified, you achieve best performance by supplying any initial sort order or filtering criteria as constructor arguments when you create the **DataView**.</span></span> <span data-ttu-id="9b66f-108">Oluşturma bir **DataView** sıralama veya filtre ölçütünü belirterek ve ardından ayarlar olmadan **sıralama**, **RowFilter**, veya **RowStateFilter** özellikleri daha sonra en az iki kez oluşturulacak dizin neden olur: sonra zaman **DataView** oluşturulduğu ve yeniden sıralama veya filtre özelliklerden herhangi biri değiştirildiği.</span><span class="sxs-lookup"><span data-stu-id="9b66f-108">Creating a **DataView** without specifying sort or filter criteria and then setting the **Sort**, **RowFilter**, or **RowStateFilter** properties later causes the index to be built at least twice: once when the **DataView** is created, and again when any of the sort or filter properties are modified.</span></span>  
  
 <span data-ttu-id="9b66f-109">Oluşturduğunuz gerçekleştiriyorsanız bir **DataView** herhangi bir bağımsız değişken almaz Oluşturucusu kullanarak, kullanmanız mümkün olmayacaktır **DataView** ayarladığınız kadar **tablo** özelliği .</span><span class="sxs-lookup"><span data-stu-id="9b66f-109">Note that if you create a **DataView** using the constructor that does not take any arguments, you will not be able to use the **DataView** until you have set the **Table** property.</span></span>  
  
 <span data-ttu-id="9b66f-110">Aşağıdaki kod örneğinde nasıl oluşturulduğunu gösteren bir **DataView** kullanarak **DataView** Oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="9b66f-110">The following code example demonstrates how to create a **DataView** using the **DataView** constructor.</span></span> <span data-ttu-id="9b66f-111">A **RowFilter**, **sıralama** sütun ve **DataViewRowState** ile birlikte sağlanan **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="9b66f-111">A **RowFilter**, **Sort** column, and **DataViewRowState** are supplied along with the **DataTable**.</span></span>  
  
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
  
 <span data-ttu-id="9b66f-112">Aşağıdaki kod örneği, varsayılan bir başvuru almak gösterilmiştir **DataView** , bir **DataTable** kullanarak **DefaultView** tablo özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="9b66f-112">The following code example demonstrates how to obtain a reference to the default **DataView** of a **DataTable** using the **DefaultView** property of the table.</span></span>  
  
```vb  
Dim custDV As DataView = custDS.Tables("Customers").DefaultView  
```  
  
```csharp  
DataView custDV = custDS.Tables["Customers"].DefaultView;  
```  
  
## <a name="see-also"></a><span data-ttu-id="9b66f-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9b66f-113">See Also</span></span>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataView>  
 [<span data-ttu-id="9b66f-114">DataViews</span><span class="sxs-lookup"><span data-stu-id="9b66f-114">DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [<span data-ttu-id="9b66f-115">Verileri Sıralama ve Filtreleme</span><span class="sxs-lookup"><span data-stu-id="9b66f-115">Sorting and Filtering Data</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md)  
 [<span data-ttu-id="9b66f-116">DataTables</span><span class="sxs-lookup"><span data-stu-id="9b66f-116">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [<span data-ttu-id="9b66f-117">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="9b66f-117">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
