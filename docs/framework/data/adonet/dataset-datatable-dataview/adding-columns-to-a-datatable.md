---
title: DataTable’a Sütun Ekleme
description: DataTable, tablonun Columns özelliği tarafından başvurulan DataColumn nesnelerini içerir. ADO.NET içindeki bir tabloya sütun eklemek için bu örnek kodu kullanın.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e85c4a0e-4f3f-458c-b58b-0ddbc06bf974
ms.openlocfilehash: 7f220f5d8cbc4b1c12dec018a4497c6bc492f3c1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164889"
---
# <a name="adding-columns-to-a-datatable"></a><span data-ttu-id="b1ccd-104">DataTable’a Sütun Ekleme</span><span class="sxs-lookup"><span data-stu-id="b1ccd-104">Adding Columns to a DataTable</span></span>

<span data-ttu-id="b1ccd-105"><xref:System.Data.DataTable> <xref:System.Data.DataColumn> , Tablonun **Columns** özelliği tarafından başvurulan nesnelerin bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="b1ccd-105">A <xref:System.Data.DataTable> contains a collection of <xref:System.Data.DataColumn> objects referenced by the **Columns** property of the table.</span></span> <span data-ttu-id="b1ccd-106">Bu sütun koleksiyonu, tüm kısıtlamalarla birlikte, tablonun şemasını veya yapısını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b1ccd-106">This collection of columns, along with any constraints, defines the schema, or structure, of the table.</span></span>  
  
 <span data-ttu-id="b1ccd-107">**DataColumn** oluşturucusunu kullanarak veya tablosunun **Columns** özelliğinin **Add** metodunu çağırarak bir tablo içinde **DataColumn** nesneleri oluşturun <xref:System.Data.DataColumnCollection> .</span><span class="sxs-lookup"><span data-stu-id="b1ccd-107">You create **DataColumn** objects within a table by using the **DataColumn** constructor, or by calling the **Add** method of the **Columns** property of the table, which is a <xref:System.Data.DataColumnCollection>.</span></span> <span data-ttu-id="b1ccd-108">**Add** yöntemi, Isteğe bağlı **ColumnName**, **DataType**ve **Expression** bağımsız değişkenlerini kabul eder ve koleksiyonun bir üyesi olarak yeni bir **DataColumn** oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b1ccd-108">The **Add** method accepts optional **ColumnName**, **DataType**, and **Expression** arguments and creates a new **DataColumn** as a member of the collection.</span></span> <span data-ttu-id="b1ccd-109">Ayrıca, var olan bir **DataColumn** nesnesini kabul eder ve koleksiyona ekler ve Isteniyorsa eklenen **DataColumn** öğesine bir başvuru döndürür.</span><span class="sxs-lookup"><span data-stu-id="b1ccd-109">It also accepts an existing **DataColumn** object and adds it to the collection, and returns a reference to the added **DataColumn** if requested.</span></span> <span data-ttu-id="b1ccd-110">**DataTable** nesneleri herhangi bir veri kaynağına özgü olmadığından, bir **DataColumn**veri türü belirtirken .NET Framework türleri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b1ccd-110">Because **DataTable** objects are not specific to any data source, .NET Framework types are used when specifying the data type of a **DataColumn**.</span></span>  
  
 <span data-ttu-id="b1ccd-111">Aşağıdaki örnek, bir **DataTable**'a dört sütun ekler.</span><span class="sxs-lookup"><span data-stu-id="b1ccd-111">The following example adds four columns to a **DataTable**.</span></span>  
  
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
  
 <span data-ttu-id="b1ccd-112">Örnekte, **CustId** sütununun özelliklerinin **DBNull** değerlerine izin vermeyeceğini ve değerlerin benzersiz olduğunu kısıtlamak olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="b1ccd-112">In the example, notice that the properties for the **CustID** column are set to not allow **DBNull** values and to constrain values to be unique.</span></span> <span data-ttu-id="b1ccd-113">Ancak, tablosunun birincil anahtar sütunu olarak **CustId** sütununu tanımlarsanız, **AllowDBNull** özelliği otomatik olarak **false** olarak ayarlanır ve **Unique** özelliği otomatik olarak **doğru**olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="b1ccd-113">However, if you define the **CustID** column as the primary key column of the table, the **AllowDBNull** property will automatically be set to **false** and the **Unique** property will automatically be set to **true**.</span></span> <span data-ttu-id="b1ccd-114">Daha fazla bilgi için bkz. [birincil anahtarları tanımlama](defining-primary-keys.md).</span><span class="sxs-lookup"><span data-stu-id="b1ccd-114">For more information, see [Defining Primary Keys](defining-primary-keys.md).</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="b1ccd-115">Bir sütun için bir sütun adı sağlanmazsa, sütuna, **DataColumnCollection**'a eklendiğinde "Sütun1"*ile başlayan, sütun için* artımlı bir varsayılan ad verilir.</span><span class="sxs-lookup"><span data-stu-id="b1ccd-115">If a column name is not supplied for a column, the column is given an incremental default name of Column*N,* starting with "Column1", when it is added to the **DataColumnCollection**.</span></span> <span data-ttu-id="b1ccd-116">Sağladığınız ad, **DataColumnCollection**içinde varolan bir varsayılan sütun adıyla çakışabileceğinden, bir sütun adı belirttiğinizde "sütun*N*" adlandırma kuralına engel olmasını öneririz.</span><span class="sxs-lookup"><span data-stu-id="b1ccd-116">We recommend that you avoid the naming convention of "Column*N*" when you supply a column name, because the name you supply may conflict with an existing default column name in the **DataColumnCollection**.</span></span> <span data-ttu-id="b1ccd-117">Sağlanan ad zaten varsa, bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b1ccd-117">If the supplied name already exists, an exception is thrown.</span></span>  
  
 <span data-ttu-id="b1ccd-118"><xref:System.Xml.Linq.XElement> <xref:System.Data.DataColumn.DataType%2A> İçindeki bir ' ı olarak kullanıyorsanız, <xref:System.Data.DataColumn> <xref:System.Data.DataTable> verileri okurken XML serileştirme çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="b1ccd-118">If you are using <xref:System.Xml.Linq.XElement> as the <xref:System.Data.DataColumn.DataType%2A> of a <xref:System.Data.DataColumn> in the <xref:System.Data.DataTable>, XML serialization will not work when you read in data.</span></span> <span data-ttu-id="b1ccd-119">Örneğin, <xref:System.Xml.XmlDocument> yöntemini kullanarak bir yazarsanız `DataTable.WriteXml` , XML 'e Serileştirmeden sonra içinde ek bir üst düğüm vardır <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="b1ccd-119">For example, if you write out a <xref:System.Xml.XmlDocument> by using the `DataTable.WriteXml` method, upon serialization to XML there is an additional parent node in the <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="b1ccd-120">Bu sorunu geçici olarak çözmek için <xref:System.Data.SqlTypes.SqlXml> yerine türünü kullanın <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="b1ccd-120">To work around this problem, use the <xref:System.Data.SqlTypes.SqlXml> type instead of <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="b1ccd-121">`ReadXml` ve `WriteXml` ile düzgün çalışır <xref:System.Data.SqlTypes.SqlXml> .</span><span class="sxs-lookup"><span data-stu-id="b1ccd-121">`ReadXml` and `WriteXml` work correctly with <xref:System.Data.SqlTypes.SqlXml>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1ccd-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b1ccd-122">See also</span></span>

- <xref:System.Data.DataColumn>
- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="b1ccd-123">DataTable Şema Tanımı</span><span class="sxs-lookup"><span data-stu-id="b1ccd-123">DataTable Schema Definition</span></span>](datatable-schema-definition.md)
- [<span data-ttu-id="b1ccd-124">DataTables</span><span class="sxs-lookup"><span data-stu-id="b1ccd-124">DataTables</span></span>](datatables.md)
- [<span data-ttu-id="b1ccd-125">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b1ccd-125">ADO.NET Overview</span></span>](../ado-net-overview.md)
