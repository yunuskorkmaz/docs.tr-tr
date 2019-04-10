---
title: Birincil Anahtarlar Tanımlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2ea85959-e763-4669-8bd9-46a9dab894bd
ms.openlocfilehash: 84c84cb8fc0ee484b09c69c72571a19c335b58f4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59230635"
---
# <a name="defining-primary-keys"></a><span data-ttu-id="c89bb-102">Birincil Anahtarlar Tanımlama</span><span class="sxs-lookup"><span data-stu-id="c89bb-102">Defining Primary Keys</span></span>
<span data-ttu-id="c89bb-103">Bir veritabanı tablosu, yaygın olarak bir sütun veya tablosundaki her satırda benzersiz olarak tanımlayan sütun grubunun sahiptir.</span><span class="sxs-lookup"><span data-stu-id="c89bb-103">A database table commonly has a column or group of columns that uniquely identifies each row in the table.</span></span> <span data-ttu-id="c89bb-104">Bu tanımlayıcı sütun veya sütun grubunun birincil anahtarı olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="c89bb-104">This identifying column or group of columns is called the primary key.</span></span>  
  
 <span data-ttu-id="c89bb-105">Tanımlamak, tek bir <xref:System.Data.DataColumn> olarak <xref:System.Data.DataTable.PrimaryKey%2A> için bir <xref:System.Data.DataTable>, tablo otomatik olarak ayarlar <xref:System.Data.DataColumn.AllowDBNull%2A> sütununun özellik **false** ve <xref:System.Data.DataColumn.Unique%2A> özelliğini  **true**.</span><span class="sxs-lookup"><span data-stu-id="c89bb-105">When you identify a single <xref:System.Data.DataColumn> as the <xref:System.Data.DataTable.PrimaryKey%2A> for a <xref:System.Data.DataTable>, the table automatically sets the <xref:System.Data.DataColumn.AllowDBNull%2A> property of the column to **false** and the <xref:System.Data.DataColumn.Unique%2A> property to **true**.</span></span> <span data-ttu-id="c89bb-106">Birden çok sütun birincil anahtarlar için yalnızca **AllowDBNull** otomatik olarak ayarlanırsa **false**.</span><span class="sxs-lookup"><span data-stu-id="c89bb-106">For multiple-column primary keys, only the **AllowDBNull** property is automatically set to **false**.</span></span>  
  
 <span data-ttu-id="c89bb-107">**PrimaryKey** özelliği bir <xref:System.Data.DataTable> değeri olarak bir dizi bir veya daha fazla alan **DataColumn** , aşağıdaki örneklerde gösterildiği gibi nesneleri.</span><span class="sxs-lookup"><span data-stu-id="c89bb-107">The **PrimaryKey** property of a <xref:System.Data.DataTable> receives as its value an array of one or more **DataColumn** objects, as shown in the following examples.</span></span> <span data-ttu-id="c89bb-108">İlk örnek, tek bir sütun birincil anahtar olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c89bb-108">The first example defines a single column as the primary key.</span></span>  
  
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
  
 <span data-ttu-id="c89bb-109">Aşağıdaki örnek, iki sütun birincil anahtar olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c89bb-109">The following example defines two columns as a primary key.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c89bb-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c89bb-110">See also</span></span>

- <xref:System.Data.DataTable>
- [<span data-ttu-id="c89bb-111">DataTable Şema Tanımı</span><span class="sxs-lookup"><span data-stu-id="c89bb-111">DataTable Schema Definition</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)
- [<span data-ttu-id="c89bb-112">DataTables</span><span class="sxs-lookup"><span data-stu-id="c89bb-112">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)
- [<span data-ttu-id="c89bb-113">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="c89bb-113">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
