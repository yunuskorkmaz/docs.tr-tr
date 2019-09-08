---
title: DataRelations Ekleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a4a564fb-c1c4-4135-b6c2-b030e51195e4
ms.openlocfilehash: 8157d296636d0f8661a35af35de561f5cc49c30b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784814"
---
# <a name="adding-datarelations"></a><span data-ttu-id="ab6ff-102">DataRelations Ekleme</span><span class="sxs-lookup"><span data-stu-id="ab6ff-102">Adding DataRelations</span></span>
<span data-ttu-id="ab6ff-103">Birden çok <xref:System.Data.DataSet> <xref:System.Data.DataTable> nesne ile, bir tabloyu başka bir <xref:System.Data.DataRelation> tabloyla ilişkilendirmek, tablolar arasında gezinmek ve ilişkili bir tablodan alt veya üst satırları döndürmek için nesneleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ab6ff-103">In a <xref:System.Data.DataSet> with multiple <xref:System.Data.DataTable> objects, you can use <xref:System.Data.DataRelation> objects to relate one table to another, to navigate through the tables, and to return child or parent rows from a related table.</span></span>  
  
 <span data-ttu-id="ab6ff-104">Bir **DataRelation** oluşturmak için gereken bağımsız değişkenler, oluşturulmakta olan **DataRelation** için bir addır ve ilişkide üst ve alt sütunları olarak işlev gösteren <xref:System.Data.DataColumn> sütunlara bir veya daha fazla başvuru dizisi.</span><span class="sxs-lookup"><span data-stu-id="ab6ff-104">The arguments required to create a **DataRelation** are a name for the **DataRelation** being created, and an array of one or more <xref:System.Data.DataColumn> references to the columns that serve as the parent and child columns in the relationship.</span></span> <span data-ttu-id="ab6ff-105">Bir **DataRelation**oluşturduktan sonra, tablolar arasında gezinmek ve değerleri almak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ab6ff-105">After you have created a **DataRelation**, you can use it to navigate between tables and to retrieve values.</span></span>  
  
 <span data-ttu-id="ab6ff-106">' A bir **DataRelation** <xref:System.Data.DataSet> eklemek, varsayılan olarak bir <xref:System.Data.UniqueConstraint> üst tabloya ve <xref:System.Data.ForeignKeyConstraint> alt tablosuna bir ekler.</span><span class="sxs-lookup"><span data-stu-id="ab6ff-106">Adding a **DataRelation** to a <xref:System.Data.DataSet> adds, by default, a <xref:System.Data.UniqueConstraint> to the parent table and a <xref:System.Data.ForeignKeyConstraint> to the child table.</span></span> <span data-ttu-id="ab6ff-107">Bu varsayılan kısıtlamalar hakkında daha fazla bilgi için bkz. [DataTable kısıtlamaları](datatable-constraints.md).</span><span class="sxs-lookup"><span data-stu-id="ab6ff-107">For more information about these default constraints, see [DataTable Constraints](datatable-constraints.md).</span></span>  
  
 <span data-ttu-id="ab6ff-108">Aşağıdaki kod örneği, bir <xref:System.Data.DataSet>içinde iki <xref:System.Data.DataTable> nesne kullanarak bir DataRelation oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ab6ff-108">The following code example creates a **DataRelation** using two <xref:System.Data.DataTable> objects in a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="ab6ff-109">Her <xref:System.Data.DataTable> biri, iki <xref:System.Data.DataTable> nesne arasında bağlantı görevi gören **CustId**adlı bir sütun içerir.</span><span class="sxs-lookup"><span data-stu-id="ab6ff-109">Each <xref:System.Data.DataTable> contains a column named **CustID**, which serves as a link between the two <xref:System.Data.DataTable> objects.</span></span> <span data-ttu-id="ab6ff-110">Örnek, <xref:System.Data.DataSet>ilişki koleksiyonuna tek bir **DataRelation** ekler.</span><span class="sxs-lookup"><span data-stu-id="ab6ff-110">The example adds a single **DataRelation** to the **Relations** collection of the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="ab6ff-111">Örnekteki ilk bağımsız değişken, oluşturulmakta olan **DataRelation** 'ın adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ab6ff-111">The first argument in the example specifies the name of the **DataRelation** being created.</span></span> <span data-ttu-id="ab6ff-112">İkinci bağımsız değişken üst **DataColumn** ' i ayarlar ve üçüncü bağımsız değişken alt **DataColumn**' i ayarlar.</span><span class="sxs-lookup"><span data-stu-id="ab6ff-112">The second argument sets the parent **DataColumn** and the third argument sets the child **DataColumn**.</span></span>  
  
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
  
 <span data-ttu-id="ab6ff-113">Bir **DataRelation** Ayrıca, **true**olarak ayarlandığında, alt TABLODAKI satırların, kullanılarak <xref:System.Data.DataSet.WriteXml%2A> XML öğeleri olarak yazıldığında üst tablodaki iç içe olmasına neden olan **iç içe** bir özelliği vardır.</span><span class="sxs-lookup"><span data-stu-id="ab6ff-113">A **DataRelation** also has a **Nested** property which, when set to **true**, causes the rows from the child table to be nested within the associated row from the parent table when written as XML elements using <xref:System.Data.DataSet.WriteXml%2A> .</span></span> <span data-ttu-id="ab6ff-114">Daha fazla bilgi için bkz. [veri KÜMESINDE XML kullanma](using-xml-in-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="ab6ff-114">For more information, see [Using XML in a DataSet](using-xml-in-a-dataset.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab6ff-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ab6ff-115">See also</span></span>

- [<span data-ttu-id="ab6ff-116">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="ab6ff-116">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="ab6ff-117">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ab6ff-117">ADO.NET Overview</span></span>](../ado-net-overview.md)
