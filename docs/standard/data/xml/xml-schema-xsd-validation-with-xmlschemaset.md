---
title: XmlSchemaSet ile XML Şeması (XSD) Doğrulaması
description: .NET 'te bir XmlSchemaSet sınıfı kullanarak XML belgelerini bir XML şeması tanım dili (XSD) şemasına göre doğrulamayı öğrenin.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 359b10eb-ec05-4cc6-ac96-c2b060afc4de
ms.openlocfilehash: 5963ba1b382740b1774c944b74c6a54b13db4f76
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554521"
---
# <a name="xml-schema-xsd-validation-with-xmlschemaset"></a><span data-ttu-id="094e1-103">XmlSchemaSet ile XML şeması (XSD) doğrulaması</span><span class="sxs-lookup"><span data-stu-id="094e1-103">XML schema (XSD) validation with XmlSchemaSet</span></span>

<span data-ttu-id="094e1-104">XML belgeleri, bir XML şeması tanım dili (XSD) şemasına göre doğrulanabilir <xref:System.Xml.Schema.XmlSchemaSet> .</span><span class="sxs-lookup"><span data-stu-id="094e1-104">XML documents can be validated against an XML schema definition language (XSD) schema in an <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
## <a name="validate-xml-documents"></a><span data-ttu-id="094e1-105">XML belgelerini doğrula</span><span class="sxs-lookup"><span data-stu-id="094e1-105">Validate XML documents</span></span>  
 <span data-ttu-id="094e1-106">XML belgeleri, <xref:System.Xml.XmlReader.Create%2A> sınıfının yöntemi tarafından onaylanır <xref:System.Xml.XmlReader> .</span><span class="sxs-lookup"><span data-stu-id="094e1-106">XML documents are validated by the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> class.</span></span> <span data-ttu-id="094e1-107">XML belgesini doğrulamak için, XML <xref:System.Xml.XmlReaderSettings> belgesi doğrulanacak BIR XML şeması tanım dili (xsd) şeması içeren bir nesne oluşturun.</span><span class="sxs-lookup"><span data-stu-id="094e1-107">To validate an XML document, construct an <xref:System.Xml.XmlReaderSettings> object that contains an XML schema definition language (XSD) schema with which to validate the XML document.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="094e1-108"><xref:System.Xml.Schema>Ad alanı, [LINQ to XML (C#)](../../linq/linq-xml-overview.md) ve [LINQ to XML (VISUAL BASIC)](../../linq/linq-xml-overview.md)kullanırken bir xml ağacının xsd dosyasına karşı doğrulanmasını kolaylaştıran uzantı yöntemleri içerir.</span><span class="sxs-lookup"><span data-stu-id="094e1-108">The <xref:System.Xml.Schema> namespace contains extension methods that make it easy to validate an XML tree against an XSD file when using [LINQ to XML (C#)](../../linq/linq-xml-overview.md) and [LINQ to XML (Visual Basic)](../../linq/linq-xml-overview.md).</span></span> <span data-ttu-id="094e1-109">LINQ to XML ile XML belgelerinin doğrulanması hakkında daha fazla bilgi için bkz. [xsd (LINQ to XML) (C#)](../../linq/validate-xsd.md) ve [nasıl yapılır: XSD kullanarak doğrulama (LINQ to XML) (Visual Basic)](../../linq/validate-xsd.md).</span><span class="sxs-lookup"><span data-stu-id="094e1-109">For more information on validating XML documents with LINQ to XML, see [How to validate using XSD (LINQ to XML) (C#)](../../linq/validate-xsd.md) and [How to: Validate Using XSD (LINQ to XML) (Visual Basic)](../../linq/validate-xsd.md).</span></span>
  
 <span data-ttu-id="094e1-110">Tek bir şema veya bir şema kümesi (olarak <xref:System.Xml.Schema.XmlSchemaSet> ) öğesine bir <xref:System.Xml.Schema.XmlSchemaSet> parametre olarak bir parametresi geçirerek öğesine eklenebilir <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> <xref:System.Xml.Schema.XmlSchemaSet> .</span><span class="sxs-lookup"><span data-stu-id="094e1-110">An individual schema or a set of schemas (as an <xref:System.Xml.Schema.XmlSchemaSet>) can be added to an <xref:System.Xml.Schema.XmlSchemaSet> by passing either one as a parameter to the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method of <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="094e1-111">Bir belge doğrulanırken, belgenin hedef ad alanı, şema kümesindeki şemanın hedef ad alanıyla aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="094e1-111">When validating a document the target namespace of the document must match the target namespace of the schema in the schema set.</span></span>  
  
 <span data-ttu-id="094e1-112">Aşağıda örnek bir XML belgesi verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="094e1-112">The following is an example XML document.</span></span>  
  
 [!code-xml[XSDInference Examples #5](../../../../samples/snippets/xml/VS_Snippets_Data/XSDInference Examples/XML/contosoBooks.xml#5)]  
  
 <span data-ttu-id="094e1-113">Örnek XML belgesini doğrulayan şema aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="094e1-113">The following is the schema that validates the example XML document.</span></span>  
  
 [!code-xml[XSDInference Examples #6](../../../../samples/snippets/xml/VS_Snippets_Data/XSDInference Examples/XML/contosoBooks.xsd#6)]  
  
 <span data-ttu-id="094e1-114">Aşağıdaki kod örneğinde, yukarıdaki şema <xref:System.Xml.XmlReaderSettings.Schemas%2A> nesnenin özelliğine eklenir <xref:System.Xml.XmlReaderSettings> .</span><span class="sxs-lookup"><span data-stu-id="094e1-114">In the code example that follows, the schema above is added to the <xref:System.Xml.XmlReaderSettings.Schemas%2A> property of the <xref:System.Xml.XmlReaderSettings> object.</span></span> <span data-ttu-id="094e1-115"><xref:System.Xml.XmlReaderSettings>Nesnesi, <xref:System.Xml.XmlReader.Create%2A> <xref:System.Xml.XmlReader> Yukarıdaki XML belgesini doğrulayan nesnesinin yöntemine bir parametre olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="094e1-115">The <xref:System.Xml.XmlReaderSettings> object is passed as a parameter to the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> object, which validates the XML document above.</span></span>  
  
 <span data-ttu-id="094e1-116"><xref:System.Xml.XmlReaderSettings.ValidationType%2A>Nesnesinin özelliği, <xref:System.Xml.XmlReaderSettings> `Schema` nesne yöntemi tarafından XML belgesinin doğrulanmasını zorlamak için olarak ayarlanır <xref:System.Xml.XmlReader.Create%2A> <xref:System.Xml.XmlReader> .</span><span class="sxs-lookup"><span data-stu-id="094e1-116">The <xref:System.Xml.XmlReaderSettings.ValidationType%2A> property of the <xref:System.Xml.XmlReaderSettings> object is set to `Schema` to enforce validation of the XML document by the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="094e1-117"><xref:System.Xml.Schema.ValidationEventHandler> <xref:System.Xml.XmlReaderSettings> <xref:System.Xml.Schema.XmlSeverityType.Warning> <xref:System.Xml.Schema.XmlSeverityType.Error> , Hem XML belgesi hem de şemanın doğrulama işlemi sırasında bulunan hatalara göre oluşan herhangi bir veya olayı işlemek için nesnesine eklenir.</span><span class="sxs-lookup"><span data-stu-id="094e1-117">A <xref:System.Xml.Schema.ValidationEventHandler> is added to the <xref:System.Xml.XmlReaderSettings> object to handle any <xref:System.Xml.Schema.XmlSeverityType.Warning> or <xref:System.Xml.Schema.XmlSeverityType.Error> events raised by errors found during the validation process of both the XML document and the schema.</span></span>  
  
 [!code-cpp[XmlSchemaSetOverall Example #1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaSetOverall Example/CPP/xmlschemasetexample.cpp#1)]
 [!code-csharp[XmlSchemaSetOverall Example #1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaSetOverall Example/CS/xmlschemasetexample.cs#1)]
 [!code-vb[XmlSchemaSetOverall Example #1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaSetOverall Example/VB/xmlschemasetexample.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="094e1-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="094e1-118">See also</span></span>

- [<span data-ttu-id="094e1-119">Şema Derleme için XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="094e1-119">XmlSchemaSet for Schema Compilation</span></span>](xmlschemaset-for-schema-compilation.md)
- [<span data-ttu-id="094e1-120">XML Şemalarıyla Çalışma</span><span class="sxs-lookup"><span data-stu-id="094e1-120">Working with XML Schemas</span></span>](working-with-xml-schemas.md)
