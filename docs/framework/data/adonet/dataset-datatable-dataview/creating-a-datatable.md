---
title: DataTable oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: eecf9d78-60e3-4fdc-8de0-e56c13a89414
ms.openlocfilehash: ad3f8bc6b42c5a54b42100a5d010e097ba80adc2
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43521139"
---
# <a name="creating-a-datatable"></a><span data-ttu-id="14a5f-102">DataTable oluşturma</span><span class="sxs-lookup"><span data-stu-id="14a5f-102">Creating a DataTable</span></span>
<span data-ttu-id="14a5f-103">A <xref:System.Data.DataTable>, bellek içi ilişkisel verileri bir tablo temsil eden olabilir oluşturulan ve bağımsız olarak kullanılan veya diğer .NET Framework nesneleri tarafından en yaygın bir üyesi olarak kullanılabilir bir <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="14a5f-103">A <xref:System.Data.DataTable>, which represents one table of in-memory relational data, can be created and used independently, or can be used by other .NET Framework objects, most commonly as a member of a <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="14a5f-104">Oluşturabileceğiniz bir **DataTable** uygun kullanarak nesne **DataTable** Oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="14a5f-104">You can create a **DataTable** object by using the appropriate **DataTable** constructor.</span></span> <span data-ttu-id="14a5f-105">Kendisine ekleyebilirsiniz **veri kümesi** kullanarak **Ekle** eklemek üzere yöntemi **DataTable** nesnenin **tabloları** koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="14a5f-105">You can add it to the **DataSet** by using the **Add** method to add it to the **DataTable** object's **Tables** collection.</span></span>  
  
 <span data-ttu-id="14a5f-106">Oluşturabilirsiniz **DataTable** içindeki nesneleri bir **veri kümesi** kullanarak **dolgu** veya **FillSchema** yöntemlerinin  **DataAdapter** nesnesi veya bir önceden tanımlanmış veya çıkarsanan XML şeması kullanarak **ReadXml**, **ReadXmlSchema**, veya **InferXmlSchema** yöntemlerinin **veri kümesi**.</span><span class="sxs-lookup"><span data-stu-id="14a5f-106">You can also create **DataTable** objects within a **DataSet** by using the **Fill** or **FillSchema** methods of the **DataAdapter** object, or from a predefined or inferred XML schema using the **ReadXml**, **ReadXmlSchema**, or **InferXmlSchema** methods of the **DataSet**.</span></span> <span data-ttu-id="14a5f-107">Ekledikten sonra dikkat bir **DataTable** üyesi olarak **tabloları** bir koleksiyonunu **veri kümesi**, diğer bir tablolarıkoleksiyonunaeklenemiyor**Veri kümesi**.</span><span class="sxs-lookup"><span data-stu-id="14a5f-107">Note that after you have added a **DataTable** as a member of the **Tables** collection of one **DataSet**, you cannot add it to the collection of tables of any other **DataSet**.</span></span>  
  
 <span data-ttu-id="14a5f-108">İlk oluşturduğunuzda bir **DataTable**, (diğer bir deyişle, bir yapı) bir şema yok.</span><span class="sxs-lookup"><span data-stu-id="14a5f-108">When you first create a **DataTable**, it does not have a schema (that is, a structure).</span></span> <span data-ttu-id="14a5f-109">Tablo şemasını tanımlamak için oluşturma ekleyin ve gerekir <xref:System.Data.DataColumn> nesneleri için **sütunları** tablo koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="14a5f-109">To define the schema of the table, you must create and add <xref:System.Data.DataColumn> objects to the **Columns** collection of the table.</span></span> <span data-ttu-id="14a5f-110">Ayrıca tablosu için birincil anahtar sütunu tanımlamak ve oluşturma ve ekleme **kısıtlaması** nesneleri için **kısıtlamaları** tablo koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="14a5f-110">You can also define a primary key column for the table, and create and add **Constraint** objects to the **Constraints** collection of the table.</span></span> <span data-ttu-id="14a5f-111">İçin şemayı tanımladıktan sonra bir **DataTable**, ekleyerek tabloya veri satırı ekleyebilirsiniz **DataRow** nesneleri için **satırları** tablo koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="14a5f-111">After you have defined the schema for a **DataTable**, you can add rows of data to the table by adding **DataRow** objects to the **Rows** collection of the table.</span></span>  
  
 <span data-ttu-id="14a5f-112">İçin bir değer sağlamanız gerekmez <xref:System.Data.DataTable.TableName%2A> oluşturduğunuzda özelliği bir **DataTable**; özelliği başka bir zaman belirtebilirsiniz ya da bölmeyi boş bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="14a5f-112">You are not required to supply a value for the <xref:System.Data.DataTable.TableName%2A> property when you create a **DataTable**; you can specify the property at another time, or you can leave it empty.</span></span> <span data-ttu-id="14a5f-113">Ancak, bir tablo olmadan eklediğinizde bir **TableName** değerini bir **veri kümesi**, tablonun tablosunun bir artımlı varsayılan adı verilir*N*Table0 için "Tablo" ile başlayan.</span><span class="sxs-lookup"><span data-stu-id="14a5f-113">However, when you add a table without a **TableName** value to a **DataSet**, the table will be given an incremental default name of Table*N*, starting with "Table" for Table0.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="14a5f-114">Kaçınmanızı öneririz "tablo*N*" sağladığınız olduğunda adlandırma kuralı bir **TableName** sağladığınız ad mevcut bir varsayılan tablo adı ile çakışıyor çünkü değer **veri kümesi** .</span><span class="sxs-lookup"><span data-stu-id="14a5f-114">We recommend that you avoid the "Table*N*" naming convention when you supply a **TableName** value, because the name you supply may conflict with an existing default table name in the **DataSet**.</span></span> <span data-ttu-id="14a5f-115">Sağlanan ad zaten varsa, bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="14a5f-115">If the supplied name already exists, an exception is thrown.</span></span>  
  
 <span data-ttu-id="14a5f-116">Aşağıdaki örnek, bir örneğini oluşturur. bir **DataTable** nesnesi ve "Müşteri" adı atar</span><span class="sxs-lookup"><span data-stu-id="14a5f-116">The following example creates an instance of a **DataTable** object and assigns it the name "Customers."</span></span>  
  
```vb  
Dim workTable as DataTable = New DataTable("Customers")  
```  
  
```csharp  
DataTable workTable = new DataTable("Customers");  
```  
  
 <span data-ttu-id="14a5f-117">Aşağıdaki örnek, bir örneğini oluşturur. bir **DataTable** ekleyerek **tabloları** koleksiyonunu bir **veri kümesi**.</span><span class="sxs-lookup"><span data-stu-id="14a5f-117">The following example creates an instance of a **DataTable** by adding it to the **Tables** collection of a **DataSet**.</span></span>  
  
```vb  
Dim customers As DataSet = New DataSet  
Dim customersTable As DataTable = _  
   customers.Tables.Add("CustomersTable")  
```  
  
```csharp  
DataSet customers = new DataSet();  
DataTable customersTable = customers.Tables.Add("CustomersTable");  
```  
  
## <a name="see-also"></a><span data-ttu-id="14a5f-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="14a5f-118">See Also</span></span>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataTableCollection>  
 [<span data-ttu-id="14a5f-119">DataTables</span><span class="sxs-lookup"><span data-stu-id="14a5f-119">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [<span data-ttu-id="14a5f-120">DataAdapter’dan bir DataSet Doldurma</span><span class="sxs-lookup"><span data-stu-id="14a5f-120">Populating a DataSet from a DataAdapter</span></span>](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)  
 [<span data-ttu-id="14a5f-121">XML’den DataSet Yükleme</span><span class="sxs-lookup"><span data-stu-id="14a5f-121">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [<span data-ttu-id="14a5f-122">XML’den DataSet Schema Bilgilerini Yükleme</span><span class="sxs-lookup"><span data-stu-id="14a5f-122">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [<span data-ttu-id="14a5f-123">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="14a5f-123">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
