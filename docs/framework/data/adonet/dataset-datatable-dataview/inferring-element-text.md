---
title: Öğe Metni Çıkarımını Yapma
ms.date: 03/30/2017
ms.assetid: 789799e5-716f-459f-a168-76c5cf22178b
ms.openlocfilehash: 6ffe8f2fbf01fbe8dfa9d78f3dfb9e39b6e80b16
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61879638"
---
# <a name="inferring-element-text"></a><span data-ttu-id="1d24d-102">Öğe Metni Çıkarımını Yapma</span><span class="sxs-lookup"><span data-stu-id="1d24d-102">Inferring Element Text</span></span>
<span data-ttu-id="1d24d-103">Bir öğenin metni içeren ve yeni bir sütun adıyla (öznitelikleri olan öğe) veya yinelenen öğeler gibi tablolar olarak çıkarılan için alt öğe yok **TableName_Text** öğe için ortaya çıkan tablosuna eklenir.</span><span class="sxs-lookup"><span data-stu-id="1d24d-103">If an element contains text and has no child elements to be inferred as tables (such as elements with attributes or repeated elements), a new column with the name **TableName_Text** will be added to the table that is inferred for the element.</span></span> <span data-ttu-id="1d24d-104">Öğesinde bulunan metin tablosunda bir satıra eklenir ve yeni bir sütun depolanır.</span><span class="sxs-lookup"><span data-stu-id="1d24d-104">The text contained in the element will be added to a row in the table and stored in the new column.</span></span> <span data-ttu-id="1d24d-105">**Columnmapping'in** yeni sütunun özellik ayarlanacak **MappingType.SimpleContent**.</span><span class="sxs-lookup"><span data-stu-id="1d24d-105">The **ColumnMapping** property of the new column will be set to **MappingType.SimpleContent**.</span></span>  
  
 <span data-ttu-id="1d24d-106">Örneğin, aşağıdaki XML göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="1d24d-106">For example, consider the following XML.</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1">Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="1d24d-107">Çıkarma işlemi adlı bir tablo oluşturur **Element1** iki sütunlu: **attr1** ve **Element1_Text**.</span><span class="sxs-lookup"><span data-stu-id="1d24d-107">The inference process will produce a table named **Element1** with two columns: **attr1** and **Element1_Text**.</span></span> <span data-ttu-id="1d24d-108">**Columnmapping'in** özelliği **attr1** sütun ayarlanacak **MappingType.Attribute**.</span><span class="sxs-lookup"><span data-stu-id="1d24d-108">The **ColumnMapping** property of the **attr1** column will be set to **MappingType.Attribute**.</span></span> <span data-ttu-id="1d24d-109">**Columnmapping'in** özelliği **Element1_Text** sütun ayarlanacak **MappingType.SimpleContent**.</span><span class="sxs-lookup"><span data-stu-id="1d24d-109">The **ColumnMapping** property of the **Element1_Text** column will be set to **MappingType.SimpleContent**.</span></span>  
  
 <span data-ttu-id="1d24d-110">**Veri kümesi:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="1d24d-110">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="1d24d-111">**Tablo:** Element1</span><span class="sxs-lookup"><span data-stu-id="1d24d-111">**Table:** Element1</span></span>  
  
|<span data-ttu-id="1d24d-112">attr1</span><span class="sxs-lookup"><span data-stu-id="1d24d-112">attr1</span></span>|<span data-ttu-id="1d24d-113">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="1d24d-113">Element1_Text</span></span>|  
|-----------|--------------------|  
|<span data-ttu-id="1d24d-114">Değer1</span><span class="sxs-lookup"><span data-stu-id="1d24d-114">value1</span></span>|<span data-ttu-id="1d24d-115">text1</span><span class="sxs-lookup"><span data-stu-id="1d24d-115">Text1</span></span>|  
  
 <span data-ttu-id="1d24d-116">Bir öğenin metin içeriyor, ancak metin içeren alt öğeler de vardır, bir sütun öğesinde bulunan metin depolamaya yönelik tablo eklenmeyecek.</span><span class="sxs-lookup"><span data-stu-id="1d24d-116">If an element contains text, but also has child elements that contain text, a column will not be added to the table to store the text contained in the element.</span></span> <span data-ttu-id="1d24d-117">Alt öğeleri metinde tablosunda bir satıra dahil ederken öğesinde bulunan metin yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="1d24d-117">The text contained in the element will be ignored, while the text in the child elements is included in a row in the table.</span></span> <span data-ttu-id="1d24d-118">Örneğin, aşağıdaki XML göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="1d24d-118">For example, consider the following XML.</span></span>  
  
```xml  
<Element1>  
  Text1  
  <ChildElement1>Text2</ChildElement1>  
  Text3  
</Element1>  
```  
  
 <span data-ttu-id="1d24d-119">Çıkarma işlemi adlı bir tablo oluşturur **Element1** adlı tek bir sütunu **ChildElement1**.</span><span class="sxs-lookup"><span data-stu-id="1d24d-119">The inference process will produce a table named **Element1** with one column named **ChildElement1**.</span></span> <span data-ttu-id="1d24d-120">Metni **ChildElement1** öğesi dahil edilecek tablosundaki bir satır.</span><span class="sxs-lookup"><span data-stu-id="1d24d-120">The text for the **ChildElement1** element will be included in a row in the table.</span></span> <span data-ttu-id="1d24d-121">Diğer metin göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="1d24d-121">The other text will be ignored.</span></span> <span data-ttu-id="1d24d-122">**Columnmapping'in** özelliği **ChildElement1** sütun ayarlanacak **MappingType.Element**.</span><span class="sxs-lookup"><span data-stu-id="1d24d-122">The **ColumnMapping** property of the **ChildElement1** column will be set to **MappingType.Element**.</span></span>  
  
 <span data-ttu-id="1d24d-123">**Veri kümesi:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="1d24d-123">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="1d24d-124">**Tablo:** Element1</span><span class="sxs-lookup"><span data-stu-id="1d24d-124">**Table:** Element1</span></span>  
  
|<span data-ttu-id="1d24d-125">ChildElement1</span><span class="sxs-lookup"><span data-stu-id="1d24d-125">ChildElement1</span></span>|  
|-------------------|  
|<span data-ttu-id="1d24d-126">Text2</span><span class="sxs-lookup"><span data-stu-id="1d24d-126">Text2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1d24d-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1d24d-127">See also</span></span>

- [<span data-ttu-id="1d24d-128">XML’den DataSet İlişkisel Yapısını Çıkarma</span><span class="sxs-lookup"><span data-stu-id="1d24d-128">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="1d24d-129">XML’den DataSet Yükleme</span><span class="sxs-lookup"><span data-stu-id="1d24d-129">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)
- [<span data-ttu-id="1d24d-130">XML’den DataSet Schema Bilgilerini Yükleme</span><span class="sxs-lookup"><span data-stu-id="1d24d-130">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="1d24d-131">DataSet içinde XML kullanma</span><span class="sxs-lookup"><span data-stu-id="1d24d-131">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
- [<span data-ttu-id="1d24d-132">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="1d24d-132">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [<span data-ttu-id="1d24d-133">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="1d24d-133">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
