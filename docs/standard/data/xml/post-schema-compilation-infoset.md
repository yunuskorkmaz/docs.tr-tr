---
title: "Derleme sonrası şema bilgi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 7f1bc7f4-401b-459f-9078-f099cc711fde
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 77fe1790a4ff2f910a740e969e458549f1fd9642
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="post-schema-compilation-infoset"></a><span data-ttu-id="7d337-102">Derleme sonrası şema bilgi</span><span class="sxs-lookup"><span data-stu-id="7d337-102">Post-Schema Compilation Infoset</span></span>
<span data-ttu-id="7d337-103">[World Wide Web Konsorsiyumu (W3C) XML Şeması öneri](http://go.microsoft.com/fwlink/?linkid=45242) öncesi şema doğrulaması ve sonrası şema derleme için sunulmalıdır bilgisi kümesi (bilgi) açıklanır.</span><span class="sxs-lookup"><span data-stu-id="7d337-103">The [World Wide Web Consortium (W3C) XML Schema Recommendation](http://go.microsoft.com/fwlink/?linkid=45242) discusses the information set (infoset) that must be exposed for pre-schema validation and post-schema compilation.</span></span> <span data-ttu-id="7d337-104">XML şema nesne modeli (SOM) önce ve sonra bu Etkilenme görünümleri <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> yöntemi <xref:System.Xml.Schema.XmlSchemaSet> olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="7d337-104">The XML Schema Object Model (SOM) views this exposure before and after the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet> is called.</span></span>  
  
 <span data-ttu-id="7d337-105">Ön şema doğrulaması bilgi ve şema düzenleme sırasında oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="7d337-105">The pre-schema validation infoset is built during the editing of the schema.</span></span> <span data-ttu-id="7d337-106">Derleme sonrası şema bilgi sonra oluşturulan <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> yöntemi <xref:System.Xml.Schema.XmlSchemaSet> şema derlemesi sırasında çağrılır ve özellikleri olarak sunulur.</span><span class="sxs-lookup"><span data-stu-id="7d337-106">The post-schema compilation infoset is generated after the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet> is called, during compilation of the schema, and is exposed as properties.</span></span>  
  
 <span data-ttu-id="7d337-107">SOM öncesi şema doğrulaması ve sonrası şema derleme infosets temsil eden nesne modelidir; sınıflarda oluşan <xref:System.Xml.Schema?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="7d337-107">The SOM is the object model that represents the pre-schema validation and post-schema compilation infosets; it consists of the classes in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="7d337-108">Tüm okuma ve yazma sınıflarda özellikleri <xref:System.Xml.Schema> ad alanı ait sınıflarda salt okunur tüm özelliklerini sırasında ön şema doğrulaması bilgi <xref:System.Xml.Schema> ad ait sonrası şema derleme bilgi.</span><span class="sxs-lookup"><span data-stu-id="7d337-108">All read and write properties of classes in the <xref:System.Xml.Schema> namespace belong to the pre-schema validation infoset, while all read-only properties of classes in the <xref:System.Xml.Schema> namespace belong to the post-schema compilation infoset.</span></span> <span data-ttu-id="7d337-109">Bu kural için özel ön şema doğrulaması bilgi ve sonrası şema derleme bilgi özellikleri aşağıdaki özellikleri durumdur.</span><span class="sxs-lookup"><span data-stu-id="7d337-109">The exception to this rule are the following properties, which are both pre-schema validation infoset and post-schema compilation infoset properties.</span></span>  
  
|<span data-ttu-id="7d337-110">örneği</span><span class="sxs-lookup"><span data-stu-id="7d337-110">Class</span></span>|<span data-ttu-id="7d337-111">Özellik</span><span class="sxs-lookup"><span data-stu-id="7d337-111">Property</span></span>|  
|-----------|--------------|  
|<xref:System.Xml.Schema.XmlSchemaObject>|<xref:System.Xml.Schema.XmlSchemaObject.Parent%2A>|  
|<xref:System.Xml.Schema.XmlSchema>|<span data-ttu-id="7d337-112"><xref:System.Xml.Schema.XmlSchema.AttributeFormDefault%2A>, <xref:System.Xml.Schema.XmlSchema.BlockDefault%2A>, <xref:System.Xml.Schema.XmlSchema.ElementFormDefault%2A>, <xref:System.Xml.Schema.XmlSchema.FinalDefault%2A>, <xref:System.Xml.Schema.XmlSchema.TargetNamespace%2A></span><span class="sxs-lookup"><span data-stu-id="7d337-112"><xref:System.Xml.Schema.XmlSchema.AttributeFormDefault%2A>, <xref:System.Xml.Schema.XmlSchema.BlockDefault%2A>, <xref:System.Xml.Schema.XmlSchema.ElementFormDefault%2A>, <xref:System.Xml.Schema.XmlSchema.FinalDefault%2A>, <xref:System.Xml.Schema.XmlSchema.TargetNamespace%2A></span></span>|  
|<xref:System.Xml.Schema.XmlSchemaExternal>|<xref:System.Xml.Schema.XmlSchemaExternal.Schema%2A>|  
|<xref:System.Xml.Schema.XmlSchemaAttributeGroup>|<xref:System.Xml.Schema.XmlSchemaAttributeGroup.AnyAttribute%2A>|  
|<xref:System.Xml.Schema.XmlSchemaParticle>|<span data-ttu-id="7d337-113"><xref:System.Xml.Schema.XmlSchemaParticle.MaxOccurs%2A>, <xref:System.Xml.Schema.XmlSchemaParticle.MinOccurs%2A></span><span class="sxs-lookup"><span data-stu-id="7d337-113"><xref:System.Xml.Schema.XmlSchemaParticle.MaxOccurs%2A>, <xref:System.Xml.Schema.XmlSchemaParticle.MinOccurs%2A></span></span>|  
|<xref:System.Xml.Schema.XmlSchemaComplexType>|<xref:System.Xml.Schema.XmlSchemaComplexType.AnyAttribute%2A>|  
  
 <span data-ttu-id="7d337-114">Örneğin, <xref:System.Xml.Schema.XmlSchemaElement> ve <xref:System.Xml.Schema.XmlSchemaComplexType> sınıflarının her ikisi de sahip `BlockResolved` ve `FinalResolved` özellikleri.</span><span class="sxs-lookup"><span data-stu-id="7d337-114">For example, the <xref:System.Xml.Schema.XmlSchemaElement> and <xref:System.Xml.Schema.XmlSchemaComplexType> classes both have `BlockResolved` and `FinalResolved` properties.</span></span> <span data-ttu-id="7d337-115">Bu özelliklerin değerlerini tutmak için kullanılan `Block` ve `Final` şeması derlenmiş ve doğrulanmış sonra özellikleri.</span><span class="sxs-lookup"><span data-stu-id="7d337-115">These properties are used to hold the values for the `Block` and `Final` properties after the schema has been compiled and validated.</span></span> <span data-ttu-id="7d337-116">`BlockResolved`ve `FinalResolved` sonrası şema derleme bilgi parçası olan salt okunur özelliklerdir.</span><span class="sxs-lookup"><span data-stu-id="7d337-116">`BlockResolved` and `FinalResolved` are read-only properties that are part of the post-schema compilation infoset.</span></span>  
  
 <span data-ttu-id="7d337-117">Aşağıdaki örnekte gösterildiği <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A> özelliği <xref:System.Xml.Schema.XmlSchemaElement> sınıf kümesi şema doğrulama sonra.</span><span class="sxs-lookup"><span data-stu-id="7d337-117">The following example shows the <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A> property of the <xref:System.Xml.Schema.XmlSchemaElement> class set after validating the schema.</span></span> <span data-ttu-id="7d337-118">Doğrulama önce özelliği içeren bir `null` , başvuru ve <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> türünün adını söz konusu ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="7d337-118">Before validation, the property contains a `null` reference, and the <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> is set to the name of the type in question.</span></span> <span data-ttu-id="7d337-119">Doğrulama sonrasında <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> geçerli bir tür olarak çözümlenir ve tür nesnesi aracılığıyla kullanılabilir <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="7d337-119">After validation, the <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> is resolved to a valid type, and the type object is available through the <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A> property.</span></span>  
  
 [!code-cpp[PsciSample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/PsciSample/CPP/PsciSample.cpp#1)]
 [!code-csharp[PsciSample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/PsciSample/CS/PsciSample.cs#1)]
 [!code-vb[PsciSample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/PsciSample/VB/PsciSample.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="7d337-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7d337-120">See Also</span></span>  
 [<span data-ttu-id="7d337-121">XML şema nesne modeli (SOM)</span><span class="sxs-lookup"><span data-stu-id="7d337-121">XML Schema Object Model (SOM)</span></span>](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)
