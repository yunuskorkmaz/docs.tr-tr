---
title: Çıkarım Sınırlamaları
ms.date: 03/30/2017
ms.assetid: 78517994-5d57-44f8-9d20-38812977de09
ms.openlocfilehash: 308d2ffdd9e2cb16626861e25613657f341a4ccb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59076251"
---
# <a name="inference-limitations"></a><span data-ttu-id="39747-102">Çıkarım Sınırlamaları</span><span class="sxs-lookup"><span data-stu-id="39747-102">Inference Limitations</span></span>
<span data-ttu-id="39747-103">Çıkarma işleminin bir <xref:System.Data.DataSet> XML şemasından XML öğeleri kullanıma bağlı olarak farklı şemalar sonuçlanabilir.</span><span class="sxs-lookup"><span data-stu-id="39747-103">The process of inferring a <xref:System.Data.DataSet> schema from XML can result in different schemas depending on the XML elements in each document.</span></span> <span data-ttu-id="39747-104">Örneğin, aşağıdaki XML belgeleri göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="39747-104">For example, consider the following XML documents.</span></span>  
  
 <span data-ttu-id="39747-105">Document1:</span><span class="sxs-lookup"><span data-stu-id="39747-105">Document1:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="39747-106">Document2:</span><span class="sxs-lookup"><span data-stu-id="39747-106">Document2:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="39747-107">Çıkarma işlemi "Document1 için" ürettiği bir **veri kümesi** "Element1" yinelenen bir öğe olduğu için "DocumentElement" ve "Element1" adlı bir tablo adı.</span><span class="sxs-lookup"><span data-stu-id="39747-107">For "Document1," the inference process produces a **DataSet** named "DocumentElement" and a table named "Element1," because "Element1" is a repeating element.</span></span>  
  
 <span data-ttu-id="39747-108">**Veri kümesi:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="39747-108">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="39747-109">**Tablo:** Element1</span><span class="sxs-lookup"><span data-stu-id="39747-109">**Table:** Element1</span></span>  
  
|<span data-ttu-id="39747-110">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="39747-110">Element1_Text</span></span>|  
|--------------------|  
|<span data-ttu-id="39747-111">text1</span><span class="sxs-lookup"><span data-stu-id="39747-111">Text1</span></span>|  
|<span data-ttu-id="39747-112">Text2</span><span class="sxs-lookup"><span data-stu-id="39747-112">Text2</span></span>|  
  
 <span data-ttu-id="39747-113">Ancak, "Document2 için" çıkarımı işlemi ürettiği bir **veri kümesi** "NewDataSet" ve "DocumentElement." adlı bir tablo adı</span><span class="sxs-lookup"><span data-stu-id="39747-113">However, for "Document2," the inference process produces a **DataSet** named "NewDataSet" and a table named "DocumentElement."</span></span> <span data-ttu-id="39747-114">Öznitelikleri ve alt öğe yok olduğundan "Element1" bir sütun olarak algılanır.</span><span class="sxs-lookup"><span data-stu-id="39747-114">"Element1" is inferred as a column because it has no attributes and no child elements.</span></span>  
  
 <span data-ttu-id="39747-115">**Veri kümesi:** NewDataSet</span><span class="sxs-lookup"><span data-stu-id="39747-115">**DataSet:** NewDataSet</span></span>  
  
 <span data-ttu-id="39747-116">**Tablo:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="39747-116">**Table:** DocumentElement</span></span>  
  
|<span data-ttu-id="39747-117">Element1</span><span class="sxs-lookup"><span data-stu-id="39747-117">Element1</span></span>|  
|--------------|  
|<span data-ttu-id="39747-118">text1</span><span class="sxs-lookup"><span data-stu-id="39747-118">Text1</span></span>|  
  
 <span data-ttu-id="39747-119">Bu iki XML belgeleri şemasına üretmek için hedeflenen, ancak çıkarımı işleminin her belge içerilen öğelerin göre çok farklı sonuçlar üretir.</span><span class="sxs-lookup"><span data-stu-id="39747-119">These two XML documents may have been intended to produce the same schema, but the inference process produces very different results based on the elements contained in each document.</span></span>  
  
 <span data-ttu-id="39747-120">Şema XML belgesinden oluşturulurken oluşabilecek Tutarsızlıklardan kaçınmak için bir şema XML Şeması Tanım Dili (XSD) veya XML verileri azaltılmış (XDR) yüklenirken kullanılarak açıkça belirtmeniz önerilir bir **veri kümesi** gelen XML.</span><span class="sxs-lookup"><span data-stu-id="39747-120">To avoid the discrepancies that can occur when generating schema from an XML document, we recommend that you explicitly specify a schema using XML Schema definition language (XSD) or XML-Data Reduced (XDR) when loading a **DataSet** from XML.</span></span> <span data-ttu-id="39747-121">Açıkça belirtme hakkında daha fazla bilgi için bir **veri kümesi** XML Şeması, şema bakın [türetme DataSet ilişkisel yapısını XML Şeması (XSD) öğesinden](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span><span class="sxs-lookup"><span data-stu-id="39747-121">For more information about explicitly specifying a **DataSet** schema with XML Schema, see [Deriving DataSet Relational Structure from XML Schema (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39747-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="39747-122">See also</span></span>

- [<span data-ttu-id="39747-123">XML’den DataSet İlişkisel Yapısını Çıkarma</span><span class="sxs-lookup"><span data-stu-id="39747-123">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="39747-124">XML’den DataSet Yükleme</span><span class="sxs-lookup"><span data-stu-id="39747-124">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)
- [<span data-ttu-id="39747-125">XML’den DataSet Schema Bilgilerini Yükleme</span><span class="sxs-lookup"><span data-stu-id="39747-125">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="39747-126">DataSet içinde XML kullanma</span><span class="sxs-lookup"><span data-stu-id="39747-126">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
- [<span data-ttu-id="39747-127">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="39747-127">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [<span data-ttu-id="39747-128">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="39747-128">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
