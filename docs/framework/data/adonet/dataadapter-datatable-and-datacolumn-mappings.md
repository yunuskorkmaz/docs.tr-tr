---
title: DataAdapter DataTable ve DataColumn Eşlemeleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d023260a-a66a-4c39-b8f4-090cd130e730
ms.openlocfilehash: a9c81c8554c0fb393c10ed69f84c8b2d936ec1e6
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040123"
---
# <a name="dataadapter-datatable-and-datacolumn-mappings"></a><span data-ttu-id="7561b-102">DataAdapter DataTable ve DataColumn Eşlemeleri</span><span class="sxs-lookup"><span data-stu-id="7561b-102">DataAdapter DataTable and DataColumn Mappings</span></span>
<span data-ttu-id="7561b-103">Bir **DataAdapter** , **TableMappings** özelliğinde sıfır veya daha fazla <xref:System.Data.Common.DataTableMapping> nesne koleksiyonu içerir.</span><span class="sxs-lookup"><span data-stu-id="7561b-103">A **DataAdapter** contains a collection of zero or more <xref:System.Data.Common.DataTableMapping> objects in its **TableMappings** property.</span></span> <span data-ttu-id="7561b-104">Bir **DataTableMapping** , bir sorgudan veri kaynağına göre döndürülen veriler ile bir <xref:System.Data.DataTable>ana eşleme sağlar.</span><span class="sxs-lookup"><span data-stu-id="7561b-104">A **DataTableMapping** provides a master mapping between the data returned from a query against a data source, and a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="7561b-105">**DataTableMapping** adı DataTable 'ın **Fill** metoduna **DataTable** adının yerine **geçirilebilir.**</span><span class="sxs-lookup"><span data-stu-id="7561b-105">The **DataTableMapping** name can be passed in place of the **DataTable** name to the **Fill** method of the **DataAdapter**.</span></span> <span data-ttu-id="7561b-106">Aşağıdaki örnek, **yazarlar** tablosu Için **authorsmapping** adlı bir **DataTableMapping** oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7561b-106">The following example creates a **DataTableMapping** named **AuthorsMapping** for the **Authors** table.</span></span>  
  
```vb  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors")  
```  
  
```csharp  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors");  
```  
  
 <span data-ttu-id="7561b-107">Bir **DataTableMapping** , veritabanından farklı bir **DataTable** içindeki sütun adlarını kullanmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="7561b-107">A **DataTableMapping** enables you to use column names in a **DataTable** that are different from those in the database.</span></span> <span data-ttu-id="7561b-108">**DataAdapter** , tablo güncellendiği zaman sütunları eşleştirmek için eşlemeyi kullanır.</span><span class="sxs-lookup"><span data-stu-id="7561b-108">The **DataAdapter** uses the mapping to match the columns when the table is updated.</span></span>  
  
 <span data-ttu-id="7561b-109">**DataAdapter**'ın **Fill** veya **Update** metodunu çağırırken bir **TableName** veya bir **DataTableMapping** adı belirtmezseniz, **DataAdapter** , "Table" adlı bir **DataTableMapping** öğesine bakar.</span><span class="sxs-lookup"><span data-stu-id="7561b-109">If you do not specify a **TableName** or a **DataTableMapping** name when calling the **Fill** or **Update** method of the **DataAdapter**, the **DataAdapter** looks for a **DataTableMapping** named "Table".</span></span> <span data-ttu-id="7561b-110">Bu **DataTableMapping** yoksa, **DataTable** 'ın **TableName** tablosu "Table" olur.</span><span class="sxs-lookup"><span data-stu-id="7561b-110">If that **DataTableMapping** does not exist, the **TableName** of the **DataTable** is "Table".</span></span> <span data-ttu-id="7561b-111">"Tablo" adıyla bir **DataTableMapping** oluşturarak varsayılan bir **DataTableMapping** belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7561b-111">You can specify a default **DataTableMapping** by creating a **DataTableMapping** with the name of "Table".</span></span>  
  
 <span data-ttu-id="7561b-112">Aşağıdaki kod örneği bir **DataTableMapping** oluşturur (<xref:System.Data.Common> ad alanından) ve "Table" olarak adlandırarak belirtilen **DataAdapter** için varsayılan eşleme yapar.</span><span class="sxs-lookup"><span data-stu-id="7561b-112">The following code example creates a **DataTableMapping** (from the <xref:System.Data.Common> namespace) and makes it the default mapping for the specified **DataAdapter** by naming it "Table".</span></span> <span data-ttu-id="7561b-113">Örnek daha sonra, sorgu sonucu ( **Northwind** veritabanının **Customers** tablosu) içindeki ilk tablodaki sütunları, <xref:System.Data.DataSet>**Northwind Customers** tablosunda daha kolay bir Kullanıcı adı kümesine eşler.</span><span class="sxs-lookup"><span data-stu-id="7561b-113">The example then maps the columns from the first table in the query result (the **Customers** table of the **Northwind** database) to a set of more user-friendly names in the **Northwind Customers** table in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="7561b-114">Eşlenmemiş sütunlarda, veri kaynağındaki sütunun adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7561b-114">For columns that are not mapped, the name of the column from the data source is used.</span></span>  
  
```vb  
Dim mapping As DataTableMapping = _  
  adapter.TableMappings.Add("Table", "NorthwindCustomers")  
mapping.ColumnMappings.Add("CompanyName", "Company")  
mapping.ColumnMappings.Add("ContactName", "Contact")  
mapping.ColumnMappings.Add("PostalCode", "ZIPCode")  
  
adapter.Fill(custDS)  
```  
  
```csharp  
DataTableMapping mapping =   
  adapter.TableMappings.Add("Table", "NorthwindCustomers");  
mapping.ColumnMappings.Add("CompanyName", "Company");  
mapping.ColumnMappings.Add("ContactName", "Contact");  
mapping.ColumnMappings.Add("PostalCode", "ZIPCode");  
  
adapter.Fill(custDS);  
```  
  
 <span data-ttu-id="7561b-115">Daha gelişmiş durumlarda, aynı **DataAdapter** 'ın farklı eşlemelere sahip farklı tabloları yüklemeyi desteklemesini tercih edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7561b-115">In more advanced situations, you may decide that you want the same **DataAdapter** to support loading different tables with different mappings.</span></span> <span data-ttu-id="7561b-116">Bunu yapmak için, ek **DataTableMapping** nesneleri eklemeniz yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="7561b-116">To do this, simply add additional **DataTableMapping** objects.</span></span>  
  
 <span data-ttu-id="7561b-117">**Fill** yöntemine bir **veri kümesi** ve bir ölçü adı geçirildiğinde, bu ada **sahip bir eşleme** varsa kullanılır; Aksi takdirde, bu adı taşıyan bir **DataTable** kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7561b-117">When the **Fill** method is passed an instance of a **DataSet** and a **DataTableMapping** name, if a mapping with that name exists it is used; otherwise, a **DataTable** with that name is used.</span></span>  
  
 <span data-ttu-id="7561b-118">Aşağıdaki örneklerde, **Müşteri** adı ve **BizTalkSchema** **DataTable** adı ile bir **DataTableMapping** oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="7561b-118">The following examples create a **DataTableMapping** with a name of **Customers** and a **DataTable** name of **BizTalkSchema**.</span></span> <span data-ttu-id="7561b-119">Örnek daha sonra SELECT ifadesinin döndürdüğü satırları **BizTalkSchema** **DataTable**' a eşler.</span><span class="sxs-lookup"><span data-stu-id="7561b-119">The example then maps the rows returned by the SELECT statement to the **BizTalkSchema** **DataTable**.</span></span>  
  
```vb  
Dim mapping As ITableMapping = _  
  adapter.TableMappings.Add("Customers", "BizTalkSchema")  
mapping.ColumnMappings.Add("CustomerID", "ClientID")  
mapping.ColumnMappings.Add("CompanyName", "ClientName")  
mapping.ColumnMappings.Add("ContactName", "Contact")  
mapping.ColumnMappings.Add("PostalCode", "ZIP")  
  
adapter.Fill(custDS, "Customers")  
```  
  
```csharp  
ITableMapping mapping =   
  adapter.TableMappings.Add("Customers", "BizTalkSchema");  
mapping.ColumnMappings.Add("CustomerID", "ClientID");  
mapping.ColumnMappings.Add("CompanyName", "ClientName");  
mapping.ColumnMappings.Add("ContactName", "Contact");  
mapping.ColumnMappings.Add("PostalCode", "ZIP");  
  
adapter.Fill(custDS, "Customers");  
```  
  
> [!NOTE]
> <span data-ttu-id="7561b-120">Bir sütun eşlemesi için bir kaynak sütun adı sağlanmamışsa veya tablo eşlemesi için kaynak tablo adı sağlanmadığında, varsayılan adlar otomatik olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="7561b-120">If a source column name is not supplied for a column mapping or a source table name is not supplied for a table mapping, default names will be automatically generated.</span></span> <span data-ttu-id="7561b-121">Bir sütun eşlemesi için kaynak sütun sağlanmazsa, sütun eşlemesine **SourceColumn1**ile başlayan bir **SourceColumn** *N* artımlı varsayılan adı verilir.</span><span class="sxs-lookup"><span data-stu-id="7561b-121">If no source column is supplied for a column mapping, the column mapping is given an incremental default name of **SourceColumn** *N,* starting with **SourceColumn1**.</span></span> <span data-ttu-id="7561b-122">Tablo eşlemesi için kaynak tablo adı sağlanmadığında tablo eşlemesine, **SourceTable1**ile başlayan bir **SourceTable** *N*artımlı varsayılan adı verilir.</span><span class="sxs-lookup"><span data-stu-id="7561b-122">If no source table name is supplied for a table mapping, the table mapping is given an incremental default name of **SourceTable** *N*, starting with **SourceTable1**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7561b-123">Sağladığınız ad, var olan bir varsayılan sütun eşleme adı ile çakışabileceğinden, bir sütun eşlemesi için **SourceColumn** *n* adlandırma kuralını veya tablo eşlemesi için **SourceTable** *n* 'yi kullanmaktan kaçınmanızı öneririz. **DataTableMappingCollection**Içindeki ColumnMappingCollection veya tablo eşleme adı.</span><span class="sxs-lookup"><span data-stu-id="7561b-123">We recommend that you avoid the naming convention of **SourceColumn** *N* for a column mapping, or **SourceTable** *N* for a table mapping, because the name you supply may conflict with an existing default column mapping name in the **ColumnMappingCollection** or table mapping name in the **DataTableMappingCollection**.</span></span> <span data-ttu-id="7561b-124">Sağlanan ad zaten varsa, bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="7561b-124">If the supplied name already exists, an exception will be thrown.</span></span>  
  
## <a name="handling-multiple-result-sets"></a><span data-ttu-id="7561b-125">Birden çok sonuç kümesini işleme</span><span class="sxs-lookup"><span data-stu-id="7561b-125">Handling Multiple Result Sets</span></span>  
 <span data-ttu-id="7561b-126">**SelectCommand** uygulamanız birden çok tablo döndürürse, **Fill** , belirtilen tablo adından başlayarak ve **TableName** biçiminde devam ederek, **veri kümesindeki**tablolar için artımlı değerler içeren tablo adlarını otomatik olarak oluşturur **TableName1**Ile başlayan *N*.</span><span class="sxs-lookup"><span data-stu-id="7561b-126">If your **SelectCommand** returns multiple tables, **Fill** automatically generates table names with incremental values for the tables in the **DataSet**, starting with the specified table name and continuing on in the form **TableName** *N*, starting with **TableName1**.</span></span> <span data-ttu-id="7561b-127">Otomatik olarak üretilen tablo adını, **veri kümesindeki**tablo için belirtilen bir adla eşlemek için tablo eşlemelerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7561b-127">You can use table mappings to map the automatically generated table name to a name you want specified for the table in the **DataSet**.</span></span> <span data-ttu-id="7561b-128">Örneğin, iki tablo, **Müşteri** ve **sipariş**döndüren bir **SelectCommand** için, aşağıdaki çağrıyı **dolduracak**şekilde verin.</span><span class="sxs-lookup"><span data-stu-id="7561b-128">For example, for a **SelectCommand** that returns two tables, **Customers** and **Orders**, issue the following call to **Fill**.</span></span>  
  
```vb  
adapter.Fill(customersDataSet, "Customers")  
```  

```csharp  
adapter.Fill(customersDataSet, "Customers");  
```  

 <span data-ttu-id="7561b-129">**Veri kümesinde**iki tablo oluşturulur: **Customers** ve **Customers1**.</span><span class="sxs-lookup"><span data-stu-id="7561b-129">Two tables are created in the **DataSet**: **Customers** and **Customers1**.</span></span> <span data-ttu-id="7561b-130">Tablo eşlemelerini, ikinci tablonun **Customers1**yerine **siparişler** olarak adlandırılmış olduğundan emin olmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7561b-130">You can use table mappings to ensure that the second table is named **Orders** instead of **Customers1**.</span></span> <span data-ttu-id="7561b-131">Bunu yapmak için, **Customers1** kaynak tablosunu aşağıdaki örnekte gösterildiği gibi **veri kümesi** tablo **siparişleriyle**eşleyin.</span><span class="sxs-lookup"><span data-stu-id="7561b-131">To do this, map the source table of **Customers1** to the **DataSet** table **Orders**, as shown in the following example.</span></span>  
  
```vb  
adapter.TableMappings.Add("Customers1", "Orders")  
adapter.Fill(customersDataSet, "Customers")  
```  

```csharp  
adapter.TableMappings.Add("Customers1", "Orders");  
adapter.Fill(customersDataSet, "Customers");  
```
  
## <a name="see-also"></a><span data-ttu-id="7561b-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7561b-132">See also</span></span>

- [<span data-ttu-id="7561b-133">DataAdapters ve DataReaders</span><span class="sxs-lookup"><span data-stu-id="7561b-133">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="7561b-134">ADO.NET’te Veri Alma ve Değiştirme</span><span class="sxs-lookup"><span data-stu-id="7561b-134">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)
- [<span data-ttu-id="7561b-135">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="7561b-135">ADO.NET Overview</span></span>](ado-net-overview.md)
