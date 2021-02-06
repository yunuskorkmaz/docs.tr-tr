---
description: 'Hakkında daha fazla bilgi edinin: XML şeması (XSD) kısıtlamalarını veri kümesi kısıtlamalarına eşleme'
title: XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme
ms.date: 03/30/2017
ms.assetid: 3d0d1a4b-9104-434f-ac04-6c01ab5716b5
ms.openlocfilehash: b1a958029e541b6ac95b5c509665005c9006adfa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99651892"
---
# <a name="mapping-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="e5e71-103">XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme</span><span class="sxs-lookup"><span data-stu-id="e5e71-103">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>

<span data-ttu-id="e5e71-104">XML şeması tanım dili (XSD), kısıtlama tanımladığı öğeler ve özniteliklerde kısıtlamaların belirtilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="e5e71-104">The XML Schema definition language (XSD) allows constraints to be specified on the elements and attributes it defines.</span></span> <span data-ttu-id="e5e71-105">Bir XML şemasını bir ' deki ilişkisel şemayla eşlerken <xref:System.Data.DataSet> , XML şeması kısıtlamaları **veri kümesindeki** tablolar ve sütunlarda uygun ilişkisel kısıtlamalara eşlenir.</span><span class="sxs-lookup"><span data-stu-id="e5e71-105">When mapping an XML Schema to relational schema in a <xref:System.Data.DataSet>, XML Schema constraints are mapped to appropriate relational constraints on the tables and columns within the **DataSet**.</span></span>  
  
 <span data-ttu-id="e5e71-106">Bu bölüm, aşağıdaki XML şeması kısıtlamalarının eşlemesini anlatmaktadır:</span><span class="sxs-lookup"><span data-stu-id="e5e71-106">This section discusses the mapping of the following XML Schema constraints:</span></span>  
  
- <span data-ttu-id="e5e71-107">**Unique** öğesi kullanılarak belirtilen benzersizlik kısıtlaması.</span><span class="sxs-lookup"><span data-stu-id="e5e71-107">The uniqueness constraint specified using the **unique** element.</span></span>  
  
- <span data-ttu-id="e5e71-108">**Key** öğesi kullanılarak belirtilen anahtar kısıtlaması.</span><span class="sxs-lookup"><span data-stu-id="e5e71-108">The key constraint specified using the **key** element.</span></span>  
  
- <span data-ttu-id="e5e71-109">**Keyref öğesi kullanılarak** belirtilen keyref kısıtlaması.</span><span class="sxs-lookup"><span data-stu-id="e5e71-109">The keyref constraint specified using the **keyref** element.</span></span>  
  
 <span data-ttu-id="e5e71-110">Bir öğe veya öznitelik üzerinde bir kısıtlama kullanarak, herhangi bir belgenin örneğindeki öğe değerleri üzerinde belirli kısıtlamalar belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e5e71-110">By using a constraint on an element or attribute, you specify certain restrictions on the values of the element in any instance of the document.</span></span> <span data-ttu-id="e5e71-111">Örneğin, şemadaki bir **Müşteri** öğesinin **MüşteriNo** alt öğesinde bir anahtar kısıtlaması, **MüşteriNo** alt öğesinin değerlerinin herhangi bir belge örneğinde benzersiz olması gerektiğini ve null değerlere izin verilmediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="e5e71-111">For example, a key constraint on a **CustomerID** child element of a **Customer** element in the schema indicates that the values of the **CustomerID** child element must be unique in any document instance, and that null values are not allowed.</span></span>  
  
 <span data-ttu-id="e5e71-112">Belge içinde ilişki kurmak için bir belgedeki öğeler ve öznitelikler arasında da bir kısıtlama belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="e5e71-112">Constraints can also be specified between elements and attributes in a document, in order to establish a relationship within the document.</span></span> <span data-ttu-id="e5e71-113">Anahtar ve keyref kısıtlamaları, belge içindeki kısıtlamaları belirtmek için şemada kullanılır ve belge öğeleri ile öznitelikler arasında bir ilişki elde edilir.</span><span class="sxs-lookup"><span data-stu-id="e5e71-113">The key and keyref constraints are used in the schema to specify the constraints within the document, resulting in a relationship between document elements and attributes.</span></span>  
  
 <span data-ttu-id="e5e71-114">Eşleme işlemi, bu şema kısıtlamalarını **veri kümesi** içinde oluşturulan tablolardaki uygun kısıtlamalara dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="e5e71-114">The mapping process converts these schema constraints into appropriate constraints on the tables created within the **DataSet**.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e5e71-115">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="e5e71-115">In This Section</span></span>  

 [<span data-ttu-id="e5e71-116">Benzersiz XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme</span><span class="sxs-lookup"><span data-stu-id="e5e71-116">Map unique XML Schema (XSD) Constraints to DataSet Constraints</span></span>](map-unique-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="e5e71-117">Bir **veri kümesinde** benzersiz kısıtlamalar oluşturmak IÇIN kullanılan xml şema öğelerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="e5e71-117">Describes the XML Schema elements used to create unique constraints in a **DataSet**.</span></span>  
  
 [<span data-ttu-id="e5e71-118">Anahtar XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme</span><span class="sxs-lookup"><span data-stu-id="e5e71-118">Map key XML Schema (XSD) Constraints to DataSet Constraints</span></span>](map-key-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="e5e71-119">Bir **veri kümesinde** anahtar kısıtlamalarını (null değerlere izin verilmeyen benzersiz kısıtlamalar) oluşturmak IÇIN kullanılan xml şema öğelerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="e5e71-119">Describes the XML Schema elements used to create key constraints (unique constraints where null values are not allowed) in a **DataSet**.</span></span>  
  
 [<span data-ttu-id="e5e71-120">Keyref XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme</span><span class="sxs-lookup"><span data-stu-id="e5e71-120">Map keyref XML Schema (XSD) Constraints to DataSet Constraints</span></span>](map-keyref-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="e5e71-121">Bir **veri kümesinde** keyref (yabancı anahtar) kısıtlamalarını oluşturmak IÇIN kullanılan xml şema öğelerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="e5e71-121">Describes the XML Schema elements used to create keyref (foreign key) constraints in a **DataSet**.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e5e71-122">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="e5e71-122">Related Sections</span></span>  

 [<span data-ttu-id="e5e71-123">XML Şemasından (XSD) DataSet İlişkisel Yapısını Türetme</span><span class="sxs-lookup"><span data-stu-id="e5e71-123">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 <span data-ttu-id="e5e71-124">XSD şemasından oluşturulan bir **veri kümesinin** ilişkisel yapısını veya şemasını açıklar.</span><span class="sxs-lookup"><span data-stu-id="e5e71-124">Describes the relational structure, or schema, of a **DataSet** that is created from XSD schema.</span></span>  
  
 [<span data-ttu-id="e5e71-125">XML Şemasından (XSD) DataSet İlişkileri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e5e71-125">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)  
 <span data-ttu-id="e5e71-126">Bir **veri kümesindeki** tablo sütunları arasında ilişki oluşturmak IÇIN kullanılan xml şema öğelerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="e5e71-126">Describes the XML Schema elements used to create relations between table columns in a **DataSet**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5e71-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e5e71-127">See also</span></span>

- [<span data-ttu-id="e5e71-128">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e5e71-128">ADO.NET Overview</span></span>](../ado-net-overview.md)
