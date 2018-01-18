---
title: "AutoIncrement sütunlar oluşturma"
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
ms.assetid: cf09732a-ab54-4d98-89e2-4d0a1f28fbce
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 0cef5944db5e926a4b2d81fd226abc9691b6d1bc
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="creating-autoincrement-columns"></a><span data-ttu-id="ee0bd-102">AutoIncrement sütunlar oluşturma</span><span class="sxs-lookup"><span data-stu-id="ee0bd-102">Creating AutoIncrement Columns</span></span>
<span data-ttu-id="ee0bd-103">Benzersiz sütun değerlerini sağlamak için yeni satırlar tabloya eklendiğinde otomatik olarak artırmak için sütun değerlerini ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ee0bd-103">To ensure unique column values, you can set the column values to increment automatically when new rows are added to the table.</span></span> <span data-ttu-id="ee0bd-104">Bir otomatik artırma oluşturmak için <xref:System.Data.DataColumn>ayarlayın <xref:System.Data.DataColumn.AutoIncrement%2A> sütuna özelliğinin **doğru**.</span><span class="sxs-lookup"><span data-stu-id="ee0bd-104">To create an auto-incrementing <xref:System.Data.DataColumn>, set the <xref:System.Data.DataColumn.AutoIncrement%2A> property of the column to **true**.</span></span> <span data-ttu-id="ee0bd-105"><xref:System.Data.DataColumn> Tanımlanan değer ile başlayan <xref:System.Data.DataColumn.AutoIncrementSeed%2A> özelliği ve her satırın değerini eklenen **AutoIncrement** sütun artırır tanımlanan değere göre <xref:System.Data.DataColumn.AutoIncrementStep%2A> sütunun özelliği.</span><span class="sxs-lookup"><span data-stu-id="ee0bd-105">The <xref:System.Data.DataColumn> then starts with the value defined in the <xref:System.Data.DataColumn.AutoIncrementSeed%2A> property, and with each row added the value of the **AutoIncrement** column increases by the value defined in the <xref:System.Data.DataColumn.AutoIncrementStep%2A> property of the column.</span></span>  
  
 <span data-ttu-id="ee0bd-106">İçin **AutoIncrement** sütun öneririz <xref:System.Data.DataColumn.ReadOnly%2A> özelliği **DataColumn** ayarlanabilir **doğru**.</span><span class="sxs-lookup"><span data-stu-id="ee0bd-106">For **AutoIncrement** columns, we recommend that the <xref:System.Data.DataColumn.ReadOnly%2A> property of the **DataColumn** be set to **true**.</span></span>  
  
 <span data-ttu-id="ee0bd-107">Aşağıdaki örnek, 200 değeri ile başlar ve artımlı olarak 3 adımda eklediği bir sütun oluşturmak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ee0bd-107">The following example demonstrates how to create a column that starts with a value of 200 and adds incrementally in steps of 3.</span></span>  
  
```vb  
Dim workColumn As DataColumn = workTable.Columns.Add( _  
    "CustomerID", typeof(Int32))  
workColumn.AutoIncrement = true  
workColumn.AutoIncrementSeed = 200  
workColumn.AutoIncrementStep = 3  
```  
  
```csharp  
DataColumn workColumn = workTable.Columns.Add(  
    "CustomerID", typeof(Int32));  
workColumn.AutoIncrement = true;  
workColumn.AutoIncrementSeed = 200;  
workColumn.AutoIncrementStep = 3;  
```  
  
## <a name="see-also"></a><span data-ttu-id="ee0bd-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ee0bd-108">See Also</span></span>  
 <xref:System.Data.DataColumn>  
 [<span data-ttu-id="ee0bd-109">DataTable Şema Tanımı</span><span class="sxs-lookup"><span data-stu-id="ee0bd-109">DataTable Schema Definition</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 [<span data-ttu-id="ee0bd-110">DataTables</span><span class="sxs-lookup"><span data-stu-id="ee0bd-110">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [<span data-ttu-id="ee0bd-111">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="ee0bd-111">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
