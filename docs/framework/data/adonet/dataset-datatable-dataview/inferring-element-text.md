---
description: 'Daha fazla bilgi edinin: öğe metnini erteleme'
title: Öğe Metni Çıkarımını Yapma
ms.date: 03/30/2017
ms.assetid: 789799e5-716f-459f-a168-76c5cf22178b
ms.openlocfilehash: 5d0d9b1b3bb6164cd3cf26b429a4c7d658ee4128
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99652217"
---
# <a name="inferring-element-text"></a><span data-ttu-id="22b57-103">Öğe Metni Çıkarımını Yapma</span><span class="sxs-lookup"><span data-stu-id="22b57-103">Inferring Element Text</span></span>

<span data-ttu-id="22b57-104">Bir öğe metin içeriyorsa ve tablo olarak (öznitelikler veya yinelenen öğeler içeren öğeler gibi) çıkarsmayacak alt öğeleri yoksa, **TableName_Text** adlı yeni bir sütun, öğe için çıkartılan tabloya eklenir.</span><span class="sxs-lookup"><span data-stu-id="22b57-104">If an element contains text and has no child elements to be inferred as tables (such as elements with attributes or repeated elements), a new column with the name **TableName_Text** will be added to the table that is inferred for the element.</span></span> <span data-ttu-id="22b57-105">Öğesinde bulunan metin, tablodaki bir satıra eklenir ve yeni sütunda depolanır.</span><span class="sxs-lookup"><span data-stu-id="22b57-105">The text contained in the element will be added to a row in the table and stored in the new column.</span></span> <span data-ttu-id="22b57-106">Yeni sütunun **ColumnMapping** özelliği **MappingType. simpleContent** olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="22b57-106">The **ColumnMapping** property of the new column will be set to **MappingType.SimpleContent**.</span></span>  
  
 <span data-ttu-id="22b57-107">Örneğin, aşağıdaki XML 'i göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="22b57-107">For example, consider the following XML.</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1">Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="22b57-108">Çıkarım işlemi, iki sütunlu **Element1** adlı bir tablo oluşturur: **attr1** ve **Element1_Text**.</span><span class="sxs-lookup"><span data-stu-id="22b57-108">The inference process will produce a table named **Element1** with two columns: **attr1** and **Element1_Text**.</span></span> <span data-ttu-id="22b57-109">**Attr1** sütununun **ColumnMapping** özelliği **MappingType. Attribute** olarak ayarlanacak.</span><span class="sxs-lookup"><span data-stu-id="22b57-109">The **ColumnMapping** property of the **attr1** column will be set to **MappingType.Attribute**.</span></span> <span data-ttu-id="22b57-110">**Element1_Text** sütununun **ColumnMapping** özelliği **MappingType. simpleContent** olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="22b57-110">The **ColumnMapping** property of the **Element1_Text** column will be set to **MappingType.SimpleContent**.</span></span>  
  
 <span data-ttu-id="22b57-111">**Veri kümesi:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="22b57-111">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="22b57-112">**Tablo:** Element1</span><span class="sxs-lookup"><span data-stu-id="22b57-112">**Table:** Element1</span></span>  
  
|<span data-ttu-id="22b57-113">attr1</span><span class="sxs-lookup"><span data-stu-id="22b57-113">attr1</span></span>|<span data-ttu-id="22b57-114">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="22b57-114">Element1_Text</span></span>|  
|-----------|--------------------|  
|<span data-ttu-id="22b57-115">value1</span><span class="sxs-lookup"><span data-stu-id="22b57-115">value1</span></span>|<span data-ttu-id="22b57-116">Text1</span><span class="sxs-lookup"><span data-stu-id="22b57-116">Text1</span></span>|  
  
 <span data-ttu-id="22b57-117">Bir öğe metin içeriyorsa, ancak aynı zamanda metin içeren alt öğelere sahipse, öğesinde içerilen metni depolamak için tabloya bir sütun eklenmez.</span><span class="sxs-lookup"><span data-stu-id="22b57-117">If an element contains text, but also has child elements that contain text, a column will not be added to the table to store the text contained in the element.</span></span> <span data-ttu-id="22b57-118">Öğesinde içerilen metin yok sayılır, ancak alt öğelerdeki metin, tablodaki bir satıra dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="22b57-118">The text contained in the element will be ignored, while the text in the child elements is included in a row in the table.</span></span> <span data-ttu-id="22b57-119">Örneğin, aşağıdaki XML 'i göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="22b57-119">For example, consider the following XML.</span></span>  
  
```xml  
<Element1>  
  Text1  
  <ChildElement1>Text2</ChildElement1>  
  Text3  
</Element1>  
```  
  
 <span data-ttu-id="22b57-120">Çıkarım işlemi, **ChildElement1** adlı tek sütunlu **Element1** adlı bir tablo oluşturur.</span><span class="sxs-lookup"><span data-stu-id="22b57-120">The inference process will produce a table named **Element1** with one column named **ChildElement1**.</span></span> <span data-ttu-id="22b57-121">**ChildElement1** öğesinin metni, tablodaki bir satıra dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="22b57-121">The text for the **ChildElement1** element will be included in a row in the table.</span></span> <span data-ttu-id="22b57-122">Diğer metin yok sayılacak.</span><span class="sxs-lookup"><span data-stu-id="22b57-122">The other text will be ignored.</span></span> <span data-ttu-id="22b57-123">**ChildElement1** sütununun **ColumnMapping** özelliği **MappingType. element** olarak ayarlanacak.</span><span class="sxs-lookup"><span data-stu-id="22b57-123">The **ColumnMapping** property of the **ChildElement1** column will be set to **MappingType.Element**.</span></span>  
  
 <span data-ttu-id="22b57-124">**Veri kümesi:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="22b57-124">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="22b57-125">**Tablo:** Element1</span><span class="sxs-lookup"><span data-stu-id="22b57-125">**Table:** Element1</span></span>  
  
|<span data-ttu-id="22b57-126">ChildElement1</span><span class="sxs-lookup"><span data-stu-id="22b57-126">ChildElement1</span></span>|  
|-------------------|  
|<span data-ttu-id="22b57-127">Metin2</span><span class="sxs-lookup"><span data-stu-id="22b57-127">Text2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="22b57-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="22b57-128">See also</span></span>

- [<span data-ttu-id="22b57-129">XML’den DataSet İlişkisel Yapısını Çıkarma</span><span class="sxs-lookup"><span data-stu-id="22b57-129">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="22b57-130">XML’den DataSet Yükleme</span><span class="sxs-lookup"><span data-stu-id="22b57-130">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="22b57-131">XML’den DataSet Schema Bilgilerini Yükleme</span><span class="sxs-lookup"><span data-stu-id="22b57-131">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="22b57-132">DataSet içinde XML kullanma</span><span class="sxs-lookup"><span data-stu-id="22b57-132">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="22b57-133">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="22b57-133">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="22b57-134">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="22b57-134">ADO.NET Overview</span></span>](../ado-net-overview.md)
