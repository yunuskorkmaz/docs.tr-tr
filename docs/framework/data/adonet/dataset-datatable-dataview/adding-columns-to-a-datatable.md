---
title: "DataTable tablosuna sütun ekleme"
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
ms.assetid: e85c4a0e-4f3f-458c-b58b-0ddbc06bf974
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 6340baa434467ec4ccde501b4bb11d55a72c069b
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="adding-columns-to-a-datatable"></a><span data-ttu-id="b5b9d-102">DataTable tablosuna sütun ekleme</span><span class="sxs-lookup"><span data-stu-id="b5b9d-102">Adding Columns to a DataTable</span></span>
<span data-ttu-id="b5b9d-103">A <xref:System.Data.DataTable> bir koleksiyonu içerir <xref:System.Data.DataColumn> tarafından başvurulan nesneler **sütunları** tablosunun özelliği.</span><span class="sxs-lookup"><span data-stu-id="b5b9d-103">A <xref:System.Data.DataTable> contains a collection of <xref:System.Data.DataColumn> objects referenced by the **Columns** property of the table.</span></span> <span data-ttu-id="b5b9d-104">Tüm kısıtlamaları birlikte sütun bu koleksiyonu şema veya tablo yapısını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b5b9d-104">This collection of columns, along with any constraints, defines the schema, or structure, of the table.</span></span>  
  
 <span data-ttu-id="b5b9d-105">Oluşturduğunuz **DataColumn** kullanarak bir tablo içindeki nesneleri **DataColumn** oluşturucusu, veya çağırarak **Ekle** yöntemi **sütunları**özelliği olan tablonun bir <xref:System.Data.DataColumnCollection>.</span><span class="sxs-lookup"><span data-stu-id="b5b9d-105">You create **DataColumn** objects within a table by using the **DataColumn** constructor, or by calling the **Add** method of the **Columns** property of the table, which is a <xref:System.Data.DataColumnCollection>.</span></span> <span data-ttu-id="b5b9d-106">**Ekle** yöntemi kabul isteğe bağlı **ColumnName**, **DataType**, ve **ifade** bağımsız değişkenleri ve yeni bir  **DataColumn** koleksiyonunun bir üyesi olarak.</span><span class="sxs-lookup"><span data-stu-id="b5b9d-106">The **Add** method accepts optional **ColumnName**, **DataType**, and **Expression** arguments and creates a new **DataColumn** as a member of the collection.</span></span> <span data-ttu-id="b5b9d-107">Ayrıca varolan bir kabul **DataColumn** nesne ve koleksiyona ekler ve eklenen bir başvuru döndürür **DataColumn** istediyseniz.</span><span class="sxs-lookup"><span data-stu-id="b5b9d-107">It also accepts an existing **DataColumn** object and adds it to the collection, and returns a reference to the added **DataColumn** if requested.</span></span> <span data-ttu-id="b5b9d-108">Çünkü **DataTable** nesneleri herhangi bir veri kaynağı için belirli olmayan, .NET Framework türleri veri türünü belirtmek için kullanılan bir **DataColumn**.</span><span class="sxs-lookup"><span data-stu-id="b5b9d-108">Because **DataTable** objects are not specific to any data source, .NET Framework types are used when specifying the data type of a **DataColumn**.</span></span>  
  
 <span data-ttu-id="b5b9d-109">Dört sütun aşağıdaki örnek, bir **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="b5b9d-109">The following example adds four columns to a **DataTable**.</span></span>  
  
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
  
 <span data-ttu-id="b5b9d-110">Örnekte, dikkat özelliklerini **CustId** sütun izin ayarlandığında **DBNull** değerleri ve benzersiz olması için değerleri sınırlamak için.</span><span class="sxs-lookup"><span data-stu-id="b5b9d-110">In the example, notice that the properties for the **CustID** column are set to not allow **DBNull** values and to constrain values to be unique.</span></span> <span data-ttu-id="b5b9d-111">Ancak, tanımlarsanız **CustId** sütunu tablonun birincil anahtar sütunu olarak **AllowDBNull** özelliği otomatik olarak ayarlanacak **false** ve **Benzersiz** özelliği otomatik olarak ayarlanacak **doğru**.</span><span class="sxs-lookup"><span data-stu-id="b5b9d-111">However, if you define the **CustID** column as the primary key column of the table, the **AllowDBNull** property will automatically be set to **false** and the **Unique** property will automatically be set to **true**.</span></span> <span data-ttu-id="b5b9d-112">Daha fazla bilgi için bkz: [tanımlama birincil anahtarlar](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).</span><span class="sxs-lookup"><span data-stu-id="b5b9d-112">For more information, see [Defining Primary Keys](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="b5b9d-113">Bir sütun adı için bir sütun sağlanmazsa, sütun sütunun bir artımlı varsayılan adı verilen*N* "Column1" ile başlayarak, ne zaman eklenir **DataColumnCollection**.</span><span class="sxs-lookup"><span data-stu-id="b5b9d-113">If a column name is not supplied for a column, the column is given an incremental default name of Column*N,* starting with "Column1", when it is added to the **DataColumnCollection**.</span></span> <span data-ttu-id="b5b9d-114">Adlandırma kuralı kaçınmanızı öneririz "sütun*N*" adı sağladığınız çünkü ne zaman bir sütun adı sağlayın mevcut bir varsayılan sütun adıyla çakışıyor olabilir **DataColumnCollection**.</span><span class="sxs-lookup"><span data-stu-id="b5b9d-114">We recommend that you avoid the naming convention of "Column*N*" when you supply a column name, because the name you supply may conflict with an existing default column name in the **DataColumnCollection**.</span></span> <span data-ttu-id="b5b9d-115">Sağlanan adı zaten varsa, özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="b5b9d-115">If the supplied name already exists, an exception is thrown.</span></span>  
  
 <span data-ttu-id="b5b9d-116">Kullanıyorsanız <xref:System.Xml.Linq.XElement> olarak <xref:System.Data.DataColumn.DataType%2A> , bir <xref:System.Data.DataColumn> içinde <xref:System.Data.DataTable>, XML serileştirme verileri okurken çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="b5b9d-116">If you are using <xref:System.Xml.Linq.XElement> as the <xref:System.Data.DataColumn.DataType%2A> of a <xref:System.Data.DataColumn> in the <xref:System.Data.DataTable>, XML serialization will not work when you read in data.</span></span> <span data-ttu-id="b5b9d-117">Örneğin, yazarsanız bir <xref:System.Xml.XmlDocument> kullanarak `DataTable.WriteXml` bir ek üst düğüm XML serileştirme sırasında yöntemi <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="b5b9d-117">For example, if you write out a <xref:System.Xml.XmlDocument> by using the `DataTable.WriteXml` method, upon serialization to XML there is an additional parent node in the <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="b5b9d-118">Bu sorunu geçici olarak çözmek için kullanmak <xref:System.Data.SqlTypes.SqlXml> yerine tür <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="b5b9d-118">To work around this problem, use the <xref:System.Data.SqlTypes.SqlXml> type instead of <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="b5b9d-119">`ReadXml`ve `WriteXml` düzgün şekilde iş <xref:System.Data.SqlTypes.SqlXml>.</span><span class="sxs-lookup"><span data-stu-id="b5b9d-119">`ReadXml` and `WriteXml` work correctly with <xref:System.Data.SqlTypes.SqlXml>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5b9d-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b5b9d-120">See Also</span></span>  
 <xref:System.Data.DataColumn>  
 <xref:System.Data.DataColumnCollection>  
 <xref:System.Data.DataTable>  
 [<span data-ttu-id="b5b9d-121">DataTable Şema Tanımı</span><span class="sxs-lookup"><span data-stu-id="b5b9d-121">DataTable Schema Definition</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 [<span data-ttu-id="b5b9d-122">DataTables</span><span class="sxs-lookup"><span data-stu-id="b5b9d-122">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [<span data-ttu-id="b5b9d-123">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="b5b9d-123">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
