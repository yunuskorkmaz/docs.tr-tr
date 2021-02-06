---
description: 'Daha fazla bilgi edinin: birincil anahtarları tanımlama'
title: Birincil Anahtarlar Tanımlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2ea85959-e763-4669-8bd9-46a9dab894bd
ms.openlocfilehash: 2becfbd124af723f55edb39666352fc501044045
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99652555"
---
# <a name="defining-primary-keys"></a><span data-ttu-id="217ec-103">Birincil Anahtarlar Tanımlama</span><span class="sxs-lookup"><span data-stu-id="217ec-103">Defining Primary Keys</span></span>

<span data-ttu-id="217ec-104">Veritabanı tablosu genellikle tablodaki her satırı benzersiz bir şekilde tanımlayan bir sütun veya sütun grubuna sahiptir.</span><span class="sxs-lookup"><span data-stu-id="217ec-104">A database table commonly has a column or group of columns that uniquely identifies each row in the table.</span></span> <span data-ttu-id="217ec-105">Bu tanımlayıcı sütun veya sütun grubuna birincil anahtar denir.</span><span class="sxs-lookup"><span data-stu-id="217ec-105">This identifying column or group of columns is called the primary key.</span></span>  
  
 <span data-ttu-id="217ec-106"><xref:System.Data.DataColumn>Bir için tek bir olarak belirlediğinizde <xref:System.Data.DataTable.PrimaryKey%2A> <xref:System.Data.DataTable> , tablo otomatik olarak <xref:System.Data.DataColumn.AllowDBNull%2A> sütunun özelliğini **yanlış** , <xref:System.Data.DataColumn.Unique%2A> özelliği de **true** olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="217ec-106">When you identify a single <xref:System.Data.DataColumn> as the <xref:System.Data.DataTable.PrimaryKey%2A> for a <xref:System.Data.DataTable>, the table automatically sets the <xref:System.Data.DataColumn.AllowDBNull%2A> property of the column to **false** and the <xref:System.Data.DataColumn.Unique%2A> property to **true**.</span></span> <span data-ttu-id="217ec-107">Birden çok sütunlu birincil anahtarlar için, yalnızca **AllowDBNull** özelliği otomatik olarak **false** olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="217ec-107">For multiple-column primary keys, only the **AllowDBNull** property is automatically set to **false**.</span></span>  
  
 <span data-ttu-id="217ec-108">Bir öğesinin **PrimaryKey** özelliği, <xref:System.Data.DataTable> Aşağıdaki örneklerde gösterildiği gibi bir veya daha fazla **DataColumn** nesnesinin bir dizisi olarak alır.</span><span class="sxs-lookup"><span data-stu-id="217ec-108">The **PrimaryKey** property of a <xref:System.Data.DataTable> receives as its value an array of one or more **DataColumn** objects, as shown in the following examples.</span></span> <span data-ttu-id="217ec-109">İlk örnek, birincil anahtar olarak tek bir sütunu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="217ec-109">The first example defines a single column as the primary key.</span></span>  
  
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
  
 <span data-ttu-id="217ec-110">Aşağıdaki örnek, iki sütunu birincil anahtar olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="217ec-110">The following example defines two columns as a primary key.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="217ec-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="217ec-111">See also</span></span>

- <xref:System.Data.DataTable>
- [<span data-ttu-id="217ec-112">DataTable Şema Tanımı</span><span class="sxs-lookup"><span data-stu-id="217ec-112">DataTable Schema Definition</span></span>](datatable-schema-definition.md)
- [<span data-ttu-id="217ec-113">DataTables</span><span class="sxs-lookup"><span data-stu-id="217ec-113">DataTables</span></span>](datatables.md)
- [<span data-ttu-id="217ec-114">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="217ec-114">ADO.NET Overview</span></span>](../ado-net-overview.md)
