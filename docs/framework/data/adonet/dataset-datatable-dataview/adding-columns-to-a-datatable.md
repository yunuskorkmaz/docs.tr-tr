---
title: Bir DataTable tablosuna sütun ekleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e85c4a0e-4f3f-458c-b58b-0ddbc06bf974
ms.openlocfilehash: 892c0488588e9a5b59650f4a815ba9819493a610
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54538277"
---
# <a name="adding-columns-to-a-datatable"></a><span data-ttu-id="6981a-102">Bir DataTable tablosuna sütun ekleme</span><span class="sxs-lookup"><span data-stu-id="6981a-102">Adding Columns to a DataTable</span></span>
<span data-ttu-id="6981a-103">A <xref:System.Data.DataTable> koleksiyonunu içeren <xref:System.Data.DataColumn> nesneler tarafından başvurulan **sütunları** tablonun özelliği.</span><span class="sxs-lookup"><span data-stu-id="6981a-103">A <xref:System.Data.DataTable> contains a collection of <xref:System.Data.DataColumn> objects referenced by the **Columns** property of the table.</span></span> <span data-ttu-id="6981a-104">Bu sütunlar, kısıtlamalar, birlikte koleksiyonu, şema veya tablonun yapısını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6981a-104">This collection of columns, along with any constraints, defines the schema, or structure, of the table.</span></span>  
  
 <span data-ttu-id="6981a-105">Oluşturduğunuz **DataColumn** kullanarak bir tablo içindeki nesneleri **DataColumn** Oluşturucusu veya çağırarak **Ekle** yöntemi **sütunları**özelliği olan, tablodaki bir <xref:System.Data.DataColumnCollection>.</span><span class="sxs-lookup"><span data-stu-id="6981a-105">You create **DataColumn** objects within a table by using the **DataColumn** constructor, or by calling the **Add** method of the **Columns** property of the table, which is a <xref:System.Data.DataColumnCollection>.</span></span> <span data-ttu-id="6981a-106">**Ekle** yöntemi kabul isteğe bağlı **ColumnName**, **DataType**, ve **ifade** bağımsız değişkenleri ve yeni bir oluşturur  **DataColumn** koleksiyonunun bir üyesi olarak.</span><span class="sxs-lookup"><span data-stu-id="6981a-106">The **Add** method accepts optional **ColumnName**, **DataType**, and **Expression** arguments and creates a new **DataColumn** as a member of the collection.</span></span> <span data-ttu-id="6981a-107">Ayrıca var olan bir kabul **DataColumn** nesne koleksiyonuna ekler ve eklenen bir başvuru döndürür **DataColumn** istenmesi halinde.</span><span class="sxs-lookup"><span data-stu-id="6981a-107">It also accepts an existing **DataColumn** object and adds it to the collection, and returns a reference to the added **DataColumn** if requested.</span></span> <span data-ttu-id="6981a-108">Çünkü **DataTable** nesneler herhangi bir veri kaynağına özgü değildir, .NET Framework türleri veri türü belirtmek için kullanılan bir **DataColumn**.</span><span class="sxs-lookup"><span data-stu-id="6981a-108">Because **DataTable** objects are not specific to any data source, .NET Framework types are used when specifying the data type of a **DataColumn**.</span></span>  
  
 <span data-ttu-id="6981a-109">Aşağıdaki örnek, dört sütun ekler. bir **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="6981a-109">The following example adds four columns to a **DataTable**.</span></span>  
  
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
  
 <span data-ttu-id="6981a-110">Örnekte, dikkat özelliklerini **CustId** sütun izin ayarlanmış **DBNull** değerleri ve değerlerinin benzersiz sınırlamak için.</span><span class="sxs-lookup"><span data-stu-id="6981a-110">In the example, notice that the properties for the **CustID** column are set to not allow **DBNull** values and to constrain values to be unique.</span></span> <span data-ttu-id="6981a-111">Ancak, tanımlarsanız **CustId** sütun tablonun birincil anahtar sütunu olarak **AllowDBNull** özelliği otomatik olarak ayarlanır **false** ve **Benzersiz** özelliği otomatik olarak ayarlanır **true**.</span><span class="sxs-lookup"><span data-stu-id="6981a-111">However, if you define the **CustID** column as the primary key column of the table, the **AllowDBNull** property will automatically be set to **false** and the **Unique** property will automatically be set to **true**.</span></span> <span data-ttu-id="6981a-112">Daha fazla bilgi için [birincil anahtarlar tanımlama](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).</span><span class="sxs-lookup"><span data-stu-id="6981a-112">For more information, see [Defining Primary Keys](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="6981a-113">Bir sütun için bir sütun adı sağlanmazsa, sütun sütununun bir artımlı varsayılan ad verilir*N* "Column1" ile başlayarak, ne zaman eklenir **DataColumnCollection**.</span><span class="sxs-lookup"><span data-stu-id="6981a-113">If a column name is not supplied for a column, the column is given an incremental default name of Column*N,* starting with "Column1", when it is added to the **DataColumnCollection**.</span></span> <span data-ttu-id="6981a-114">Adlandırma kuralı kaçınmanızı öneririz "sütun*N*" adı sağlamanız için ne zaman bir sütun adı sağlayın mevcut bir varsayılan sütun adıyla çakışıyor olabilir **DataColumnCollection**.</span><span class="sxs-lookup"><span data-stu-id="6981a-114">We recommend that you avoid the naming convention of "Column*N*" when you supply a column name, because the name you supply may conflict with an existing default column name in the **DataColumnCollection**.</span></span> <span data-ttu-id="6981a-115">Sağlanan ad zaten varsa, bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6981a-115">If the supplied name already exists, an exception is thrown.</span></span>  
  
 <span data-ttu-id="6981a-116">Kullanıyorsanız <xref:System.Xml.Linq.XElement> olarak <xref:System.Data.DataColumn.DataType%2A> , bir <xref:System.Data.DataColumn> içinde <xref:System.Data.DataTable>, XML serileştirme verilerinde okuduğunuzda çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="6981a-116">If you are using <xref:System.Xml.Linq.XElement> as the <xref:System.Data.DataColumn.DataType%2A> of a <xref:System.Data.DataColumn> in the <xref:System.Data.DataTable>, XML serialization will not work when you read in data.</span></span> <span data-ttu-id="6981a-117">Örneğin, yazma, bir <xref:System.Xml.XmlDocument> kullanarak `DataTable.WriteXml` yöntem, bir ek üst düğümünde yoktur XML serileştirme <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="6981a-117">For example, if you write out a <xref:System.Xml.XmlDocument> by using the `DataTable.WriteXml` method, upon serialization to XML there is an additional parent node in the <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="6981a-118">Bu sorunu geçici olarak çözmek için kullanın <xref:System.Data.SqlTypes.SqlXml> türü yerine <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="6981a-118">To work around this problem, use the <xref:System.Data.SqlTypes.SqlXml> type instead of <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="6981a-119">`ReadXml` ve `WriteXml` ile düzgün çalışmak <xref:System.Data.SqlTypes.SqlXml>.</span><span class="sxs-lookup"><span data-stu-id="6981a-119">`ReadXml` and `WriteXml` work correctly with <xref:System.Data.SqlTypes.SqlXml>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6981a-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6981a-120">See also</span></span>
- <xref:System.Data.DataColumn>
- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="6981a-121">DataTable Şema Tanımı</span><span class="sxs-lookup"><span data-stu-id="6981a-121">DataTable Schema Definition</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)
- [<span data-ttu-id="6981a-122">DataTables</span><span class="sxs-lookup"><span data-stu-id="6981a-122">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)
- [<span data-ttu-id="6981a-123">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="6981a-123">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
