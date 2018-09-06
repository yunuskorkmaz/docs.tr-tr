---
title: XML Şeması (XSD) kısıtlamalarını DataSet kısıtlamaları ile eşleme
ms.date: 03/30/2017
ms.assetid: 3d0d1a4b-9104-434f-ac04-6c01ab5716b5
ms.openlocfilehash: c9cd97535a0165b82f0823c1f17f621491d4255c
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43868685"
---
# <a name="mapping-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="0866f-102">XML Şeması (XSD) kısıtlamalarını DataSet kısıtlamaları ile eşleme</span><span class="sxs-lookup"><span data-stu-id="0866f-102">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>
<span data-ttu-id="0866f-103">XML Şeması Tanım Dili (XSD) öğeleri ve öznitelikleri tanımlar belirtilmesi kısıtlamaları sağlar.</span><span class="sxs-lookup"><span data-stu-id="0866f-103">The XML Schema definition language (XSD) allows constraints to be specified on the elements and attributes it defines.</span></span> <span data-ttu-id="0866f-104">Bir XML Şeması ilişkisel şemasında eşlerken bir <xref:System.Data.DataSet>, XML şema kısıtlamaları uygun ilişkisel tabloları ve sütunları kısıtlamalar eşleştirilmiş **veri kümesi**.</span><span class="sxs-lookup"><span data-stu-id="0866f-104">When mapping an XML Schema to relational schema in a <xref:System.Data.DataSet>, XML Schema constraints are mapped to appropriate relational constraints on the tables and columns within the **DataSet**.</span></span>  
  
 <span data-ttu-id="0866f-105">Bu bölümde, aşağıdaki XML şema kısıtlamaları eşleme ele alınmaktadır:</span><span class="sxs-lookup"><span data-stu-id="0866f-105">This section discusses the mapping of the following XML Schema constraints:</span></span>  
  
-   <span data-ttu-id="0866f-106">Benzersizlik kısıtlamasını kullanarak belirtilen **benzersiz** öğesi.</span><span class="sxs-lookup"><span data-stu-id="0866f-106">The uniqueness constraint specified using the **unique** element.</span></span>  
  
-   <span data-ttu-id="0866f-107">Anahtar kısıtlamasını kullanarak belirtilen **anahtar** öğesi.</span><span class="sxs-lookup"><span data-stu-id="0866f-107">The key constraint specified using the **key** element.</span></span>  
  
-   <span data-ttu-id="0866f-108">Kullanarak belirtilen keyref kısıtlama **keyref** öğesi.</span><span class="sxs-lookup"><span data-stu-id="0866f-108">The keyref constraint specified using the **keyref** element.</span></span>  
  
 <span data-ttu-id="0866f-109">Bir öğe veya öznitelik bir kısıtlama kullanarak belirli kısıtlamalara belgenin herhangi bir örneğindeki öğe değerlerini belirtin.</span><span class="sxs-lookup"><span data-stu-id="0866f-109">By using a constraint on an element or attribute, you specify certain restrictions on the values of the element in any instance of the document.</span></span> <span data-ttu-id="0866f-110">Örneğin, bir anahtar kısıtlaması bir **CustomerID** alt öğesi bir **müşteri** şema öğesi gösterir değerlerini **CustomerID** alt öğesi olmalıdır. herhangi bir belge örneğindeki benzersiz ve null değerlere izin verilmemektedir.</span><span class="sxs-lookup"><span data-stu-id="0866f-110">For example, a key constraint on a **CustomerID** child element of a **Customer** element in the schema indicates that the values of the **CustomerID** child element must be unique in any document instance, and that null values are not allowed.</span></span>  
  
 <span data-ttu-id="0866f-111">Kısıtlamaları da arasında öğeleri ve özniteliklerinin belgede, belge içindeki bir ilişki kurmak için belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="0866f-111">Constraints can also be specified between elements and attributes in a document, in order to establish a relationship within the document.</span></span> <span data-ttu-id="0866f-112">Anahtar ve keyref kısıtlamaları şemada kısıtlamaları belge öğeleri ve öznitelikleri arasında bir ilişki výsledek belgenin içinde belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0866f-112">The key and keyref constraints are used in the schema to specify the constraints within the document, resulting in a relationship between document elements and attributes.</span></span>  
  
 <span data-ttu-id="0866f-113">Bu şema kısıtlamaları eşleme işlemi içinde oluşturulmuş tablolarda uygun kısıtlamaları dönüştürür **veri kümesi**.</span><span class="sxs-lookup"><span data-stu-id="0866f-113">The mapping process converts these schema constraints into appropriate constraints on the tables created within the **DataSet**.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0866f-114">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="0866f-114">In This Section</span></span>  
 [<span data-ttu-id="0866f-115">Benzersiz XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme</span><span class="sxs-lookup"><span data-stu-id="0866f-115">Map unique XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-unique-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="0866f-116">İçinde benzersiz kısıtlamalar oluşturmak için kullanılan XML Şeması öğeleri açıklar bir **veri kümesi**.</span><span class="sxs-lookup"><span data-stu-id="0866f-116">Describes the XML Schema elements used to create unique constraints in a **DataSet**.</span></span>  
  
 [<span data-ttu-id="0866f-117">Anahtar XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme</span><span class="sxs-lookup"><span data-stu-id="0866f-117">Map key XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-key-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="0866f-118">İçindeki anahtar kısıtlamaları (benzersiz kısıtlamalar burada null değerlere izin verilmez) oluşturmak için kullanılan XML Şeması öğeleri açıklar bir **veri kümesi**.</span><span class="sxs-lookup"><span data-stu-id="0866f-118">Describes the XML Schema elements used to create key constraints (unique constraints where null values are not allowed) in a **DataSet**.</span></span>  
  
 [<span data-ttu-id="0866f-119">Keyref XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme</span><span class="sxs-lookup"><span data-stu-id="0866f-119">Map keyref XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-keyref-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="0866f-120">Keyref (yabancı anahtar) kısıtlamalarını oluşturmak için kullanılan XML Şeması öğeleri açıklar bir **veri kümesi**.</span><span class="sxs-lookup"><span data-stu-id="0866f-120">Describes the XML Schema elements used to create keyref (foreign key) constraints in a **DataSet**.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="0866f-121">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="0866f-121">Related Sections</span></span>  
 [<span data-ttu-id="0866f-122">XML Şemasından (XSD) DataSet İlişkisel Yapısını Türetme</span><span class="sxs-lookup"><span data-stu-id="0866f-122">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 <span data-ttu-id="0866f-123">İlişkisel yapısını veya şema biri açıklar bir **veri kümesi** XSD şema oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="0866f-123">Describes the relational structure, or schema, of a **DataSet** that is created from XSD schema.</span></span>  
  
 [<span data-ttu-id="0866f-124">XML Şemasından (XSD) DataSet İlişkileri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="0866f-124">Generating DataSet Relations from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 <span data-ttu-id="0866f-125">Tablo sütunlarını arasındaki ilişkileri oluşturmak için kullanılan XML Şeması öğeleri açıklar bir **veri kümesi**.</span><span class="sxs-lookup"><span data-stu-id="0866f-125">Describes the XML Schema elements used to create relations between table columns in a **DataSet**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0866f-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0866f-126">See Also</span></span>  
 [<span data-ttu-id="0866f-127">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="0866f-127">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
