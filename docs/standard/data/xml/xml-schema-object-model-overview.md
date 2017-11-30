---
title: "XML şema nesne modeline genel bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 896a1e12-5655-42c6-8cdd-89c12862b34b
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6a06de3f8fb6351d340e1c8f1bfe8f4105967e25
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="xml-schema-object-model-overview"></a><span data-ttu-id="5b0a0-102">XML şema nesne modeline genel bakış</span><span class="sxs-lookup"><span data-stu-id="5b0a0-102">XML Schema Object Model Overview</span></span>
<span data-ttu-id="5b0a0-103">Microsoft .NET Framework şema nesne modeli (SOM) oluşturmak, düzenlemek ve şemaları program aracılığıyla doğrulayın olanak sağlayan zengin bir API'dir.</span><span class="sxs-lookup"><span data-stu-id="5b0a0-103">The Schema Object Model (SOM) in the Microsoft .NET Framework is a rich API that allows you to create, edit, and validate schemas programmatically.</span></span> <span data-ttu-id="5b0a0-104">SOM XML Şeması belgelerinde benzer şekilde XML belgelerini belge nesne modeli (DOM) çalıştığı şekilde çalışır.</span><span class="sxs-lookup"><span data-stu-id="5b0a0-104">The SOM operates on XML schema documents similarly to the way the Document Object Model (DOM) operates on XML documents.</span></span> <span data-ttu-id="5b0a0-105">XML Şeması belgelerinde, bir kez SOM yüklenen geçerlilik XML'sini şemaya uyacak diğer XML belgelerinin ve yapısı hakkında anlam ifade geçerli XML dosyalarıdır.</span><span class="sxs-lookup"><span data-stu-id="5b0a0-105">XML schema documents are valid XML files that, once loaded into the SOM, convey meaning about the structure and validity of other XML documents which conform to the schema.</span></span>  
  
 <span data-ttu-id="5b0a0-106">Bir şema yapısı veya modeli belirli bir şema için XML belgelerinin belirterek XML belgelerinin bir sınıf tanımlayan bir XML belgesi değil.</span><span class="sxs-lookup"><span data-stu-id="5b0a0-106">A schema is an XML document that defines a class of XML documents by specifying the structure or model of XML documents for a particular schema.</span></span> <span data-ttu-id="5b0a0-107">Bir şema XML belge içeriklerini kısıtlamalar tanımlar ve uyumlu XML belge şeması ile söz konusu şeması geçerli kabul edilmesi için izlemeniz gereken sözlüğünü (kuralları veya dilbilgisi) açıklar.</span><span class="sxs-lookup"><span data-stu-id="5b0a0-107">A schema identifies the constraints on the content of the XML documents, and describes the vocabulary (rules or grammar) that compliant XML documents must follow in order to be considered schema-valid with that particular schema.</span></span> <span data-ttu-id="5b0a0-108">XML belgesinin doğrulama belge şeması tarafından belirtilen dilbilgisi uymasını sağlar işlemidir.</span><span class="sxs-lookup"><span data-stu-id="5b0a0-108">Validation of an XML document is the process that ensures that the document conforms to the grammar specified by the schema.</span></span>  
  
 <span data-ttu-id="5b0a0-109">Aşağıdaki yolları .NET Framework'teki SOM API oluşturmak, düzenlemek ve şemaları doğrulayın sağlar geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="5b0a0-109">The following are ways the SOM API in the .NET Framework enables you to create, edit, and validate schemas.</span></span>  
  
-   <span data-ttu-id="5b0a0-110">Yük ve geçerli şemalar için ve dosyalarını kaydedin.</span><span class="sxs-lookup"><span data-stu-id="5b0a0-110">Load and save valid schemas to and from files.</span></span>  
  
-   <span data-ttu-id="5b0a0-111">Kesin türü belirtilmiş sınıflarını kullanarak bellek içi şemalarını oluşturun.</span><span class="sxs-lookup"><span data-stu-id="5b0a0-111">Create in-memory schemas using strongly typed classes.</span></span>  
  
-   <span data-ttu-id="5b0a0-112">Etkileşim <xref:System.Xml.Schema.XmlSchemaSet> önbelleğe derlemek ve şemaları almak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="5b0a0-112">Interact with the <xref:System.Xml.Schema.XmlSchemaSet> class to cache, compile, and retrieve schemas.</span></span>  
  
-   <span data-ttu-id="5b0a0-113">Etkileşim <xref:System.Xml.XmlReader.Create%2A> yöntemi <xref:System.Xml.XmlReader> XML örneği belgeleri şemalara karşı doğrulamak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="5b0a0-113">Interact with the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> class to validate XML instance documents against schemas.</span></span>  
  
-   <span data-ttu-id="5b0a0-114">Düzenleyiciler oluşturmak ve şemaları sürdürmek için oluşturun.</span><span class="sxs-lookup"><span data-stu-id="5b0a0-114">Build editors for creating and maintaining schemas.</span></span>  
  
-   <span data-ttu-id="5b0a0-115">Dinamik olarak derlendiğini ve XML örneği belgelerinin doğrulamada kullanmak için kaydedilen bir şema düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="5b0a0-115">Dynamically edit a schema that can be complied and saved for use in the validation of XML instance documents.</span></span>  
  
## <a name="the-schema-object-model"></a><span data-ttu-id="5b0a0-116">Şema nesnesi modeli</span><span class="sxs-lookup"><span data-stu-id="5b0a0-116">The Schema Object Model</span></span>  
 <span data-ttu-id="5b0a0-117">Sınıflarda kapsamlı bir kümesini SOM oluşan <xref:System.Xml.Schema?displayProperty=nameWithType> bir XML Şeması öğeleri karşılık gelen ad alanı.</span><span class="sxs-lookup"><span data-stu-id="5b0a0-117">The SOM consists of an extensive set of classes in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace corresponding to the elements in an XML schema.</span></span> <span data-ttu-id="5b0a0-118">Örneğin, `<xsd:schema>...</xsd:schema>` öğesi eşler için <xref:System.Xml.Schema.XmlSchema?displayProperty=nameWithType> sınıfı ve içinde bulunan tüm bilgileri bir `<xsd:schema/>` öğesi kullanarak temsil edilen <xref:System.Xml.Schema.XmlSchema> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="5b0a0-118">For example, the `<xsd:schema>...</xsd:schema>` element maps to the <xref:System.Xml.Schema.XmlSchema?displayProperty=nameWithType> class, and all the information that can be contained within an `<xsd:schema/>` element can be represented using the <xref:System.Xml.Schema.XmlSchema> class.</span></span> <span data-ttu-id="5b0a0-119">Benzer şekilde, `<xsd:element>...</xsd:element>` ve `<xsd:attribute>...</xsd:attribute>` öğeleri eşlemek için <xref:System.Xml.Schema.XmlSchemaElement?displayProperty=nameWithType> ve <xref:System.Xml.Schema.XmlSchemaAttribute?displayProperty=nameWithType> sırasıyla sınıfları.</span><span class="sxs-lookup"><span data-stu-id="5b0a0-119">Similarly, the `<xsd:element>...</xsd:element>` and `<xsd:attribute>...</xsd:attribute>` elements map to the <xref:System.Xml.Schema.XmlSchemaElement?displayProperty=nameWithType> and <xref:System.Xml.Schema.XmlSchemaAttribute?displayProperty=nameWithType> classes respectively.</span></span> <span data-ttu-id="5b0a0-120">Bu eşleme XML Şeması nesne modelinde oluşturma XML Şeması tüm öğeler için devam <xref:System.Xml.Schema> ad alanı Aşağıdaki diyagramda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="5b0a0-120">This mapping continues for all the elements of an XML schema creating an XML schema object model in the <xref:System.Xml.Schema> namespace illustrated in the diagram that follows.</span></span>  
  
 <span data-ttu-id="5b0a0-121">![System.Xml.Schema nesne modeli](../../../../docs/standard/data/xml/media/xmlschemaobjmodeloverview.gif "XMLSchemaObjModelOverview")</span><span class="sxs-lookup"><span data-stu-id="5b0a0-121">![System.Xml.Schema Object Model](../../../../docs/standard/data/xml/media/xmlschemaobjmodeloverview.gif "XMLSchemaObjModelOverview")</span></span>  
  
 <span data-ttu-id="5b0a0-122">Her sınıf hakkında daha fazla bilgi için <xref:System.Xml.Schema> ad alanı, bkz: <xref:System.Xml.Schema> .NET Framework Sınıf Kitaplığı'nda ad alanı başvuru belgeleri.</span><span class="sxs-lookup"><span data-stu-id="5b0a0-122">For more information about each class in the <xref:System.Xml.Schema> namespace, see the <xref:System.Xml.Schema> namespace reference documentation in the .NET Framework class library.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b0a0-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5b0a0-123">See Also</span></span>  
 [<span data-ttu-id="5b0a0-124">Okuma ve yazma XML şemaları</span><span class="sxs-lookup"><span data-stu-id="5b0a0-124">Reading and Writing XML Schemas</span></span>](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)  
 [<span data-ttu-id="5b0a0-125">Yapı XML şemaları</span><span class="sxs-lookup"><span data-stu-id="5b0a0-125">Building XML Schemas</span></span>](../../../../docs/standard/data/xml/building-xml-schemas.md)  
 [<span data-ttu-id="5b0a0-126">XML şemaları çapraz geçiş yapma</span><span class="sxs-lookup"><span data-stu-id="5b0a0-126">Traversing XML Schemas</span></span>](../../../../docs/standard/data/xml/traversing-xml-schemas.md)  
 [<span data-ttu-id="5b0a0-127">XML şemaları düzenleme</span><span class="sxs-lookup"><span data-stu-id="5b0a0-127">Editing XML Schemas</span></span>](../../../../docs/standard/data/xml/editing-xml-schemas.md)  
 [<span data-ttu-id="5b0a0-128">Dahil olmak üzere veya XML şemalarını içeri aktarma</span><span class="sxs-lookup"><span data-stu-id="5b0a0-128">Including or Importing XML Schemas</span></span>](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)  
 [<span data-ttu-id="5b0a0-129">Şema derleme için XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="5b0a0-129">XmlSchemaSet for Schema Compilation</span></span>](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
 [<span data-ttu-id="5b0a0-130">Derleme sonrası şema bilgi</span><span class="sxs-lookup"><span data-stu-id="5b0a0-130">Post-Schema Compilation Infoset</span></span>](../../../../docs/standard/data/xml/post-schema-compilation-infoset.md)
