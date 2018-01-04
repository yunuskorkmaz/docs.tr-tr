---
title: "DataTable oluşturma"
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
ms.assetid: eecf9d78-60e3-4fdc-8de0-e56c13a89414
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 68f8272aa0f525c04120f129057e6151e42ffee1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="creating-a-datatable"></a><span data-ttu-id="84188-102">DataTable oluşturma</span><span class="sxs-lookup"><span data-stu-id="84188-102">Creating a DataTable</span></span>
<span data-ttu-id="84188-103">A <xref:System.Data.DataTable>, bellek içi ilişkisel veriyi, bir tablo temsil eden olabilir oluşturulan ve bağımsız olarak kullanılan ya da diğer .NET Framework nesneleri tarafından yaygın bir üyesi olarak kullanılabilir bir <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="84188-103">A <xref:System.Data.DataTable>, which represents one table of in-memory relational data, can be created and used independently, or can be used by other .NET Framework objects, most commonly as a member of a <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="84188-104">Oluşturabileceğiniz bir **DataTable** uygun kullanarak nesne **DataTable** Oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="84188-104">You can create a **DataTable** object by using the appropriate **DataTable** constructor.</span></span> <span data-ttu-id="84188-105">Ona ekleyebilirsiniz **DataSet** kullanarak **Ekle** eklemek için yöntemi **DataTable** nesnenin **tabloları** koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="84188-105">You can add it to the **DataSet** by using the **Add** method to add it to the **DataTable** object's **Tables** collection.</span></span>  
  
 <span data-ttu-id="84188-106">Oluşturabilirsiniz **DataTable** içindeki nesneleri bir **DataSet** kullanarak **doldurun** veya **FillSchema** yöntemleri  **DataAdapter** nesnesi veya önceden tanımlanmış veya oluşturulursa XML şeması kullanarak bir **ReadXml**, **ReadXmlSchema**, veya **InferXmlSchema** yöntemlerinin **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="84188-106">You can also create **DataTable** objects within a **DataSet** by using the **Fill** or **FillSchema** methods of the **DataAdapter** object, or from a predefined or inferred XML schema using the **ReadXml**, **ReadXmlSchema**, or **InferXmlSchema** methods of the **DataSet**.</span></span> <span data-ttu-id="84188-107">Ekledikten sonra unutmayın bir **DataTable** bir üyesi olarak **tabloları** bir koleksiyonunu **DataSet**, diğer tablolarıkoleksiyonunaeklenemez**DataSet**.</span><span class="sxs-lookup"><span data-stu-id="84188-107">Note that after you have added a **DataTable** as a member of the **Tables** collection of one **DataSet**, you cannot add it to the collection of tables of any other **DataSet**.</span></span>  
  
 <span data-ttu-id="84188-108">İlk oluşturduğunuzda bir **DataTable**, bir şema (diğer bir deyişle, bir yapı) yok.</span><span class="sxs-lookup"><span data-stu-id="84188-108">When you first create a **DataTable**, it does not have a schema (that is, a structure).</span></span> <span data-ttu-id="84188-109">Tablonun şeması tanımlamak için Oluştur ekleyin ve gerekir <xref:System.Data.DataColumn> nesneleri **sütunları** tablo koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="84188-109">To define the schema of the table, you must create and add <xref:System.Data.DataColumn> objects to the **Columns** collection of the table.</span></span> <span data-ttu-id="84188-110">Ayrıca tablosu için birincil anahtar sütunu tanımlayın ve oluşturun ve eklemek **kısıtlaması** nesneleri **kısıtlamaları** tablo koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="84188-110">You can also define a primary key column for the table, and create and add **Constraint** objects to the **Constraints** collection of the table.</span></span> <span data-ttu-id="84188-111">İçin şemayı tanımladıktan sonra bir **DataTable**, ekleyerek tabloya veri satırı ekleyebilirsiniz **DataRow** nesneleri **satırları** tablo koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="84188-111">After you have defined the schema for a **DataTable**, you can add rows of data to the table by adding **DataRow** objects to the **Rows** collection of the table.</span></span>  
  
 <span data-ttu-id="84188-112">İçin bir değer sağlamanız gerekmez <xref:System.Data.DataTable.TableName%2A> oluşturduğunuzda özelliği bir **DataTable**; başka bir zamanda özelliği belirtebilirsiniz veya boş bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="84188-112">You are not required to supply a value for the <xref:System.Data.DataTable.TableName%2A> property when you create a **DataTable**; you can specify the property at another time, or you can leave it empty.</span></span> <span data-ttu-id="84188-113">Ancak, olmayan bir tablo eklediğinizde bir **TableName** değeri bir **DataSet**, tabloyu tablonun artımlı varsayılan adı verilen*N*Table0 için "Tablo" ile başlayan.</span><span class="sxs-lookup"><span data-stu-id="84188-113">However, when you add a table without a **TableName** value to a **DataSet**, the table will be given an incremental default name of Table*N*, starting with "Table" for Table0.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="84188-114">Kaçınmanızı öneririz "tablo*N*" sağladığınız zaman adlandırma bir **TableName** değer sağladığınız ad içinde varolan bir varsayılan tablo adı ile çakışıyor olabilir çünkü **veri kümesi** .</span><span class="sxs-lookup"><span data-stu-id="84188-114">We recommend that you avoid the "Table*N*" naming convention when you supply a **TableName** value, because the name you supply may conflict with an existing default table name in the **DataSet**.</span></span> <span data-ttu-id="84188-115">Sağlanan adı zaten varsa, özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="84188-115">If the supplied name already exists, an exception is thrown.</span></span>  
  
 <span data-ttu-id="84188-116">Aşağıdaki örnek, bir örneğini oluşturur. bir **DataTable** nesnesi ve "Müşteri" adı atar</span><span class="sxs-lookup"><span data-stu-id="84188-116">The following example creates an instance of a **DataTable** object and assigns it the name "Customers."</span></span>  
  
```vb  
Dim workTable as DataTable = New DataTable("Customers")  
```  
  
```csharp  
DataTable workTable = new DataTable("Customers");  
```  
  
 <span data-ttu-id="84188-117">Aşağıdaki örnek, bir örneğini oluşturur. bir **DataTable** ekleyerek **tabloları** koleksiyonu bir **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="84188-117">The following example creates an instance of a **DataTable** by adding it to the **Tables** collection of a **DataSet**.</span></span>  
  
```vb  
Dim customers As DataSet = New DataSet  
Dim customersTable As DataTable = _  
   customers.Tables.Add("CustomersTable")  
```  
  
```csharp  
DataSet customers = new DataSet();  
DataTable customersTable = customers.Tables.Add("CustomersTable");  
```  
  
## <a name="see-also"></a><span data-ttu-id="84188-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="84188-118">See Also</span></span>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataTableCollection>  
 [<span data-ttu-id="84188-119">DataTables</span><span class="sxs-lookup"><span data-stu-id="84188-119">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [<span data-ttu-id="84188-120">DataAdapter’dan bir DataSet Doldurma</span><span class="sxs-lookup"><span data-stu-id="84188-120">Populating a DataSet from a DataAdapter</span></span>](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)  
 [<span data-ttu-id="84188-121">XML’den DataSet Yükleme</span><span class="sxs-lookup"><span data-stu-id="84188-121">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [<span data-ttu-id="84188-122">XML’den DataSet Schema Bilgilerini Yükleme</span><span class="sxs-lookup"><span data-stu-id="84188-122">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [<span data-ttu-id="84188-123">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="84188-123">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
