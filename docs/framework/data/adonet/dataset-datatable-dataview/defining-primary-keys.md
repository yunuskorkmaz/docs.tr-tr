---
title: Birincil Anahtarlar Tanımlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2ea85959-e763-4669-8bd9-46a9dab894bd
ms.openlocfilehash: 159b23eb4ef5ca38ebce6e488080d315ec3be081
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151188"
---
# <a name="defining-primary-keys"></a><span data-ttu-id="dfd5b-102">Birincil Anahtarlar Tanımlama</span><span class="sxs-lookup"><span data-stu-id="dfd5b-102">Defining Primary Keys</span></span>
<span data-ttu-id="dfd5b-103">Veritabanı tablosunda genellikle tablodaki her satırı benzersiz olarak tanımlayan bir sütun veya sütun grubu bulunur.</span><span class="sxs-lookup"><span data-stu-id="dfd5b-103">A database table commonly has a column or group of columns that uniquely identifies each row in the table.</span></span> <span data-ttu-id="dfd5b-104">Bu tanımlayıcı sütun veya sütun grubu birincil anahtar olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="dfd5b-104">This identifying column or group of columns is called the primary key.</span></span>  
  
 <span data-ttu-id="dfd5b-105">Bir tek <xref:System.Data.DataColumn> bir <xref:System.Data.DataTable.PrimaryKey%2A> için olarak <xref:System.Data.DataTable>tanımladığınızda , tablo <xref:System.Data.DataColumn.AllowDBNull%2A> otomatik olarak **yanlış** ve <xref:System.Data.DataColumn.Unique%2A> özelliği **doğru**sütunun özelliği ni ayarlar.</span><span class="sxs-lookup"><span data-stu-id="dfd5b-105">When you identify a single <xref:System.Data.DataColumn> as the <xref:System.Data.DataTable.PrimaryKey%2A> for a <xref:System.Data.DataTable>, the table automatically sets the <xref:System.Data.DataColumn.AllowDBNull%2A> property of the column to **false** and the <xref:System.Data.DataColumn.Unique%2A> property to **true**.</span></span> <span data-ttu-id="dfd5b-106">Birden çok sütunlu birincil anahtarlar için yalnızca **AllowDBNull** özelliği otomatik olarak **false**olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="dfd5b-106">For multiple-column primary keys, only the **AllowDBNull** property is automatically set to **false**.</span></span>  
  
 <span data-ttu-id="dfd5b-107">Bir a'nın <xref:System.Data.DataTable> **PrimaryKey** özelliği, aşağıdaki örneklerde gösterildiği gibi, bir veya daha fazla **DataColumn** nesnesi dizisini değeri olarak alır.</span><span class="sxs-lookup"><span data-stu-id="dfd5b-107">The **PrimaryKey** property of a <xref:System.Data.DataTable> receives as its value an array of one or more **DataColumn** objects, as shown in the following examples.</span></span> <span data-ttu-id="dfd5b-108">İlk örnek, tek bir sütunu birincil anahtar olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="dfd5b-108">The first example defines a single column as the primary key.</span></span>  
  
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
  
 <span data-ttu-id="dfd5b-109">Aşağıdaki örnekte, birincil anahtar olarak iki sütun tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="dfd5b-109">The following example defines two columns as a primary key.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="dfd5b-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dfd5b-110">See also</span></span>

- <xref:System.Data.DataTable>
- [<span data-ttu-id="dfd5b-111">DataTable Şema Tanımı</span><span class="sxs-lookup"><span data-stu-id="dfd5b-111">DataTable Schema Definition</span></span>](datatable-schema-definition.md)
- [<span data-ttu-id="dfd5b-112">DataTables</span><span class="sxs-lookup"><span data-stu-id="dfd5b-112">DataTables</span></span>](datatables.md)
- [<span data-ttu-id="dfd5b-113">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="dfd5b-113">ADO.NET Overview</span></span>](../ado-net-overview.md)
