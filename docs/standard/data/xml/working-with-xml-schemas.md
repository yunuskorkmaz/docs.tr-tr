---
title: "XML şemaları ile çalışma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bbbcc70c-bf9a-4f6a-af72-1bab5384a187
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 6cba66a0d8291592b082898d20ca780c8067401e
ms.sourcegitcommit: ba765893e3efcece67d99fd6d5ce0074b050d1d9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/02/2018
---
# <a name="working-with-xml-schemas"></a><span data-ttu-id="bebde-102">XML şemaları ile çalışma</span><span class="sxs-lookup"><span data-stu-id="bebde-102">Working with XML Schemas</span></span>
<span data-ttu-id="bebde-103">Bir XML belgesi yanı sıra kendi öğesi ilişkileri, veri türleri ve içerik kısıtlamaları yapısını tanımlamak için bir belge türü tanımı (DTD) veya XML Şeması Tanım Dili (XSD) şeması kullanın.</span><span class="sxs-lookup"><span data-stu-id="bebde-103">To define the structure of an XML document, as well as its element relationships, data types, and content constraints, you use a document type definition (DTD) or XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="bebde-104">Bir XML belgesi World Wide Web Konsorsiyumu (W3C) Genişletilebilir İşaretleme Dili (XML) 1.0 önerisi tarafından tanımlanan tüm söz dizimi gereksinimleri karşılıyorsa doğru biçimlendirilmiş olarak kabul edilir olsa da her ikisini de olmadığı sürece, geçerli doğru biçimlendirilmiş olarak kabul edilmez ve kendi DTD ya da şema tarafından tanımlanmış kısıtlamalar için uygundur.</span><span class="sxs-lookup"><span data-stu-id="bebde-104">Although an XML document is considered to be well-formed if it meets all the syntactical requirements defined by the World Wide Web Consortium (W3C) Extensible Markup Language (XML) 1.0 Recommendation, it is not considered valid unless it is both well-formed and conforms to the constraints defined by its DTD or schema.</span></span> <span data-ttu-id="bebde-105">Bu nedenle, tüm geçerli XML belgeleri doğru biçimlendirilmiş olsa da, tüm doğru biçimlendirilmiş XML belgeleri geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="bebde-105">Therefore, although all valid XML documents are well-formed, not all well-formed XML documents are valid.</span></span>  
  
 <span data-ttu-id="bebde-106">XML hakkında daha fazla bilgi için bkz: [W3C XML 1.0 öneri](https://www.w3.org/TR/REC-xml/).</span><span class="sxs-lookup"><span data-stu-id="bebde-106">For more information about XML, see the [W3C XML 1.0 Recommendation](https://www.w3.org/TR/REC-xml/).</span></span> <span data-ttu-id="bebde-107">XML şeması hakkında daha fazla bilgi için bkz: [W3C XML Şeması Kısım 1: yapıları öneri](https://www.w3.org/TR/xmlschema-1/) ve [W3C XML Şeması Kısım 2: veri türleri öneri](https://www.w3.org/TR/xmlschema-2/) öneriler.</span><span class="sxs-lookup"><span data-stu-id="bebde-107">For more information about XML Schema, see the [W3C XML Schema Part 1: Structures Recommendation](https://www.w3.org/TR/xmlschema-1/) and the [W3C XML Schema Part 2: Datatypes Recommendation](https://www.w3.org/TR/xmlschema-2/) recommendations.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bebde-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="bebde-108">In This Section</span></span>  
 [<span data-ttu-id="bebde-109">XML Şema Nesne Modeli (SOM)</span><span class="sxs-lookup"><span data-stu-id="bebde-109">XML Schema Object Model (SOM)</span></span>](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)  
 <span data-ttu-id="bebde-110">Şema nesne modeli (SOM) içinde ele alınmıştır <xref:System.Xml.Schema?displayProperty=nameWithType> bir şema tanım dili (XSD) şeması bir dosya veya program aracılığıyla okumaya izin veren bir dizi sınıfları sağlar ad alanını bir şema bellek içi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="bebde-110">Discusses the Schema Object Model (SOM) in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace that provides a set of classes that allows you to read a Schema definition language (XSD) schema from a file or programmatically create a schema in-memory.</span></span>  
  
 [<span data-ttu-id="bebde-111">Şema Derleme için XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="bebde-111">XmlSchemaSet for Schema Compilation</span></span>](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
 <span data-ttu-id="bebde-112">Anlatılmaktadır <xref:System.Xml.Schema.XmlSchemaSet> sınıfı bir önbellek burada XSD şemaları depolanabilir ve doğrulandı.</span><span class="sxs-lookup"><span data-stu-id="bebde-112">Discusses the <xref:System.Xml.Schema.XmlSchemaSet> class that is a cache where XSD schemas can be stored and validated.</span></span>  
  
 [<span data-ttu-id="bebde-113">XmlSchemaValidator Gönderim Temelli Doğrulaması</span><span class="sxs-lookup"><span data-stu-id="bebde-113">XmlSchemaValidator Push-Based Validation</span></span>](../../../../docs/standard/data/xml/xmlschemavalidator-push-based-validation.md)  
 <span data-ttu-id="bebde-114">Anlatılmaktadır <xref:System.Xml.Schema.XmlSchemaValidator> gönderim tabanlı bir biçimde XSD şemaları karşı XML verileri doğrulamak için verimli, yüksek performanslı bir mekanizma sağlayan sınıf.</span><span class="sxs-lookup"><span data-stu-id="bebde-114">Discusses the <xref:System.Xml.Schema.XmlSchemaValidator> class that provides an efficient, high-performance mechanism to validate XML data against XSD schemas in a push-based manner.</span></span>  
  
 [<span data-ttu-id="bebde-115">XML Şemasından Çıkarım Yapma</span><span class="sxs-lookup"><span data-stu-id="bebde-115">Inferring an XML Schema</span></span>](../../../../docs/standard/data/xml/inferring-an-xml-schema.md)  
 <span data-ttu-id="bebde-116">Nasıl kullanılacağı açıklanır <xref:System.Xml.Schema.XmlSchemaInference> bir XML belgesi yapısından XSD şemasını sınıfı.</span><span class="sxs-lookup"><span data-stu-id="bebde-116">Discusses how to use the <xref:System.Xml.Schema.XmlSchemaInference> class to infer an XSD schema from the structure of an XML document.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="bebde-117">Başvuru</span><span class="sxs-lookup"><span data-stu-id="bebde-117">Reference</span></span>  
 <span data-ttu-id="bebde-118"><xref:System.Xml.Schema.XmlSchemaSet> &#124; <xref:System.Xml.Schema.XmlSchemaInference> &#124; <xref:System.Xml.XmlReader></span><span class="sxs-lookup"><span data-stu-id="bebde-118"><xref:System.Xml.Schema.XmlSchemaSet> &#124; <xref:System.Xml.Schema.XmlSchemaInference> &#124; <xref:System.Xml.XmlReader></span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="bebde-119">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="bebde-119">Related Sections</span></span>  
 [<span data-ttu-id="bebde-120">DOM’da XML Belgesi Doğrulama</span><span class="sxs-lookup"><span data-stu-id="bebde-120">Validating an XML Document in the DOM</span></span>](../../../../docs/standard/data/xml/validating-an-xml-document-in-the-dom.md)  
 <span data-ttu-id="bebde-121">XML belge nesne modeli (DOM) doğrulamak nasıl ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bebde-121">Discusses how to validate the XML in the Document Object Model (DOM).</span></span> <span data-ttu-id="bebde-122">DOM yüklenmiş olarak XML doğrulamak veya önceden doğrulanmamış bir XML belgesi DOM içinde doğrula</span><span class="sxs-lookup"><span data-stu-id="bebde-122">You can validate the XML as it is loaded into the DOM, or validate a previously unvalidated XML document in the DOM.</span></span>  
  
 [<span data-ttu-id="bebde-123">XPathNavigator Kullanarak Şema Doğrulama</span><span class="sxs-lookup"><span data-stu-id="bebde-123">Schema Validation using XPathNavigator</span></span>](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md)  
 <span data-ttu-id="bebde-124">XML olan doğrulamak nasıl gittiğinizde ve kullanarak düzenlenebilir anlatılmaktadır <xref:System.Xml.XPath.XPathNavigator> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="bebde-124">Discusses how to validate XML being navigated and edited using the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>
