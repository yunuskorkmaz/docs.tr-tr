---
title: XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme
ms.date: 03/30/2017
ms.assetid: 3d0d1a4b-9104-434f-ac04-6c01ab5716b5
ms.openlocfilehash: b44c3193e1b9e2e52e086111eab0ab0b0cae5c97
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786079"
---
# <a name="mapping-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="f5e4f-102">XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme</span><span class="sxs-lookup"><span data-stu-id="f5e4f-102">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>
<span data-ttu-id="f5e4f-103">XML şeması tanım dili (XSD), kısıtlama tanımladığı öğeler ve özniteliklerde kısıtlamaların belirtilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="f5e4f-103">The XML Schema definition language (XSD) allows constraints to be specified on the elements and attributes it defines.</span></span> <span data-ttu-id="f5e4f-104">Bir XML şemasını bir <xref:System.Data.DataSet>' deki ilişkisel şemayla eşlerken, XML şeması kısıtlamaları **veri kümesindeki**tablolar ve sütunlarda uygun ilişkisel kısıtlamalara eşlenir.</span><span class="sxs-lookup"><span data-stu-id="f5e4f-104">When mapping an XML Schema to relational schema in a <xref:System.Data.DataSet>, XML Schema constraints are mapped to appropriate relational constraints on the tables and columns within the **DataSet**.</span></span>  
  
 <span data-ttu-id="f5e4f-105">Bu bölüm, aşağıdaki XML şeması kısıtlamalarının eşlemesini anlatmaktadır:</span><span class="sxs-lookup"><span data-stu-id="f5e4f-105">This section discusses the mapping of the following XML Schema constraints:</span></span>  
  
- <span data-ttu-id="f5e4f-106">**Unique** öğesi kullanılarak belirtilen benzersizlik kısıtlaması.</span><span class="sxs-lookup"><span data-stu-id="f5e4f-106">The uniqueness constraint specified using the **unique** element.</span></span>  
  
- <span data-ttu-id="f5e4f-107">**Key** öğesi kullanılarak belirtilen anahtar kısıtlaması.</span><span class="sxs-lookup"><span data-stu-id="f5e4f-107">The key constraint specified using the **key** element.</span></span>  
  
- <span data-ttu-id="f5e4f-108">**Keyref öğesi kullanılarak** belirtilen keyref kısıtlaması.</span><span class="sxs-lookup"><span data-stu-id="f5e4f-108">The keyref constraint specified using the **keyref** element.</span></span>  
  
 <span data-ttu-id="f5e4f-109">Bir öğe veya öznitelik üzerinde bir kısıtlama kullanarak, herhangi bir belgenin örneğindeki öğe değerleri üzerinde belirli kısıtlamalar belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f5e4f-109">By using a constraint on an element or attribute, you specify certain restrictions on the values of the element in any instance of the document.</span></span> <span data-ttu-id="f5e4f-110">Örneğin, şemadaki bir **Müşteri** öğesinin **MüşteriNo** alt öğesinde bir anahtar kısıtlaması, **MüşteriNo** alt öğesinin değerlerinin herhangi bir belge örneğinde benzersiz olması gerektiğini ve null değerlere izin verilmediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f5e4f-110">For example, a key constraint on a **CustomerID** child element of a **Customer** element in the schema indicates that the values of the **CustomerID** child element must be unique in any document instance, and that null values are not allowed.</span></span>  
  
 <span data-ttu-id="f5e4f-111">Belge içinde ilişki kurmak için bir belgedeki öğeler ve öznitelikler arasında da bir kısıtlama belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="f5e4f-111">Constraints can also be specified between elements and attributes in a document, in order to establish a relationship within the document.</span></span> <span data-ttu-id="f5e4f-112">Anahtar ve keyref kısıtlamaları, belge içindeki kısıtlamaları belirtmek için şemada kullanılır ve belge öğeleri ile öznitelikler arasında bir ilişki elde edilir.</span><span class="sxs-lookup"><span data-stu-id="f5e4f-112">The key and keyref constraints are used in the schema to specify the constraints within the document, resulting in a relationship between document elements and attributes.</span></span>  
  
 <span data-ttu-id="f5e4f-113">Eşleme işlemi, bu şema kısıtlamalarını **veri kümesi**içinde oluşturulan tablolardaki uygun kısıtlamalara dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="f5e4f-113">The mapping process converts these schema constraints into appropriate constraints on the tables created within the **DataSet**.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f5e4f-114">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="f5e4f-114">In This Section</span></span>  
 [<span data-ttu-id="f5e4f-115">Benzersiz XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme</span><span class="sxs-lookup"><span data-stu-id="f5e4f-115">Map unique XML Schema (XSD) Constraints to DataSet Constraints</span></span>](map-unique-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="f5e4f-116">Bir **veri kümesinde**benzersiz kısıtlamalar oluşturmak IÇIN kullanılan xml şema öğelerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="f5e4f-116">Describes the XML Schema elements used to create unique constraints in a **DataSet**.</span></span>  
  
 [<span data-ttu-id="f5e4f-117">Anahtar XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme</span><span class="sxs-lookup"><span data-stu-id="f5e4f-117">Map key XML Schema (XSD) Constraints to DataSet Constraints</span></span>](map-key-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="f5e4f-118">Bir **veri kümesinde**anahtar kısıtlamalarını (null değerlere izin verilmeyen benzersiz kısıtlamalar) oluşturmak IÇIN kullanılan xml şema öğelerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="f5e4f-118">Describes the XML Schema elements used to create key constraints (unique constraints where null values are not allowed) in a **DataSet**.</span></span>  
  
 [<span data-ttu-id="f5e4f-119">Keyref XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme</span><span class="sxs-lookup"><span data-stu-id="f5e4f-119">Map keyref XML Schema (XSD) Constraints to DataSet Constraints</span></span>](map-keyref-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="f5e4f-120">Bir **veri kümesinde**keyref (yabancı anahtar) kısıtlamalarını oluşturmak IÇIN kullanılan xml şema öğelerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="f5e4f-120">Describes the XML Schema elements used to create keyref (foreign key) constraints in a **DataSet**.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="f5e4f-121">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="f5e4f-121">Related Sections</span></span>  
 [<span data-ttu-id="f5e4f-122">XML Şemasından (XSD) DataSet İlişkisel Yapısını Türetme</span><span class="sxs-lookup"><span data-stu-id="f5e4f-122">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 <span data-ttu-id="f5e4f-123">XSD şemasından oluşturulan bir **veri kümesinin** ilişkisel yapısını veya şemasını açıklar.</span><span class="sxs-lookup"><span data-stu-id="f5e4f-123">Describes the relational structure, or schema, of a **DataSet** that is created from XSD schema.</span></span>  
  
 [<span data-ttu-id="f5e4f-124">XML Şemasından (XSD) DataSet İlişkileri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f5e4f-124">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)  
 <span data-ttu-id="f5e4f-125">Bir **veri kümesindeki**tablo sütunları arasında ilişki oluşturmak IÇIN kullanılan xml şema öğelerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="f5e4f-125">Describes the XML Schema elements used to create relations between table columns in a **DataSet**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5e4f-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f5e4f-126">See also</span></span>

- [<span data-ttu-id="f5e4f-127">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="f5e4f-127">ADO.NET Overview</span></span>](../ado-net-overview.md)
