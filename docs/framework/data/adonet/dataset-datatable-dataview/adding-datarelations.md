---
title: DataRelations Ekleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a4a564fb-c1c4-4135-b6c2-b030e51195e4
ms.openlocfilehash: 9cefc97e571f315a6a644e0a058d4283168ecb9f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62034529"
---
# <a name="adding-datarelations"></a><span data-ttu-id="b0db9-102">DataRelations Ekleme</span><span class="sxs-lookup"><span data-stu-id="b0db9-102">Adding DataRelations</span></span>
<span data-ttu-id="b0db9-103">İçinde bir <xref:System.Data.DataSet> birden çok <xref:System.Data.DataTable> nesnelerini kullanabileceğiniz <xref:System.Data.DataRelation> diğerine tabloları gidin ve ilişkili tablodan alt veya üst satırlar döndürülecek bir tablo ilişkilendirmek için nesneleri.</span><span class="sxs-lookup"><span data-stu-id="b0db9-103">In a <xref:System.Data.DataSet> with multiple <xref:System.Data.DataTable> objects, you can use <xref:System.Data.DataRelation> objects to relate one table to another, to navigate through the tables, and to return child or parent rows from a related table.</span></span>  
  
 <span data-ttu-id="b0db9-104">Oluşturmak için gereken bağımsız değişkenler bir **DataRelation** için bir adı olan **DataRelation** oluşturulan ve bir dizi veya birden fazla <xref:System.Data.DataColumn> üst ve alt hizmet sütunlara yönelik başvurulara İlişki sütun.</span><span class="sxs-lookup"><span data-stu-id="b0db9-104">The arguments required to create a **DataRelation** are a name for the **DataRelation** being created, and an array of one or more <xref:System.Data.DataColumn> references to the columns that serve as the parent and child columns in the relationship.</span></span> <span data-ttu-id="b0db9-105">Oluşturduktan sonra bir **DataRelation**, tablolar arasında gezinmek için ve değerleri almak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b0db9-105">After you have created a **DataRelation**, you can use it to navigate between tables and to retrieve values.</span></span>  
  
 <span data-ttu-id="b0db9-106">Ekleme bir **DataRelation** için bir <xref:System.Data.DataSet> ekler, varsayılan olarak, bir <xref:System.Data.UniqueConstraint> üst tabloya ve <xref:System.Data.ForeignKeyConstraint> alt tablo için.</span><span class="sxs-lookup"><span data-stu-id="b0db9-106">Adding a **DataRelation** to a <xref:System.Data.DataSet> adds, by default, a <xref:System.Data.UniqueConstraint> to the parent table and a <xref:System.Data.ForeignKeyConstraint> to the child table.</span></span> <span data-ttu-id="b0db9-107">Bu varsayılan kısıtlamaları hakkında daha fazla bilgi için bkz: [DataTable kısıtlamaları](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md).</span><span class="sxs-lookup"><span data-stu-id="b0db9-107">For more information about these default constraints, see [DataTable Constraints](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md).</span></span>  
  
 <span data-ttu-id="b0db9-108">Aşağıdaki kod örneği oluşturur bir **DataRelation** iki kullanarak <xref:System.Data.DataTable> nesneler bir <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="b0db9-108">The following code example creates a **DataRelation** using two <xref:System.Data.DataTable> objects in a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="b0db9-109">Her <xref:System.Data.DataTable> adlı bir sütun içeren **CustId**, ikisi arasında bir bağlantı olarak görev gören <xref:System.Data.DataTable> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="b0db9-109">Each <xref:System.Data.DataTable> contains a column named **CustID**, which serves as a link between the two <xref:System.Data.DataTable> objects.</span></span> <span data-ttu-id="b0db9-110">Tek bir örnek ekler **DataRelation** için **ilişkileri** koleksiyonunu <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="b0db9-110">The example adds a single **DataRelation** to the **Relations** collection of the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="b0db9-111">Örnekteki ilk bağımsız değişken adını belirten **DataRelation** oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="b0db9-111">The first argument in the example specifies the name of the **DataRelation** being created.</span></span> <span data-ttu-id="b0db9-112">İkinci bağımsız değişkeni üst ayarlar **DataColumn** ve üçüncü bağımsız değişken alt ayarlar **DataColumn**.</span><span class="sxs-lookup"><span data-stu-id="b0db9-112">The second argument sets the parent **DataColumn** and the third argument sets the child **DataColumn**.</span></span>  
  
```vb  
customerOrders.Relations.Add("CustOrders", _  
  customerOrders.Tables("Customers").Columns("CustID"), _  
  customerOrders.Tables("Orders").Columns("CustID"))  
```  
  
```csharp  
customerOrders.Relations.Add("CustOrders",  
  customerOrders.Tables["Customers"].Columns["CustID"],  
  customerOrders.Tables["Orders"].Columns["CustID"]);  
```  
  
 <span data-ttu-id="b0db9-113">A **DataRelation** de sahip bir **iç içe** özelliği, ayarlandığında **true**, üst tablodan ilgili satır içinde iç içe alt tablosundan satırları neden olur XML öğeleri kullanarak yazılırken <xref:System.Data.DataSet.WriteXml%2A> .</span><span class="sxs-lookup"><span data-stu-id="b0db9-113">A **DataRelation** also has a **Nested** property which, when set to **true**, causes the rows from the child table to be nested within the associated row from the parent table when written as XML elements using <xref:System.Data.DataSet.WriteXml%2A> .</span></span> <span data-ttu-id="b0db9-114">Daha fazla bilgi için [kullanarak bir veri kümesi XML'de](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="b0db9-114">For more information, see [Using XML in a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0db9-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b0db9-115">See also</span></span>

- [<span data-ttu-id="b0db9-116">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="b0db9-116">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [<span data-ttu-id="b0db9-117">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="b0db9-117">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
