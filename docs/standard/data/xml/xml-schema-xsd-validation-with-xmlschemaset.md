---
title: XML Şeması (XSD) doğrulama XmlSchemaSet ile
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 359b10eb-ec05-4cc6-ac96-c2b060afc4de
caps.latest.revision: 3
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: f18852411d733d12bcbbdba2b64bc2f134ea061c
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
---
# <a name="xml-schema-xsd-validation-with-xmlschemaset"></a><span data-ttu-id="2dcb1-102">XML Şeması (XSD) doğrulama XmlSchemaSet ile</span><span class="sxs-lookup"><span data-stu-id="2dcb1-102">XML Schema (XSD) Validation with XmlSchemaSet</span></span>
<span data-ttu-id="2dcb1-103">XML belgeleri doğrulanmış bir XML Şeması Tanım Dili (XSD) şemasında karşı bir <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="2dcb1-103">XML documents can be validated against an XML schema definition language (XSD) schema in an <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
## <a name="validating-xml-documents"></a><span data-ttu-id="2dcb1-104">XML belgeleri doğrulanıyor</span><span class="sxs-lookup"><span data-stu-id="2dcb1-104">Validating XML Documents</span></span>  
 <span data-ttu-id="2dcb1-105">XML belgeleri tarafından doğrulanır <xref:System.Xml.XmlReader.Create%2A> yöntemi <xref:System.Xml.XmlReader> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="2dcb1-105">XML documents are validated by the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> class.</span></span> <span data-ttu-id="2dcb1-106">Bir XML belgesi doğrulamak için oluşturmak bir <xref:System.Xml.XmlReaderSettings> bir XML Şeması Tanım Dili (XSD) şemasıyla XML belgesi doğrulamak içeren nesne.</span><span class="sxs-lookup"><span data-stu-id="2dcb1-106">To validate an XML document, construct an <xref:System.Xml.XmlReaderSettings> object that contains an XML schema definition language (XSD) schema with which to validate the XML document.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2dcb1-107"><xref:System.Xml.Schema> Ad alanı, kolaylaştıran kullanırken bir XML ağacı bir XSD dosyası karşı doğrulamak genişletme yöntemleri içerir [LINQ-XML](https://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13).</span><span class="sxs-lookup"><span data-stu-id="2dcb1-107">The <xref:System.Xml.Schema> namespace contains extension methods that make it easy to validate an XML tree against an XSD file when using [LINQ to XML](https://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13).</span></span> <span data-ttu-id="2dcb1-108">LINQ-XML ile XML belgelerini doğrulama ile ilgili daha fazla bilgi için bkz: [nasıl yapılır: kullanarak XSD doğrulama](https://msdn.microsoft.com/library/481a97fa-6e96-46f2-8c9a-415555fac33b).</span><span class="sxs-lookup"><span data-stu-id="2dcb1-108">For more information on validating XML documents with LINQ to XML, see [How to: Validate Using XSD](https://msdn.microsoft.com/library/481a97fa-6e96-46f2-8c9a-415555fac33b).</span></span>  
  
 <span data-ttu-id="2dcb1-109">Tek bir şema veya şema kümesine (olarak bir <xref:System.Xml.Schema.XmlSchemaSet>) eklenebilir bir <xref:System.Xml.Schema.XmlSchemaSet> ya da bir parametre olarak geçirerek <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> yöntemi <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="2dcb1-109">An individual schema or a set of schemas (as an <xref:System.Xml.Schema.XmlSchemaSet>) can be added to an <xref:System.Xml.Schema.XmlSchemaSet> by passing either one as a parameter to the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method of <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="2dcb1-110">Bir belge doğrularken belgenin hedef ad alanı şema kümesini şemada hedef ad alanı eşleşmesi gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="2dcb1-110">Note that when validating a document the target namespace of the document must match the target namespace of the schema in the schema set.</span></span>  
  
 <span data-ttu-id="2dcb1-111">Aşağıdaki örnek XML dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="2dcb1-111">The following is an example XML document.</span></span>  
  
 [!code-xml[XSDInference Examples#5](../../../../samples/snippets/xml/VS_Snippets_Data/XSDInference Examples/XML/contosoBooks.xml#5)]  
  
 <span data-ttu-id="2dcb1-112">Bu örnek XML belge doğrular şema verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="2dcb1-112">The following is the schema that validates the example XML document.</span></span>  
  
 [!code-xml[XSDInference Examples#6](../../../../samples/snippets/xml/VS_Snippets_Data/XSDInference Examples/XML/contosoBooks.xsd#6)]  
  
 <span data-ttu-id="2dcb1-113">Aşağıdaki kod örneğinde, yukarıdaki şemayı eklenen <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.XmlReaderSettings.Schemas%2A> özelliği <xref:System.Xml.XmlReaderSettings> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="2dcb1-113">In the code example that follows, the schema above is added to the <xref:System.Xml.Schema.XmlSchemaSet><xref:System.Xml.XmlReaderSettings.Schemas%2A> property of the <xref:System.Xml.XmlReaderSettings> object.</span></span> <span data-ttu-id="2dcb1-114"><xref:System.Xml.XmlReaderSettings> Nesnesini parametre olarak geçirilen <xref:System.Xml.XmlReader.Create%2A> yöntemi <xref:System.Xml.XmlReader> yukarıdaki XML belgesi doğrular nesnesi.</span><span class="sxs-lookup"><span data-stu-id="2dcb1-114">The <xref:System.Xml.XmlReaderSettings> object is passed as a parameter to the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> object, which validates the XML document above.</span></span>  
  
 <span data-ttu-id="2dcb1-115"><xref:System.Xml.XmlReaderSettings.ValidationType%2A> Özelliği <xref:System.Xml.XmlReaderSettings> nesne ayarlanmış `Schema` XML belgesi tarafından doğrulanmasını zorlamak için <xref:System.Xml.XmlReader.Create%2A> yöntemi <xref:System.Xml.XmlReader> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="2dcb1-115">The <xref:System.Xml.XmlReaderSettings.ValidationType%2A> property of the <xref:System.Xml.XmlReaderSettings> object is set to `Schema` to enforce validation of the XML document by the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="2dcb1-116">A <xref:System.Xml.Schema.ValidationEventHandler> eklenen <xref:System.Xml.XmlReaderSettings> herhangi işlenecek nesne <xref:System.Xml.Schema.XmlSeverityType.Warning> veya <xref:System.Xml.Schema.XmlSeverityType.Error> XML belgesi ve şema doğrulama işlemi sırasında bulunan hatalar tarafından başlatılan olayları.</span><span class="sxs-lookup"><span data-stu-id="2dcb1-116">A <xref:System.Xml.Schema.ValidationEventHandler> is added to the <xref:System.Xml.XmlReaderSettings> object to handle any <xref:System.Xml.Schema.XmlSeverityType.Warning> or <xref:System.Xml.Schema.XmlSeverityType.Error> events raised by errors found during the validation process of both the XML document and the schema.</span></span>  
  
 [!code-cpp[XmlSchemaSetOverall Example#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaSetOverall Example/CPP/xmlschemasetexample.cpp#1)]
 [!code-csharp[XmlSchemaSetOverall Example#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaSetOverall Example/CS/xmlschemasetexample.cs#1)]
 [!code-vb[XmlSchemaSetOverall Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaSetOverall Example/VB/xmlschemasetexample.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="2dcb1-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2dcb1-117">See Also</span></span>  
 [<span data-ttu-id="2dcb1-118">Şema Derleme için XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="2dcb1-118">XmlSchemaSet for Schema Compilation</span></span>](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
 [<span data-ttu-id="2dcb1-119">XML Şemalarıyla Çalışma</span><span class="sxs-lookup"><span data-stu-id="2dcb1-119">Working with XML Schemas</span></span>](../../../../docs/standard/data/xml/working-with-xml-schemas.md)
