---
title: "Öğe metni çıkarımını yapma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 789799e5-716f-459f-a168-76c5cf22178b
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 66dcc6a98d365f20da6c7f4c075c2fdd8ab936e2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="inferring-element-text"></a><span data-ttu-id="9aacf-102">Öğe metni çıkarımını yapma</span><span class="sxs-lookup"><span data-stu-id="9aacf-102">Inferring Element Text</span></span>
<span data-ttu-id="9aacf-103">Bir öğenin metni içeren ve (öznitelikleri öğeleriyle) veya yinelenen öğeleri gibi yeni bir sütun adıyla tabloları gibi olayla için alt öğe varsa **TableName_Text** öğe için olayla tablosuna eklenir.</span><span class="sxs-lookup"><span data-stu-id="9aacf-103">If an element contains text and has no child elements to be inferred as tables (such as elements with attributes or repeated elements), a new column with the name **TableName_Text** will be added to the table that is inferred for the element.</span></span> <span data-ttu-id="9aacf-104">Öğesinde bulunan metin tablosunda bir satırı eklenir ve yeni bir sütun depolanır.</span><span class="sxs-lookup"><span data-stu-id="9aacf-104">The text contained in the element will be added to a row in the table and stored in the new column.</span></span> <span data-ttu-id="9aacf-105">**ColumnMapping** yeni bir sütun özelliği, ayarlanacak **MappingType.SimpleContent**.</span><span class="sxs-lookup"><span data-stu-id="9aacf-105">The **ColumnMapping** property of the new column will be set to **MappingType.SimpleContent**.</span></span>  
  
 <span data-ttu-id="9aacf-106">Örneğin, aşağıdaki XML göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="9aacf-106">For example, consider the following XML.</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1">Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="9aacf-107">Çıkarma işlemi adlı bir tablo oluşturur **Element1** iki sütunlarla: **attr1** ve **Element1_Text**.</span><span class="sxs-lookup"><span data-stu-id="9aacf-107">The inference process will produce a table named **Element1** with two columns: **attr1** and **Element1_Text**.</span></span> <span data-ttu-id="9aacf-108">**ColumnMapping** özelliği **attr1** sütun ayarlanacak **MappingType.Attribute**.</span><span class="sxs-lookup"><span data-stu-id="9aacf-108">The **ColumnMapping** property of the **attr1** column will be set to **MappingType.Attribute**.</span></span> <span data-ttu-id="9aacf-109">**ColumnMapping** özelliği **Element1_Text** sütun ayarlanacak **MappingType.SimpleContent**.</span><span class="sxs-lookup"><span data-stu-id="9aacf-109">The **ColumnMapping** property of the **Element1_Text** column will be set to **MappingType.SimpleContent**.</span></span>  
  
 <span data-ttu-id="9aacf-110">**Veri kümesi:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="9aacf-110">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="9aacf-111">**Tablo:** Element1</span><span class="sxs-lookup"><span data-stu-id="9aacf-111">**Table:** Element1</span></span>  
  
|<span data-ttu-id="9aacf-112">attr1</span><span class="sxs-lookup"><span data-stu-id="9aacf-112">attr1</span></span>|<span data-ttu-id="9aacf-113">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="9aacf-113">Element1_Text</span></span>|  
|-----------|--------------------|  
|<span data-ttu-id="9aacf-114">Değer1</span><span class="sxs-lookup"><span data-stu-id="9aacf-114">value1</span></span>|<span data-ttu-id="9aacf-115">Metin1</span><span class="sxs-lookup"><span data-stu-id="9aacf-115">Text1</span></span>|  
  
 <span data-ttu-id="9aacf-116">Bir öğenin metni içeren, ancak Ayrıca metin içeren alt öğeleri varsa, bir sütun öğesinde yer metin depolamak için tabloya eklenmez.</span><span class="sxs-lookup"><span data-stu-id="9aacf-116">If an element contains text, but also has child elements that contain text, a column will not be added to the table to store the text contained in the element.</span></span> <span data-ttu-id="9aacf-117">Alt öğeler metinde tablosunda bir satırı dahil ederken öğesinde yer metin yoksayılacak.</span><span class="sxs-lookup"><span data-stu-id="9aacf-117">The text contained in the element will be ignored, while the text in the child elements is included in a row in the table.</span></span> <span data-ttu-id="9aacf-118">Örneğin, aşağıdaki XML göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="9aacf-118">For example, consider the following XML.</span></span>  
  
```xml  
<Element1>  
  Text1  
  <ChildElement1>Text2</ChildElement1>  
  Text3  
</Element1>  
```  
  
 <span data-ttu-id="9aacf-119">Çıkarma işlemi adlı bir tablo oluşturur **Element1** adlı bir sütunu ile **ChildElement1**.</span><span class="sxs-lookup"><span data-stu-id="9aacf-119">The inference process will produce a table named **Element1** with one column named **ChildElement1**.</span></span> <span data-ttu-id="9aacf-120">Metni **ChildElement1** öğesi dahil edilir tabloda satırda.</span><span class="sxs-lookup"><span data-stu-id="9aacf-120">The text for the **ChildElement1** element will be included in a row in the table.</span></span> <span data-ttu-id="9aacf-121">Başka bir metin göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="9aacf-121">The other text will be ignored.</span></span> <span data-ttu-id="9aacf-122">**ColumnMapping** özelliği **ChildElement1** sütun ayarlanacak **MappingType.Element**.</span><span class="sxs-lookup"><span data-stu-id="9aacf-122">The **ColumnMapping** property of the **ChildElement1** column will be set to **MappingType.Element**.</span></span>  
  
 <span data-ttu-id="9aacf-123">**Veri kümesi:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="9aacf-123">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="9aacf-124">**Tablo:** Element1</span><span class="sxs-lookup"><span data-stu-id="9aacf-124">**Table:** Element1</span></span>  
  
|<span data-ttu-id="9aacf-125">ChildElement1</span><span class="sxs-lookup"><span data-stu-id="9aacf-125">ChildElement1</span></span>|  
|-------------------|  
|<span data-ttu-id="9aacf-126">Metin2</span><span class="sxs-lookup"><span data-stu-id="9aacf-126">Text2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9aacf-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9aacf-127">See Also</span></span>  
 [<span data-ttu-id="9aacf-128">Veri kümesi ilişkisel XML yapısından çıkarımını yapma</span><span class="sxs-lookup"><span data-stu-id="9aacf-128">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [<span data-ttu-id="9aacf-129">Bir veri kümesini XML dosyası şuradan yükleniyor</span><span class="sxs-lookup"><span data-stu-id="9aacf-129">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [<span data-ttu-id="9aacf-130">XML'den veri kümesi şema bilgileri yükleniyor</span><span class="sxs-lookup"><span data-stu-id="9aacf-130">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [<span data-ttu-id="9aacf-131">Bir veri kümesini XML kullanma</span><span class="sxs-lookup"><span data-stu-id="9aacf-131">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [<span data-ttu-id="9aacf-132">Veri kümeleri, DataTable ve DataView</span><span class="sxs-lookup"><span data-stu-id="9aacf-132">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="9aacf-133">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="9aacf-133">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
