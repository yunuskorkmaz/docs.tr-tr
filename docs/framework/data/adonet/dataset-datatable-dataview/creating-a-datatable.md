---
title: DataTable Oluşturma
description: Bağımsız olarak veya diğer .NET Framework nesneleri kullanarak, bir bellek içi ilişkisel veri tablosunu temsil eden ADO.NET içinde bir DataTable oluşturmayı öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: eecf9d78-60e3-4fdc-8de0-e56c13a89414
ms.openlocfilehash: 75c9bcf0e0b6180030825b4d1e7dd9e1f9686712
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198645"
---
# <a name="creating-a-datatable"></a><span data-ttu-id="ef25e-103">DataTable Oluşturma</span><span class="sxs-lookup"><span data-stu-id="ef25e-103">Creating a DataTable</span></span>

<span data-ttu-id="ef25e-104">Bir <xref:System.Data.DataTable> bellek içi ilişkisel veri tablosunu temsil eden bir tablosu, bağımsız olarak oluşturulup kullanılabilir veya diğer .NET Framework nesneleri tarafından, genellikle bir üyesi olarak kullanılabilir <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="ef25e-104">A <xref:System.Data.DataTable>, which represents one table of in-memory relational data, can be created and used independently, or can be used by other .NET Framework objects, most commonly as a member of a <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="ef25e-105">Uygun **DataTable** oluşturucusunu kullanarak bir **DataTable** nesnesi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef25e-105">You can create a **DataTable** object by using the appropriate **DataTable** constructor.</span></span> <span data-ttu-id="ef25e-106">Bunu **DataTable** nesnesinin **Tables** koleksiyonuna eklemek Için **Add** metodunu kullanarak **veri kümesine** ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef25e-106">You can add it to the **DataSet** by using the **Add** method to add it to the **DataTable** object's **Tables** collection.</span></span>  
  
 <span data-ttu-id="ef25e-107">Ayrıca, **DataAdapter** nesnesinin **Fill** veya **FillSchema** yöntemlerini **kullanarak veya** **veri kümesinin** **ReadXml**, **ReadXmlSchema**ya da **InferXmlSchema** yöntemlerini kullanarak önceden tanımlanmış veya Çıkarsanan xml şemasından **DataTable** nesneleri de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef25e-107">You can also create **DataTable** objects within a **DataSet** by using the **Fill** or **FillSchema** methods of the **DataAdapter** object, or from a predefined or inferred XML schema using the **ReadXml**, **ReadXmlSchema**, or **InferXmlSchema** methods of the **DataSet**.</span></span> <span data-ttu-id="ef25e-108">Bir **veri kümesinin** **Tables** koleksiyonunun bir üyesi olarak bir **DataTable** ekledikten sonra, bunu başka bir **veri kümesinin**tablo koleksiyonuna ekleyemediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="ef25e-108">Note that after you have added a **DataTable** as a member of the **Tables** collection of one **DataSet**, you cannot add it to the collection of tables of any other **DataSet**.</span></span>  
  
 <span data-ttu-id="ef25e-109">İlk olarak bir **DataTable**oluşturduğunuzda, bir şeması (yani bir yapı) yoktur.</span><span class="sxs-lookup"><span data-stu-id="ef25e-109">When you first create a **DataTable**, it does not have a schema (that is, a structure).</span></span> <span data-ttu-id="ef25e-110">Tablonun şemasını tanımlamak için, nesneleri oluşturmanız ve <xref:System.Data.DataColumn> tablonun **Columns** koleksiyonuna eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ef25e-110">To define the schema of the table, you must create and add <xref:System.Data.DataColumn> objects to the **Columns** collection of the table.</span></span> <span data-ttu-id="ef25e-111">Ayrıca tablo için bir birincil anahtar sütunu tanımlayabilir ve tablonun **kısıtlamalar** koleksiyonuna **kısıtlama** nesneleri oluşturabilir ve ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef25e-111">You can also define a primary key column for the table, and create and add **Constraint** objects to the **Constraints** collection of the table.</span></span> <span data-ttu-id="ef25e-112">Bir **DataTable**şemasını tanımladıktan sonra, tablodaki **satır** koleksiyonuna **DataRow** nesneleri ekleyerek tabloya veri satırları ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef25e-112">After you have defined the schema for a **DataTable**, you can add rows of data to the table by adding **DataRow** objects to the **Rows** collection of the table.</span></span>  
  
 <span data-ttu-id="ef25e-113">DataTable oluştururken özellik için bir değer sağlamanız gerekmez <xref:System.Data.DataTable.TableName%2A> ; özelliği başka bir zaman belirtebilir veya **DataTable**boş bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef25e-113">You are not required to supply a value for the <xref:System.Data.DataTable.TableName%2A> property when you create a **DataTable**; you can specify the property at another time, or you can leave it empty.</span></span> <span data-ttu-id="ef25e-114">Ancak, bir **veri kümesine** **TableName** değeri olmayan bir tablo eklediğinizde, tabloya TABLE0 için "Table" Ile başlayarak, tablo*N*artımlı varsayılan adı verilir.</span><span class="sxs-lookup"><span data-stu-id="ef25e-114">However, when you add a table without a **TableName** value to a **DataSet**, the table will be given an incremental default name of Table*N*, starting with "Table" for Table0.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ef25e-115">Bir **TableName** değeri belirttiğinizde "tablo*N*" adlandırma kuralını önlemenize önerilir, çünkü sağladığınız ad **veri kümesindeki**mevcut bir varsayılan tablo adıyla çakışabilir.</span><span class="sxs-lookup"><span data-stu-id="ef25e-115">We recommend that you avoid the "Table*N*" naming convention when you supply a **TableName** value, because the name you supply may conflict with an existing default table name in the **DataSet**.</span></span> <span data-ttu-id="ef25e-116">Sağlanan ad zaten varsa, bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="ef25e-116">If the supplied name already exists, an exception is thrown.</span></span>  
  
 <span data-ttu-id="ef25e-117">Aşağıdaki örnek, bir **DataTable** nesnesinin örneğini oluşturur ve "Customers" adına atar.</span><span class="sxs-lookup"><span data-stu-id="ef25e-117">The following example creates an instance of a **DataTable** object and assigns it the name "Customers."</span></span>  
  
```vb  
Dim workTable as DataTable = New DataTable("Customers")  
```  
  
```csharp  
DataTable workTable = new DataTable("Customers");  
```  
  
 <span data-ttu-id="ef25e-118">Aşağıdaki örnek, bir **veri kümesinin** **Tables** koleksiyonuna ekleyerek bir **DataTable** örneği oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ef25e-118">The following example creates an instance of a **DataTable** by adding it to the **Tables** collection of a **DataSet**.</span></span>  
  
```vb  
Dim customers As DataSet = New DataSet  
Dim customersTable As DataTable = _  
   customers.Tables.Add("CustomersTable")  
```  
  
```csharp  
DataSet customers = new DataSet();  
DataTable customersTable = customers.Tables.Add("CustomersTable");  
```  
  
## <a name="see-also"></a><span data-ttu-id="ef25e-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ef25e-119">See also</span></span>

- <xref:System.Data.DataTable>
- <xref:System.Data.DataTableCollection>
- [<span data-ttu-id="ef25e-120">DataTables</span><span class="sxs-lookup"><span data-stu-id="ef25e-120">DataTables</span></span>](datatables.md)
- [<span data-ttu-id="ef25e-121">DataAdapter’dan bir DataSet Doldurma</span><span class="sxs-lookup"><span data-stu-id="ef25e-121">Populating a DataSet from a DataAdapter</span></span>](../populating-a-dataset-from-a-dataadapter.md)
- [<span data-ttu-id="ef25e-122">XML’den DataSet Yükleme</span><span class="sxs-lookup"><span data-stu-id="ef25e-122">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="ef25e-123">XML’den DataSet Schema Bilgilerini Yükleme</span><span class="sxs-lookup"><span data-stu-id="ef25e-123">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="ef25e-124">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ef25e-124">ADO.NET Overview</span></span>](../ado-net-overview.md)
