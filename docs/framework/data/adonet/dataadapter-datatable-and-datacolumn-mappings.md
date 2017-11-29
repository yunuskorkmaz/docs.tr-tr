---
title: "DataAdapter DataTable ve DataColumn eşlemeleri"
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
ms.assetid: d023260a-a66a-4c39-b8f4-090cd130e730
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: e96eb8e48b5787db5296458af650133747687295
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="dataadapter-datatable-and-datacolumn-mappings"></a><span data-ttu-id="610ef-102">DataAdapter DataTable ve DataColumn eşlemeleri</span><span class="sxs-lookup"><span data-stu-id="610ef-102">DataAdapter DataTable and DataColumn Mappings</span></span>
<span data-ttu-id="610ef-103">A **DataAdapter** sıfır veya daha fazla koleksiyonu içeren <xref:System.Data.Common.DataTableMapping> nesnelerini kendi **TableMappings** özelliği.</span><span class="sxs-lookup"><span data-stu-id="610ef-103">A **DataAdapter** contains a collection of zero or more <xref:System.Data.Common.DataTableMapping> objects in its **TableMappings** property.</span></span> <span data-ttu-id="610ef-104">A **DataTableMapping** bir veri kaynağına karşı sorgu sağlayıcıdan döndürülen verileri arasında ana bir eşleme sağlar ve bir <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="610ef-104">A **DataTableMapping** provides a master mapping between the data returned from a query against a data source, and a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="610ef-105">**DataTableMapping** adı yerine geçirilebilir **DataTable** için ad **doldurun** yöntemi **DataAdapter**.</span><span class="sxs-lookup"><span data-stu-id="610ef-105">The **DataTableMapping** name can be passed in place of the **DataTable** name to the **Fill** method of the **DataAdapter**.</span></span> <span data-ttu-id="610ef-106">Aşağıdaki örnekte bir **DataTableMapping** adlı **AuthorsMapping** için **yazarlar** tablo.</span><span class="sxs-lookup"><span data-stu-id="610ef-106">The following example creates a **DataTableMapping** named **AuthorsMapping** for the **Authors** table.</span></span>  
  
```vb  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors")  
```  
  
```csharp  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors");  
```  
  
 <span data-ttu-id="610ef-107">A **DataTableMapping** sütun adları kullanmanıza olanak sağlayan bir **DataTable** , veritabanındaki kullanılanlardan farklı.</span><span class="sxs-lookup"><span data-stu-id="610ef-107">A **DataTableMapping** enables you to use column names in a **DataTable** that are different from those in the database.</span></span> <span data-ttu-id="610ef-108">**DataAdapter** eşleme tablosu güncelleştirildiğinde sütunlarla eşleşmesi için kullanır.</span><span class="sxs-lookup"><span data-stu-id="610ef-108">The **DataAdapter** uses the mapping to match the columns when the table is updated.</span></span>  
  
 <span data-ttu-id="610ef-109">Belirtmezseniz, bir **TableName** veya **DataTableMapping** ad çağrılırken **doldurun** veya **güncelleştirme** yöntemi  **DataAdapter**, **DataAdapter** arar bir **DataTableMapping** "Tablo" adlı.</span><span class="sxs-lookup"><span data-stu-id="610ef-109">If you do not specify a **TableName** or a **DataTableMapping** name when calling the **Fill** or **Update** method of the **DataAdapter**, the **DataAdapter** looks for a **DataTableMapping** named "Table".</span></span> <span data-ttu-id="610ef-110">Bu, **DataTableMapping** yok, **TableName** , **DataTable** "Tablo".</span><span class="sxs-lookup"><span data-stu-id="610ef-110">If that **DataTableMapping** does not exist, the **TableName** of the **DataTable** is "Table".</span></span> <span data-ttu-id="610ef-111">Varsayılan belirtebilirsiniz **DataTableMapping** oluşturarak bir **DataTableMapping** "Tablo" adı.</span><span class="sxs-lookup"><span data-stu-id="610ef-111">You can specify a default **DataTableMapping** by creating a **DataTableMapping** with the name of "Table".</span></span>  
  
 <span data-ttu-id="610ef-112">Aşağıdaki kod örneği oluşturur bir **DataTableMapping** (gelen <xref:System.Data.Common> ad alanı) için belirtilen varsayılan eşleme yapar **DataAdapter** "Tablo" adlandırma tarafından.</span><span class="sxs-lookup"><span data-stu-id="610ef-112">The following code example creates a **DataTableMapping** (from the <xref:System.Data.Common> namespace) and makes it the default mapping for the specified **DataAdapter** by naming it "Table".</span></span> <span data-ttu-id="610ef-113">Örnek sorgu sonucundaki ilk tablodaki sütunların sonra eşlemeleri ( **müşteriler** tablosu **Northwind** veritabanı) daha kullanıcı dostu adlarında kümesine **Northwind müşterileri**  tablosundaki <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="610ef-113">The example then maps the columns from the first table in the query result (the **Customers** table of the **Northwind** database) to a set of more user-friendly names in the **Northwind Customers** table in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="610ef-114">Eşlenmemiş sütunlar için veri kaynağından sütunun adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="610ef-114">For columns that are not mapped, the name of the column from the data source is used.</span></span>  
  
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
  
 <span data-ttu-id="610ef-115">Daha gelişmiş durumlarda aynı istediğiniz karar verebilir **DataAdapter** farklı eşlemeleri farklı tablolarla yüklenirken desteklemek için.</span><span class="sxs-lookup"><span data-stu-id="610ef-115">In more advanced situations, you may decide that you want the same **DataAdapter** to support loading different tables with different mappings.</span></span> <span data-ttu-id="610ef-116">Bunu yapmak için sadece olarak ek ekleyin **DataTableMapping** nesneleri.</span><span class="sxs-lookup"><span data-stu-id="610ef-116">To do this, simply add additional **DataTableMapping** objects.</span></span>  
  
 <span data-ttu-id="610ef-117">Zaman **doldurun** yöntemi örneği geçirilen bir **DataSet** ve **DataTableMapping** adı, bu adı taşıyan bir eşleme varsa, kullanılan Aksi takdirde bir  **DataTable** ile adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="610ef-117">When the **Fill** method is passed an instance of a **DataSet** and a **DataTableMapping** name, if a mapping with that name exists it is used; otherwise, a **DataTable** with that name is used.</span></span>  
  
 <span data-ttu-id="610ef-118">Aşağıdaki örnekler oluşturma bir **DataTableMapping** adıyla **müşteriler** ve **DataTable** adını **BizTalkSchema**.</span><span class="sxs-lookup"><span data-stu-id="610ef-118">The following examples create a **DataTableMapping** with a name of **Customers** and a **DataTable** name of **BizTalkSchema**.</span></span> <span data-ttu-id="610ef-119">Örnek ardından SELECT deyimi tarafından döndürülen satır eşler **BizTalkSchema** **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="610ef-119">The example then maps the rows returned by the SELECT statement to the **BizTalkSchema** **DataTable**.</span></span>  
  
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
>  <span data-ttu-id="610ef-120">Sütun eşlemesi için bir kaynak sütun adı belirtilmedi veya bir kaynak tablo adı için bir tablo eşlemesi belirtilmedi, varsayılan adlarını otomatik olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="610ef-120">If a source column name is not supplied for a column mapping or a source table name is not supplied for a table mapping, default names will be automatically generated.</span></span> <span data-ttu-id="610ef-121">Hiç kaynak sütunu için sütun eşleme sağlanırsa, sütun eşlemesi bir artımlı varsayılan adı verilen **SourceColumn** *N* başlayarak **SourceColumn1**.</span><span class="sxs-lookup"><span data-stu-id="610ef-121">If no source column is supplied for a column mapping, the column mapping is given an incremental default name of **SourceColumn** *N,* starting with **SourceColumn1**.</span></span> <span data-ttu-id="610ef-122">Kaynak tablo adı için bir tablo eşleme sağlanırsa, tablo eşlemesi bir artımlı varsayılan adı verilen **SourceTable** *N*sürümünden itibaren **SourceTable1**.</span><span class="sxs-lookup"><span data-stu-id="610ef-122">If no source table name is supplied for a table mapping, the table mapping is given an incremental default name of **SourceTable** *N*, starting with **SourceTable1**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="610ef-123">Adlandırma kuralı kaçınmanızı öneririz **SourceColumn** *N* bir sütun eşlemesi için veya **SourceTable** *N* bir tablo için Sağladığınız ad mevcut bir varsayılan sütun eşlemesi adı ile çakışıyor olabilir çünkü eşleme **ColumnMappingCollection** veya Tablo eşleme adını **DataTableMappingCollection** .</span><span class="sxs-lookup"><span data-stu-id="610ef-123">We recommend that you avoid the naming convention of **SourceColumn** *N* for a column mapping, or **SourceTable** *N* for a table mapping, because the name you supply may conflict with an existing default column mapping name in the **ColumnMappingCollection** or table mapping name in the **DataTableMappingCollection**.</span></span> <span data-ttu-id="610ef-124">Sağlanan adı zaten varsa, bir özel durum.</span><span class="sxs-lookup"><span data-stu-id="610ef-124">If the supplied name already exists, an exception will be thrown.</span></span>  
  
## <a name="handling-multiple-result-sets"></a><span data-ttu-id="610ef-125">Birden çok sonuç kümesi işleme</span><span class="sxs-lookup"><span data-stu-id="610ef-125">Handling Multiple Result Sets</span></span>  
 <span data-ttu-id="610ef-126">Varsa, **SelectCommand** birden çok tablo döndüren **doldurun** artımlı değerlerle tablo adları tablolar için otomatik olarak oluşturur **DataSet**sürümünden itibaren Belirtilen tablo adı ve devam etmeden biçiminde **TableName** *N*sürümünden itibaren **TableName1**.</span><span class="sxs-lookup"><span data-stu-id="610ef-126">If your **SelectCommand** returns multiple tables, **Fill** automatically generates table names with incremental values for the tables in the **DataSet**, starting with the specified table name and continuing on in the form **TableName** *N*, starting with **TableName1**.</span></span> <span data-ttu-id="610ef-127">Tablo için belirtilen istediğiniz bir adla otomatik olarak oluşturulan tablo adını eşleştirmek için Tablo eşlemeleri kullanabilirsiniz **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="610ef-127">You can use table mappings to map the automatically generated table name to a name you want specified for the table in the **DataSet**.</span></span> <span data-ttu-id="610ef-128">Örneğin, bir **SelectCommand** iki tablo döndüren **müşteriler** ve **siparişleri**, aşağıdaki çağrıyı sorun **doldurun**.</span><span class="sxs-lookup"><span data-stu-id="610ef-128">For example, for a **SelectCommand** that returns two tables, **Customers** and **Orders**, issue the following call to **Fill**.</span></span>  
  
```  
adapter.Fill(customersDataSet, "Customers")  
```  
  
 <span data-ttu-id="610ef-129">İki tablo oluşturulan **DataSet**: **müşteriler** ve **Customers1**.</span><span class="sxs-lookup"><span data-stu-id="610ef-129">Two tables are created in the **DataSet**: **Customers** and **Customers1**.</span></span> <span data-ttu-id="610ef-130">Tablo eşlemeleri ikinci tablo adlandırdığınız emin olmak için kullanabileceğiniz **siparişleri** yerine **Customers1**.</span><span class="sxs-lookup"><span data-stu-id="610ef-130">You can use table mappings to ensure that the second table is named **Orders** instead of **Customers1**.</span></span> <span data-ttu-id="610ef-131">Bunu yapmak için kaynak tablosu eşleyin **Customers1** için **DataSet** tablo **siparişleri**, aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="610ef-131">To do this, map the source table of **Customers1** to the **DataSet** table **Orders**, as shown in the following example.</span></span>  
  
```  
adapter.TableMappings.Add("Customers1", "Orders")  
adapter.Fill(customersDataSet, "Customers")  
```  
  
## <a name="see-also"></a><span data-ttu-id="610ef-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="610ef-132">See Also</span></span>  
 [<span data-ttu-id="610ef-133">DataAdapters ve DataReader</span><span class="sxs-lookup"><span data-stu-id="610ef-133">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="610ef-134">Alma ve ADO.NET veri değiştirme</span><span class="sxs-lookup"><span data-stu-id="610ef-134">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="610ef-135">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="610ef-135">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
