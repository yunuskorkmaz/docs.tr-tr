---
title: DataTable’a Sütun Ekleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e85c4a0e-4f3f-458c-b58b-0ddbc06bf974
ms.openlocfilehash: 6e0dcd819dc354e1fd23b244692dff5091142004
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784849"
---
# <a name="adding-columns-to-a-datatable"></a><span data-ttu-id="83b5a-102">DataTable’a Sütun Ekleme</span><span class="sxs-lookup"><span data-stu-id="83b5a-102">Adding Columns to a DataTable</span></span>
<span data-ttu-id="83b5a-103">, Tablonun **Columns** özelliği tarafından <xref:System.Data.DataColumn> başvurulan nesnelerin bir koleksiyonunu içerir.<xref:System.Data.DataTable></span><span class="sxs-lookup"><span data-stu-id="83b5a-103">A <xref:System.Data.DataTable> contains a collection of <xref:System.Data.DataColumn> objects referenced by the **Columns** property of the table.</span></span> <span data-ttu-id="83b5a-104">Bu sütun koleksiyonu, tüm kısıtlamalarla birlikte, tablonun şemasını veya yapısını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="83b5a-104">This collection of columns, along with any constraints, defines the schema, or structure, of the table.</span></span>  
  
 <span data-ttu-id="83b5a-105">**DataColumn** oluşturucusunu kullanarak veya tablosunun **Columns** özelliğinin <xref:System.Data.DataColumnCollection> **Add** metodunu çağırarak bir tablo içinde **DataColumn** nesneleri oluşturun.</span><span class="sxs-lookup"><span data-stu-id="83b5a-105">You create **DataColumn** objects within a table by using the **DataColumn** constructor, or by calling the **Add** method of the **Columns** property of the table, which is a <xref:System.Data.DataColumnCollection>.</span></span> <span data-ttu-id="83b5a-106">**Add** yöntemi, Isteğe bağlı **ColumnName**, **DataType**ve **Expression** bağımsız değişkenlerini kabul eder ve koleksiyonun bir üyesi olarak yeni bir **DataColumn** oluşturur.</span><span class="sxs-lookup"><span data-stu-id="83b5a-106">The **Add** method accepts optional **ColumnName**, **DataType**, and **Expression** arguments and creates a new **DataColumn** as a member of the collection.</span></span> <span data-ttu-id="83b5a-107">Ayrıca, var olan bir **DataColumn** nesnesini kabul eder ve koleksiyona ekler ve Isteniyorsa eklenen **DataColumn** öğesine bir başvuru döndürür.</span><span class="sxs-lookup"><span data-stu-id="83b5a-107">It also accepts an existing **DataColumn** object and adds it to the collection, and returns a reference to the added **DataColumn** if requested.</span></span> <span data-ttu-id="83b5a-108">**DataTable** nesneleri herhangi bir veri kaynağına özgü olmadığından, bir **DataColumn**veri türü belirtirken .NET Framework türleri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="83b5a-108">Because **DataTable** objects are not specific to any data source, .NET Framework types are used when specifying the data type of a **DataColumn**.</span></span>  
  
 <span data-ttu-id="83b5a-109">Aşağıdaki örnek, bir **DataTable**'a dört sütun ekler.</span><span class="sxs-lookup"><span data-stu-id="83b5a-109">The following example adds four columns to a **DataTable**.</span></span>  
  
```vb  
Dim workTable As DataTable = New DataTable("Customers")  
  
Dim workCol As DataColumn = workTable.Columns.Add( _  
    "CustID", Type.GetType("System.Int32"))  
workCol.AllowDBNull = false  
workCol.Unique = true  
  
workTable.Columns.Add("CustLName", Type.GetType("System.String"))  
workTable.Columns.Add("CustFName", Type.GetType("System.String"))  
workTable.Columns.Add("Purchases", Type.GetType("System.Double"))  
```  
  
```csharp  
DataTable workTable = new DataTable("Customers");  
  
DataColumn workCol = workTable.Columns.Add("CustID", typeof(Int32));  
workCol.AllowDBNull = false;  
workCol.Unique = true;  
  
workTable.Columns.Add("CustLName", typeof(String));  
workTable.Columns.Add("CustFName", typeof(String));  
workTable.Columns.Add("Purchases", typeof(Double));  
```  
  
 <span data-ttu-id="83b5a-110">Örnekte, **CustId** sütununun özelliklerinin **DBNull** değerlerine izin vermeyeceğini ve değerlerin benzersiz olduğunu kısıtlamak olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="83b5a-110">In the example, notice that the properties for the **CustID** column are set to not allow **DBNull** values and to constrain values to be unique.</span></span> <span data-ttu-id="83b5a-111">Ancak, tablosunun birincil anahtar sütunu olarak **CustId** sütununu tanımlarsanız, **AllowDBNull** özelliği otomatik olarak **false** olarak ayarlanır ve **Unique** özelliği otomatik olarak **doğru**olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="83b5a-111">However, if you define the **CustID** column as the primary key column of the table, the **AllowDBNull** property will automatically be set to **false** and the **Unique** property will automatically be set to **true**.</span></span> <span data-ttu-id="83b5a-112">Daha fazla bilgi için bkz. [birincil anahtarları tanımlama](defining-primary-keys.md).</span><span class="sxs-lookup"><span data-stu-id="83b5a-112">For more information, see [Defining Primary Keys](defining-primary-keys.md).</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="83b5a-113">Bir sütun için bir sütun adı sağlanmazsa, sütuna, **DataColumnCollection**'a eklendiğinde "Sütun1"*ile başlayan, sütun için* artımlı bir varsayılan ad verilir.</span><span class="sxs-lookup"><span data-stu-id="83b5a-113">If a column name is not supplied for a column, the column is given an incremental default name of Column*N,* starting with "Column1", when it is added to the **DataColumnCollection**.</span></span> <span data-ttu-id="83b5a-114">Sağladığınız ad, **DataColumnCollection**içinde varolan bir varsayılan sütun adıyla çakışabileceğinden, bir sütun adı belirttiğinizde "sütun*N*" adlandırma kuralına engel olmasını öneririz.</span><span class="sxs-lookup"><span data-stu-id="83b5a-114">We recommend that you avoid the naming convention of "Column*N*" when you supply a column name, because the name you supply may conflict with an existing default column name in the **DataColumnCollection**.</span></span> <span data-ttu-id="83b5a-115">Sağlanan ad zaten varsa, bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="83b5a-115">If the supplied name already exists, an exception is thrown.</span></span>  
  
 <span data-ttu-id="83b5a-116"><xref:System.Xml.Linq.XElement> İçindeki bir <xref:System.Data.DataColumn.DataType%2A> '<xref:System.Data.DataTable>ıolarak kullanıyorsanız, verileri okurken XML serileştirme çalışmaz. <xref:System.Data.DataColumn></span><span class="sxs-lookup"><span data-stu-id="83b5a-116">If you are using <xref:System.Xml.Linq.XElement> as the <xref:System.Data.DataColumn.DataType%2A> of a <xref:System.Data.DataColumn> in the <xref:System.Data.DataTable>, XML serialization will not work when you read in data.</span></span> <span data-ttu-id="83b5a-117">Örneğin, <xref:System.Xml.XmlDocument> `DataTable.WriteXml` yöntemini kullanarak bir yazarsanız, XML 'e Serileştirmeden sonra içinde <xref:System.Xml.Linq.XElement>ek bir üst düğüm vardır.</span><span class="sxs-lookup"><span data-stu-id="83b5a-117">For example, if you write out a <xref:System.Xml.XmlDocument> by using the `DataTable.WriteXml` method, upon serialization to XML there is an additional parent node in the <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="83b5a-118">Bu sorunu geçici olarak çözmek için <xref:System.Data.SqlTypes.SqlXml> <xref:System.Xml.Linq.XElement>yerine türünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="83b5a-118">To work around this problem, use the <xref:System.Data.SqlTypes.SqlXml> type instead of <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="83b5a-119">`ReadXml`ve `WriteXml` ile<xref:System.Data.SqlTypes.SqlXml>düzgün çalışır.</span><span class="sxs-lookup"><span data-stu-id="83b5a-119">`ReadXml` and `WriteXml` work correctly with <xref:System.Data.SqlTypes.SqlXml>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83b5a-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="83b5a-120">See also</span></span>

- <xref:System.Data.DataColumn>
- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="83b5a-121">DataTable Şema Tanımı</span><span class="sxs-lookup"><span data-stu-id="83b5a-121">DataTable Schema Definition</span></span>](datatable-schema-definition.md)
- [<span data-ttu-id="83b5a-122">DataTables</span><span class="sxs-lookup"><span data-stu-id="83b5a-122">DataTables</span></span>](datatables.md)
- [<span data-ttu-id="83b5a-123">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="83b5a-123">ADO.NET Overview</span></span>](../ado-net-overview.md)
