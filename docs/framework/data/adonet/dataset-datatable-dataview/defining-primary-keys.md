---
title: "Birincil anahtarlar tanımlama"
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
ms.assetid: 2ea85959-e763-4669-8bd9-46a9dab894bd
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: dffced0e3d8cd28699d41ea6bb286e3d59f16bb2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="defining-primary-keys"></a><span data-ttu-id="40240-102">Birincil anahtarlar tanımlama</span><span class="sxs-lookup"><span data-stu-id="40240-102">Defining Primary Keys</span></span>
<span data-ttu-id="40240-103">Bir veritabanı tablosu genellikle bir sütun veya sütunlar tablodaki her satırda benzersiz olarak tanımlayan grubunun sahiptir.</span><span class="sxs-lookup"><span data-stu-id="40240-103">A database table commonly has a column or group of columns that uniquely identifies each row in the table.</span></span> <span data-ttu-id="40240-104">Bu tanımlayıcı sütun veya sütun grubunun birincil anahtar adı verilir.</span><span class="sxs-lookup"><span data-stu-id="40240-104">This identifying column or group of columns is called the primary key.</span></span>  
  
 <span data-ttu-id="40240-105">Tanımlamak zaman tek bir <xref:System.Data.DataColumn> olarak <xref:System.Data.DataTable.PrimaryKey%2A> için bir <xref:System.Data.DataTable>, tablonun otomatik olarak ayarlar <xref:System.Data.DataColumn.AllowDBNull%2A> sütuna özelliğinin **false** ve <xref:System.Data.DataColumn.Unique%2A> özelliğine  **doğru**.</span><span class="sxs-lookup"><span data-stu-id="40240-105">When you identify a single <xref:System.Data.DataColumn> as the <xref:System.Data.DataTable.PrimaryKey%2A> for a <xref:System.Data.DataTable>, the table automatically sets the <xref:System.Data.DataColumn.AllowDBNull%2A> property of the column to **false** and the <xref:System.Data.DataColumn.Unique%2A> property to **true**.</span></span> <span data-ttu-id="40240-106">Birden çok sütun birincil anahtarlar için yalnızca **AllowDBNull** özelliği ayarlanmış otomatik olarak **false**.</span><span class="sxs-lookup"><span data-stu-id="40240-106">For multiple-column primary keys, only the **AllowDBNull** property is automatically set to **false**.</span></span>  
  
 <span data-ttu-id="40240-107">**PrimaryKey** özelliği bir <xref:System.Data.DataTable> değer olarak bir dizi bir veya daha fazla alan **DataColumn** , aşağıdaki örneklerde gösterildiği gibi nesneleri.</span><span class="sxs-lookup"><span data-stu-id="40240-107">The **PrimaryKey** property of a <xref:System.Data.DataTable> receives as its value an array of one or more **DataColumn** objects, as shown in the following examples.</span></span> <span data-ttu-id="40240-108">İlk örnek tek bir sütun birincil anahtar olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="40240-108">The first example defines a single column as the primary key.</span></span>  
  
```vb  
workTable.PrimaryKey = New DataColumn() {workTable.Columns("CustID")}  
  
' Or  
  
Dim columns(1) As DataColumn  
columns(0) = workTable.Columns("CustID")  
workTable.PrimaryKey = columns  
```  
  
```csharp  
workTable.PrimaryKey = new DataColumn[] {workTable.Columns["CustID"]};  
  
// Or  
  
DataColumn[] columns = new DataColumn[1];  
columns[0] = workTable.Columns["CustID"];  
workTable.PrimaryKey = columns;  
```  
  
 <span data-ttu-id="40240-109">Aşağıdaki örnek, bir birincil anahtar olarak iki sütun tanımlar.</span><span class="sxs-lookup"><span data-stu-id="40240-109">The following example defines two columns as a primary key.</span></span>  
  
```vb  
workTable.PrimaryKey = New DataColumn() {workTable.Columns("CustLName"), _  
                                         workTable.Columns("CustFName")}  
  
' Or  
  
Dim keyColumn(2) As DataColumn  
keyColumn(0) = workTable.Columns("CustLName")  
keyColumn(1) = workTable.Columns("CustFName")  
workTable.PrimaryKey = keyColumn  
```  
  
```csharp  
workTable.PrimaryKey = new DataColumn[] {workTable.Columns["CustLName"],   
                                         workTable.Columns["CustFName"]};  
  
// Or  
  
DataColumn[] keyColumn = new DataColumn[2];  
keyColumn[0] = workTable.Columns["CustLName"];  
keyColumn[1] = workTable.Columns["CustFName"];  
workTable.PrimaryKey = keyColumn;  
```  
  
## <a name="see-also"></a><span data-ttu-id="40240-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="40240-110">See Also</span></span>  
 <xref:System.Data.DataTable>  
 [<span data-ttu-id="40240-111">DataTable Şema Tanımı</span><span class="sxs-lookup"><span data-stu-id="40240-111">DataTable Schema Definition</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 [<span data-ttu-id="40240-112">DataTables</span><span class="sxs-lookup"><span data-stu-id="40240-112">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [<span data-ttu-id="40240-113">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="40240-113">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
