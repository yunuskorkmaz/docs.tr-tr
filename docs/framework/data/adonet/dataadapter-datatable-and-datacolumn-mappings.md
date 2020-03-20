---
title: DataAdapter DataTable ve DataColumn Eşlemeleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d023260a-a66a-4c39-b8f4-090cd130e730
ms.openlocfilehash: 6380dd0512bd7834f50b87f90f445cb01b7a8b95
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151565"
---
# <a name="dataadapter-datatable-and-datacolumn-mappings"></a><span data-ttu-id="80cff-102">DataAdapter DataTable ve DataColumn Eşlemeleri</span><span class="sxs-lookup"><span data-stu-id="80cff-102">DataAdapter DataTable and DataColumn Mappings</span></span>
<span data-ttu-id="80cff-103">**DataAdapter,** **TableMappings** özelliğinde <xref:System.Data.Common.DataTableMapping> sıfır veya daha fazla nesne koleksiyonu içerir.</span><span class="sxs-lookup"><span data-stu-id="80cff-103">A **DataAdapter** contains a collection of zero or more <xref:System.Data.Common.DataTableMapping> objects in its **TableMappings** property.</span></span> <span data-ttu-id="80cff-104">**DataTableMapping,** bir sorgudan bir veri kaynağına karşı döndürülen <xref:System.Data.DataTable>veriler ile bir .</span><span class="sxs-lookup"><span data-stu-id="80cff-104">A **DataTableMapping** provides a master mapping between the data returned from a query against a data source, and a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="80cff-105">**DataTableMapping** adı **DataTable** adının yerine **DataAdapter'ın** **Dolgu** yöntemine geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="80cff-105">The **DataTableMapping** name can be passed in place of the **DataTable** name to the **Fill** method of the **DataAdapter**.</span></span> <span data-ttu-id="80cff-106">Aşağıdaki örnek, **Yazarlar** tablosu için **Yazarlar Eşleme** adlı bir **DataTableMapping** oluşturur.</span><span class="sxs-lookup"><span data-stu-id="80cff-106">The following example creates a **DataTableMapping** named **AuthorsMapping** for the **Authors** table.</span></span>  
  
```vb  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors")  
```  
  
```csharp  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors");  
```  
  
 <span data-ttu-id="80cff-107">**DataTableMapping,** veritabanındakilerden farklı bir **DataTable'da** sütun adlarını kullanmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="80cff-107">A **DataTableMapping** enables you to use column names in a **DataTable** that are different from those in the database.</span></span> <span data-ttu-id="80cff-108">**DataAdapter,** tablo güncelleştirildiğinde sütunları eşleştirmek için eşleci kullanır.</span><span class="sxs-lookup"><span data-stu-id="80cff-108">The **DataAdapter** uses the mapping to match the columns when the table is updated.</span></span>  
  
 <span data-ttu-id="80cff-109">DataAdapter'ın **Dolgu** veya **Güncelleştirme** yöntemini ararken bir **TableName** veya **DataTableMapping** adı belirtmezseniz, **DataAdapter**"Tablo" adlı bir **DataTableMapping eşlemesi** arar. **DataAdapter**</span><span class="sxs-lookup"><span data-stu-id="80cff-109">If you do not specify a **TableName** or a **DataTableMapping** name when calling the **Fill** or **Update** method of the **DataAdapter**, the **DataAdapter** looks for a **DataTableMapping** named "Table".</span></span> <span data-ttu-id="80cff-110">Bu **DataTableMapping** yoksa, **DataTable** **Tablo Adı** "Tablo"dur.</span><span class="sxs-lookup"><span data-stu-id="80cff-110">If that **DataTableMapping** does not exist, the **TableName** of the **DataTable** is "Table".</span></span> <span data-ttu-id="80cff-111">"Tablo" adında bir **DataTableMapping** oluşturarak varsayılan bir **DataTableMapping** belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="80cff-111">You can specify a default **DataTableMapping** by creating a **DataTableMapping** with the name of "Table".</span></span>  
  
 <span data-ttu-id="80cff-112">Aşağıdaki kod örneği bir **DataTableMapping** <xref:System.Data.Common> (ad alanından) oluşturur ve "Tablo" adını vererek belirtilen **DataAdapter** için varsayılan eşleme yapar.</span><span class="sxs-lookup"><span data-stu-id="80cff-112">The following code example creates a **DataTableMapping** (from the <xref:System.Data.Common> namespace) and makes it the default mapping for the specified **DataAdapter** by naming it "Table".</span></span> <span data-ttu-id="80cff-113">Örnek daha sonra sorgu sonucu **(Northwind** veritabanının **Müşteriler** tablosu) ilk tablodan **northwind Müşteriler** tablosunda daha kullanıcı dostu <xref:System.Data.DataSet>adlar kümesi için sütuneşler .</span><span class="sxs-lookup"><span data-stu-id="80cff-113">The example then maps the columns from the first table in the query result (the **Customers** table of the **Northwind** database) to a set of more user-friendly names in the **Northwind Customers** table in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="80cff-114">Eşlenen olmayan sütunlar için, veri kaynağından sütunadı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="80cff-114">For columns that are not mapped, the name of the column from the data source is used.</span></span>  
  
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
  
 <span data-ttu-id="80cff-115">Daha gelişmiş durumlarda, aynı **DataAdapter'ın** farklı tablolara farklı eşlemelerle yüklemeyi desteklemesini istediğinize karar verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="80cff-115">In more advanced situations, you may decide that you want the same **DataAdapter** to support loading different tables with different mappings.</span></span> <span data-ttu-id="80cff-116">Bunu yapmak için ek **DataTableMapping** nesneleri eklemeniz yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="80cff-116">To do this, simply add additional **DataTableMapping** objects.</span></span>  
  
 <span data-ttu-id="80cff-117">**Dolgu** yöntemi bir **DataSet** ve **DataTableMapping** adı örneği geçirildiğinde, bu ada sahip bir eşleme varsa kullanılır; aksi takdirde, bu ada sahip bir **DataTable** kullanılır.</span><span class="sxs-lookup"><span data-stu-id="80cff-117">When the **Fill** method is passed an instance of a **DataSet** and a **DataTableMapping** name, if a mapping with that name exists it is used; otherwise, a **DataTable** with that name is used.</span></span>  
  
 <span data-ttu-id="80cff-118">Aşağıdaki örnekler, **Müşterilerin** adı ve **BizTalkSchema**bir **DataTable** adı ile **DataTableMapping** oluşturun.</span><span class="sxs-lookup"><span data-stu-id="80cff-118">The following examples create a **DataTableMapping** with a name of **Customers** and a **DataTable** name of **BizTalkSchema**.</span></span> <span data-ttu-id="80cff-119">Örnek daha sonra SELECT deyimi tarafından döndürülen satırları **BizTalkSchema** **DataTable**ile eşler.</span><span class="sxs-lookup"><span data-stu-id="80cff-119">The example then maps the rows returned by the SELECT statement to the **BizTalkSchema** **DataTable**.</span></span>  
  
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
> <span data-ttu-id="80cff-120">Bir sütun eşleme için bir kaynak sütun adı sağlanmaz veya tablo eşlemesi için bir kaynak tablo adı sağlanmazsa, varsayılan adlar otomatik olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="80cff-120">If a source column name is not supplied for a column mapping or a source table name is not supplied for a table mapping, default names will be automatically generated.</span></span> <span data-ttu-id="80cff-121">Sütun eşleme için kaynak sütun sağlanmışsa, sütun eşleme **kaynağına SourceColumn1**ile başlayarak **Kaynak Sütun** *U, N'nin* artımlı varsayılan adı verilir.</span><span class="sxs-lookup"><span data-stu-id="80cff-121">If no source column is supplied for a column mapping, the column mapping is given an incremental default name of **SourceColumn** *N,* starting with **SourceColumn1**.</span></span> <span data-ttu-id="80cff-122">Tablo eşleme için kaynak tablo adı sağlanmışsa, tablo eşlemi **SourceTable** *N'nin*artımlı varsayılan adı verilir, **SourceTable1**ile başlayarak.</span><span class="sxs-lookup"><span data-stu-id="80cff-122">If no source table name is supplied for a table mapping, the table mapping is given an incremental default name of **SourceTable** *N*, starting with **SourceTable1**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="80cff-123">Bir sütun eşleme için **SourceColumn** *N'nin* adlandırma kuralından veya tablo eşlemesi için **SourceTable** *N'den* kaçınmanızı öneririz, çünkü sağladığınız **ad, ColumnMappingCollection'daki** varolan varsayılan sütun eşleme adı veya **DataTableMappingCollection'daki**tablo eşleme adı ile çakışabilir.</span><span class="sxs-lookup"><span data-stu-id="80cff-123">We recommend that you avoid the naming convention of **SourceColumn** *N* for a column mapping, or **SourceTable** *N* for a table mapping, because the name you supply may conflict with an existing default column mapping name in the **ColumnMappingCollection** or table mapping name in the **DataTableMappingCollection**.</span></span> <span data-ttu-id="80cff-124">Sağlanan ad zaten varsa, bir özel durum atılır.</span><span class="sxs-lookup"><span data-stu-id="80cff-124">If the supplied name already exists, an exception will be thrown.</span></span>  
  
## <a name="handling-multiple-result-sets"></a><span data-ttu-id="80cff-125">Birden Çok Sonuç Kümesini Işleme</span><span class="sxs-lookup"><span data-stu-id="80cff-125">Handling Multiple Result Sets</span></span>  
 <span data-ttu-id="80cff-126">**SelectCommand'ınız** birden çok tablo döndürürse, **Fill,** belirtilen tablo adı ile başlayan ve **TableName** *N*formunda devam eden **DataSet**tabloları için artımlı değerlere sahip tablo adlarını otomatik olarak oluşturur Tablo **Adı1**ile başlar.</span><span class="sxs-lookup"><span data-stu-id="80cff-126">If your **SelectCommand** returns multiple tables, **Fill** automatically generates table names with incremental values for the tables in the **DataSet**, starting with the specified table name and continuing on in the form **TableName** *N*, starting with **TableName1**.</span></span> <span data-ttu-id="80cff-127">Otomatik olarak oluşturulan tablo adını **DataSet'teki**tablo için belirtilmiş olmasını istediğiniz bir ada eşleştirmek için tablo eşlemelerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="80cff-127">You can use table mappings to map the automatically generated table name to a name you want specified for the table in the **DataSet**.</span></span> <span data-ttu-id="80cff-128">Örneğin, müşteriler **ve** **siparişler**olmak üzere iki tablo döndüren bir **SelectCommand** için aşağıdaki çağrıyı **Doldur'a**verir.</span><span class="sxs-lookup"><span data-stu-id="80cff-128">For example, for a **SelectCommand** that returns two tables, **Customers** and **Orders**, issue the following call to **Fill**.</span></span>  
  
```vb  
adapter.Fill(customersDataSet, "Customers")  
```  

```csharp  
adapter.Fill(customersDataSet, "Customers");  
```  

 <span data-ttu-id="80cff-129">**DataSet'te**iki tablo oluşturulur: **Müşteriler** ve **Müşteriler1.**</span><span class="sxs-lookup"><span data-stu-id="80cff-129">Two tables are created in the **DataSet**: **Customers** and **Customers1**.</span></span> <span data-ttu-id="80cff-130">İkinci tablonun Müşteriler yerine **Siparişler** olarak adlandırılmasını sağlamak için tablo eşlemelerini **kullanabilirsiniz1.**</span><span class="sxs-lookup"><span data-stu-id="80cff-130">You can use table mappings to ensure that the second table is named **Orders** instead of **Customers1**.</span></span> <span data-ttu-id="80cff-131">Bunu yapmak için, Aşağıdaki örnekte gösterildiği **gibi, Müşteriler1'in** kaynak tablosunu **DataSet** tablo **Siparişleri**ile eşlendirin.</span><span class="sxs-lookup"><span data-stu-id="80cff-131">To do this, map the source table of **Customers1** to the **DataSet** table **Orders**, as shown in the following example.</span></span>  
  
```vb  
adapter.TableMappings.Add("Customers1", "Orders")  
adapter.Fill(customersDataSet, "Customers")  
```  

```csharp  
adapter.TableMappings.Add("Customers1", "Orders");  
adapter.Fill(customersDataSet, "Customers");  
```
  
## <a name="see-also"></a><span data-ttu-id="80cff-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="80cff-132">See also</span></span>

- [<span data-ttu-id="80cff-133">DataAdapters ve DataReaders</span><span class="sxs-lookup"><span data-stu-id="80cff-133">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="80cff-134">ADO.NET’te Veri Alma ve Değiştirme</span><span class="sxs-lookup"><span data-stu-id="80cff-134">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)
- [<span data-ttu-id="80cff-135">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="80cff-135">ADO.NET Overview</span></span>](ado-net-overview.md)
