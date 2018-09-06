---
title: Çıkarım sınırlamaları
ms.date: 03/30/2017
ms.assetid: 78517994-5d57-44f8-9d20-38812977de09
ms.openlocfilehash: d113df98cdd339300b3e75ceda49a56d4f346d3c
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43724159"
---
# <a name="inference-limitations"></a><span data-ttu-id="bfc30-102">Çıkarım sınırlamaları</span><span class="sxs-lookup"><span data-stu-id="bfc30-102">Inference Limitations</span></span>
<span data-ttu-id="bfc30-103">Çıkarma işleminin bir <xref:System.Data.DataSet> XML şemasından XML öğeleri kullanıma bağlı olarak farklı şemalar sonuçlanabilir.</span><span class="sxs-lookup"><span data-stu-id="bfc30-103">The process of inferring a <xref:System.Data.DataSet> schema from XML can result in different schemas depending on the XML elements in each document.</span></span> <span data-ttu-id="bfc30-104">Örneğin, aşağıdaki XML belgeleri göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="bfc30-104">For example, consider the following XML documents.</span></span>  
  
 <span data-ttu-id="bfc30-105">Document1:</span><span class="sxs-lookup"><span data-stu-id="bfc30-105">Document1:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="bfc30-106">Document2:</span><span class="sxs-lookup"><span data-stu-id="bfc30-106">Document2:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="bfc30-107">Çıkarma işlemi "Document1 için" ürettiği bir **veri kümesi** "Element1" yinelenen bir öğe olduğu için "DocumentElement" ve "Element1" adlı bir tablo adı.</span><span class="sxs-lookup"><span data-stu-id="bfc30-107">For "Document1," the inference process produces a **DataSet** named "DocumentElement" and a table named "Element1," because "Element1" is a repeating element.</span></span>  
  
 <span data-ttu-id="bfc30-108">**Veri kümesi:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="bfc30-108">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="bfc30-109">**Tablo:** Element1</span><span class="sxs-lookup"><span data-stu-id="bfc30-109">**Table:** Element1</span></span>  
  
|<span data-ttu-id="bfc30-110">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="bfc30-110">Element1_Text</span></span>|  
|--------------------|  
|<span data-ttu-id="bfc30-111">text1</span><span class="sxs-lookup"><span data-stu-id="bfc30-111">Text1</span></span>|  
|<span data-ttu-id="bfc30-112">Text2</span><span class="sxs-lookup"><span data-stu-id="bfc30-112">Text2</span></span>|  
  
 <span data-ttu-id="bfc30-113">Ancak, "Document2 için" çıkarımı işlemi ürettiği bir **veri kümesi** "NewDataSet" ve "DocumentElement." adlı bir tablo adı</span><span class="sxs-lookup"><span data-stu-id="bfc30-113">However, for "Document2," the inference process produces a **DataSet** named "NewDataSet" and a table named "DocumentElement."</span></span> <span data-ttu-id="bfc30-114">Öznitelikleri ve alt öğe yok olduğundan "Element1" bir sütun olarak algılanır.</span><span class="sxs-lookup"><span data-stu-id="bfc30-114">"Element1" is inferred as a column because it has no attributes and no child elements.</span></span>  
  
 <span data-ttu-id="bfc30-115">**Veri kümesi:** NewDataSet</span><span class="sxs-lookup"><span data-stu-id="bfc30-115">**DataSet:** NewDataSet</span></span>  
  
 <span data-ttu-id="bfc30-116">**Tablo:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="bfc30-116">**Table:** DocumentElement</span></span>  
  
|<span data-ttu-id="bfc30-117">element1</span><span class="sxs-lookup"><span data-stu-id="bfc30-117">Element1</span></span>|  
|--------------|  
|<span data-ttu-id="bfc30-118">text1</span><span class="sxs-lookup"><span data-stu-id="bfc30-118">Text1</span></span>|  
  
 <span data-ttu-id="bfc30-119">Bu iki XML belgeleri şemasına üretmek için hedeflenen, ancak çıkarımı işleminin her belge içerilen öğelerin göre çok farklı sonuçlar üretir.</span><span class="sxs-lookup"><span data-stu-id="bfc30-119">These two XML documents may have been intended to produce the same schema, but the inference process produces very different results based on the elements contained in each document.</span></span>  
  
 <span data-ttu-id="bfc30-120">Şema XML belgesinden oluşturulurken oluşabilecek Tutarsızlıklardan kaçınmak için bir şema XML Şeması Tanım Dili (XSD) veya XML verileri azaltılmış (XDR) yüklenirken kullanılarak açıkça belirtmeniz önerilir bir **veri kümesi** gelen XML.</span><span class="sxs-lookup"><span data-stu-id="bfc30-120">To avoid the discrepancies that can occur when generating schema from an XML document, we recommend that you explicitly specify a schema using XML Schema definition language (XSD) or XML-Data Reduced (XDR) when loading a **DataSet** from XML.</span></span> <span data-ttu-id="bfc30-121">Açıkça belirtme hakkında daha fazla bilgi için bir **veri kümesi** XML Şeması, şema bakın [türetme DataSet ilişkisel yapısını XML Şeması (XSD) öğesinden](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span><span class="sxs-lookup"><span data-stu-id="bfc30-121">For more information about explicitly specifying a **DataSet** schema with XML Schema, see [Deriving DataSet Relational Structure from XML Schema (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfc30-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bfc30-122">See Also</span></span>  
 [<span data-ttu-id="bfc30-123">XML’den DataSet İlişkisel Yapısını Çıkarma</span><span class="sxs-lookup"><span data-stu-id="bfc30-123">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [<span data-ttu-id="bfc30-124">XML’den DataSet Yükleme</span><span class="sxs-lookup"><span data-stu-id="bfc30-124">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [<span data-ttu-id="bfc30-125">XML’den DataSet Schema Bilgilerini Yükleme</span><span class="sxs-lookup"><span data-stu-id="bfc30-125">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [<span data-ttu-id="bfc30-126">DataSet içinde XML kullanma</span><span class="sxs-lookup"><span data-stu-id="bfc30-126">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [<span data-ttu-id="bfc30-127">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="bfc30-127">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="bfc30-128">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="bfc30-128">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
