---
title: "Veri kümesi sınırlamaları için eşleme XML Şeması (XSD) kısıtlamaları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3d0d1a4b-9104-434f-ac04-6c01ab5716b5
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 9ac8e64c02d96450d41233cfbe65e1db839df9e7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="mapping-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="fbf98-102">Veri kümesi sınırlamaları için eşleme XML Şeması (XSD) kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="fbf98-102">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>
<span data-ttu-id="fbf98-103">XML Şeması Tanım Dili (XSD) kısıtlamaları öğeleri ve özniteliklerinin tanımladığı üzerinde belirtilmesine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="fbf98-103">The XML Schema definition language (XSD) allows constraints to be specified on the elements and attributes it defines.</span></span> <span data-ttu-id="fbf98-104">Bir XML Şeması ilişkisel şemada eşlerken bir <xref:System.Data.DataSet>, XML Şeması kısıtlamaları tablolar ve sütunlar içinde uygun ilişkisel kısıtlamalar eşlendiğinden **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="fbf98-104">When mapping an XML Schema to relational schema in a <xref:System.Data.DataSet>, XML Schema constraints are mapped to appropriate relational constraints on the tables and columns within the **DataSet**.</span></span>  
  
 <span data-ttu-id="fbf98-105">Bu bölümde aşağıdaki XML Şeması kısıtlamaları eşleme ele alınmıştır:</span><span class="sxs-lookup"><span data-stu-id="fbf98-105">This section discusses the mapping of the following XML Schema constraints:</span></span>  
  
-   <span data-ttu-id="fbf98-106">Benzersizlik kısıtlamasını kullanarak belirtilen **benzersiz** öğesi.</span><span class="sxs-lookup"><span data-stu-id="fbf98-106">The uniqueness constraint specified using the **unique** element.</span></span>  
  
-   <span data-ttu-id="fbf98-107">Anahtar kısıtlamasını kullanarak belirtilen **anahtar** öğesi.</span><span class="sxs-lookup"><span data-stu-id="fbf98-107">The key constraint specified using the **key** element.</span></span>  
  
-   <span data-ttu-id="fbf98-108">Kullanarak belirtilen keyref kısıtlaması **keyref** öğesi.</span><span class="sxs-lookup"><span data-stu-id="fbf98-108">The keyref constraint specified using the **keyref** element.</span></span>  
  
 <span data-ttu-id="fbf98-109">Öğe veya öznitelik bir kısıtlama kullanarak bazı kısıtlamalar belge herhangi bir örneğine öğesinde değerleri belirtin.</span><span class="sxs-lookup"><span data-stu-id="fbf98-109">By using a constraint on an element or attribute, you specify certain restrictions on the values of the element in any instance of the document.</span></span> <span data-ttu-id="fbf98-110">Örneğin, bir anahtar kısıtlaması bir **CustomerID** alt öğesi olan bir **müşteri** schema öğesinde gösterir değerlerini **CustomerID** alt öğesi olması gerekir herhangi bir belge örneğindeki benzersiz ve null değerlere izin verilmemektedir.</span><span class="sxs-lookup"><span data-stu-id="fbf98-110">For example, a key constraint on a **CustomerID** child element of a **Customer** element in the schema indicates that the values of the **CustomerID** child element must be unique in any document instance, and that null values are not allowed.</span></span>  
  
 <span data-ttu-id="fbf98-111">Kısıtlamaları da öğeleri ve özniteliklerinin bir belgede arasında belge içinde bir ilişkisi oluşturmak için belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="fbf98-111">Constraints can also be specified between elements and attributes in a document, in order to establish a relationship within the document.</span></span> <span data-ttu-id="fbf98-112">Anahtar ve keyref kısıtlamaları şemada kısıtlamaları belge öğeleri ve özniteliklerinin arasında bir ilişki sonuçta belgenin içinde belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fbf98-112">The key and keyref constraints are used in the schema to specify the constraints within the document, resulting in a relationship between document elements and attributes.</span></span>  
  
 <span data-ttu-id="fbf98-113">Eşleme işlemini içinde oluşturulan tabloları uygun kısıtlamalar bu şema kısıtlamaları dönüştürür **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="fbf98-113">The mapping process converts these schema constraints into appropriate constraints on the tables created within the **DataSet**.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fbf98-114">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="fbf98-114">In This Section</span></span>  
 [<span data-ttu-id="fbf98-115">Veri kümesi sınırlamaları benzersiz XML Şeması (XSD) kısıtlamalar eşleme</span><span class="sxs-lookup"><span data-stu-id="fbf98-115">Map unique XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-unique-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="fbf98-116">Benzersiz kısıtlamalar oluşturmak için kullanılan XML şema öğeleri açıklayan bir **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="fbf98-116">Describes the XML Schema elements used to create unique constraints in a **DataSet**.</span></span>  
  
 [<span data-ttu-id="fbf98-117">Harita anahtar DataSet kısıtlamaları için XML Şeması (XSD) kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="fbf98-117">Map key XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-key-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="fbf98-118">Anahtar kısıtlamalarını (benzersiz kısıtlamalar burada null değerlere izin vermiyor) oluşturmak için kullanılan XML şema öğeleri açıklanır bir **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="fbf98-118">Describes the XML Schema elements used to create key constraints (unique constraints where null values are not allowed) in a **DataSet**.</span></span>  
  
 [<span data-ttu-id="fbf98-119">Harita keyref DataSet kısıtlamaları için XML Şeması (XSD) kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="fbf98-119">Map keyref XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-keyref-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="fbf98-120">Keyref (yabancı anahtar) kısıtlamalar oluşturmak için kullanılan XML şema öğeleri açıklayan bir **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="fbf98-120">Describes the XML Schema elements used to create keyref (foreign key) constraints in a **DataSet**.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="fbf98-121">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="fbf98-121">Related Sections</span></span>  
 [<span data-ttu-id="fbf98-122">Türetilen DataSet ilişkisel yapısından XML Şeması (XSD)</span><span class="sxs-lookup"><span data-stu-id="fbf98-122">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 <span data-ttu-id="fbf98-123">İlişkisel yapısı veya şema açıklayan bir **DataSet** XSD şema oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="fbf98-123">Describes the relational structure, or schema, of a **DataSet** that is created from XSD schema.</span></span>  
  
 [<span data-ttu-id="fbf98-124">DataSet ilişkileri XML Schema (XSD) oluşturma</span><span class="sxs-lookup"><span data-stu-id="fbf98-124">Generating DataSet Relations from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 <span data-ttu-id="fbf98-125">Tablo sütunları arasındaki ilişkileri oluşturmak için kullanılan XML Şeması öğelerini açıklar bir **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="fbf98-125">Describes the XML Schema elements used to create relations between table columns in a **DataSet**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbf98-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fbf98-126">See Also</span></span>  
 [<span data-ttu-id="fbf98-127">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="fbf98-127">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
