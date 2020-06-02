---
title: XmlSchemaSet ile XML Şeması (XSD) Doğrulaması
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 359b10eb-ec05-4cc6-ac96-c2b060afc4de
ms.openlocfilehash: 1729380180d4440ac107885a39eff706c7fc8e5c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290298"
---
# <a name="xml-schema-xsd-validation-with-xmlschemaset"></a><span data-ttu-id="3d107-102">XmlSchemaSet ile XML şeması (XSD) doğrulaması</span><span class="sxs-lookup"><span data-stu-id="3d107-102">XML schema (XSD) validation with XmlSchemaSet</span></span>

<span data-ttu-id="3d107-103">XML belgeleri, bir XML şeması tanım dili (XSD) şemasına göre doğrulanabilir <xref:System.Xml.Schema.XmlSchemaSet> .</span><span class="sxs-lookup"><span data-stu-id="3d107-103">XML documents can be validated against an XML schema definition language (XSD) schema in an <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
## <a name="validate-xml-documents"></a><span data-ttu-id="3d107-104">XML belgelerini doğrula</span><span class="sxs-lookup"><span data-stu-id="3d107-104">Validate XML documents</span></span>  
 <span data-ttu-id="3d107-105">XML belgeleri, <xref:System.Xml.XmlReader.Create%2A> sınıfının yöntemi tarafından onaylanır <xref:System.Xml.XmlReader> .</span><span class="sxs-lookup"><span data-stu-id="3d107-105">XML documents are validated by the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> class.</span></span> <span data-ttu-id="3d107-106">XML belgesini doğrulamak için, XML <xref:System.Xml.XmlReaderSettings> belgesi doğrulanacak BIR XML şeması tanım dili (xsd) şeması içeren bir nesne oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3d107-106">To validate an XML document, construct an <xref:System.Xml.XmlReaderSettings> object that contains an XML schema definition language (XSD) schema with which to validate the XML document.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3d107-107"><xref:System.Xml.Schema>Ad alanı, [LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) ve [LINQ to XML (VISUAL BASIC)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md)kullanırken bir xml ağacının xsd dosyasına karşı doğrulanmasını kolaylaştıran uzantı yöntemleri içerir.</span><span class="sxs-lookup"><span data-stu-id="3d107-107">The <xref:System.Xml.Schema> namespace contains extension methods that make it easy to validate an XML tree against an XSD file when using [LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) and [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md).</span></span> <span data-ttu-id="3d107-108">LINQ to XML ile XML belgelerinin doğrulanması hakkında daha fazla bilgi için bkz. [xsd (LINQ to XML) (C#)](../../../csharp/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md) ve [nasıl yapılır: XSD kullanarak doğrulama (LINQ to XML) (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="3d107-108">For more information on validating XML documents with LINQ to XML, see [How to validate using XSD (LINQ to XML) (C#)](../../../csharp/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md) and [How to: Validate Using XSD (LINQ to XML) (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md).</span></span>
  
 <span data-ttu-id="3d107-109">Tek bir şema veya bir şema kümesi (olarak <xref:System.Xml.Schema.XmlSchemaSet> ) öğesine bir <xref:System.Xml.Schema.XmlSchemaSet> parametre olarak bir parametresi geçirerek öğesine eklenebilir <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> <xref:System.Xml.Schema.XmlSchemaSet> .</span><span class="sxs-lookup"><span data-stu-id="3d107-109">An individual schema or a set of schemas (as an <xref:System.Xml.Schema.XmlSchemaSet>) can be added to an <xref:System.Xml.Schema.XmlSchemaSet> by passing either one as a parameter to the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method of <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="3d107-110">Bir belge doğrulanırken, belgenin hedef ad alanı, şema kümesindeki şemanın hedef ad alanıyla aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3d107-110">When validating a document the target namespace of the document must match the target namespace of the schema in the schema set.</span></span>  
  
 <span data-ttu-id="3d107-111">Aşağıda örnek bir XML belgesi verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="3d107-111">The following is an example XML document.</span></span>  
  
 [!code-xml[XSDInference Examples #5](../../../../samples/snippets/xml/VS_Snippets_Data/XSDInference Examples/XML/contosoBooks.xml#5)]  
  
 <span data-ttu-id="3d107-112">Örnek XML belgesini doğrulayan şema aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="3d107-112">The following is the schema that validates the example XML document.</span></span>  
  
 [!code-xml[XSDInference Examples #6](../../../../samples/snippets/xml/VS_Snippets_Data/XSDInference Examples/XML/contosoBooks.xsd#6)]  
  
 <span data-ttu-id="3d107-113">Aşağıdaki kod örneğinde, yukarıdaki şema <xref:System.Xml.XmlReaderSettings.Schemas%2A> nesnenin özelliğine eklenir <xref:System.Xml.XmlReaderSettings> .</span><span class="sxs-lookup"><span data-stu-id="3d107-113">In the code example that follows, the schema above is added to the <xref:System.Xml.XmlReaderSettings.Schemas%2A> property of the <xref:System.Xml.XmlReaderSettings> object.</span></span> <span data-ttu-id="3d107-114"><xref:System.Xml.XmlReaderSettings>Nesnesi, <xref:System.Xml.XmlReader.Create%2A> <xref:System.Xml.XmlReader> Yukarıdaki XML belgesini doğrulayan nesnesinin yöntemine bir parametre olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="3d107-114">The <xref:System.Xml.XmlReaderSettings> object is passed as a parameter to the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> object, which validates the XML document above.</span></span>  
  
 <span data-ttu-id="3d107-115"><xref:System.Xml.XmlReaderSettings.ValidationType%2A>Nesnesinin özelliği, <xref:System.Xml.XmlReaderSettings> `Schema` nesne yöntemi tarafından XML belgesinin doğrulanmasını zorlamak için olarak ayarlanır <xref:System.Xml.XmlReader.Create%2A> <xref:System.Xml.XmlReader> .</span><span class="sxs-lookup"><span data-stu-id="3d107-115">The <xref:System.Xml.XmlReaderSettings.ValidationType%2A> property of the <xref:System.Xml.XmlReaderSettings> object is set to `Schema` to enforce validation of the XML document by the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="3d107-116"><xref:System.Xml.Schema.ValidationEventHandler> <xref:System.Xml.XmlReaderSettings> <xref:System.Xml.Schema.XmlSeverityType.Warning> <xref:System.Xml.Schema.XmlSeverityType.Error> , Hem XML belgesi hem de şemanın doğrulama işlemi sırasında bulunan hatalara göre oluşan herhangi bir veya olayı işlemek için nesnesine eklenir.</span><span class="sxs-lookup"><span data-stu-id="3d107-116">A <xref:System.Xml.Schema.ValidationEventHandler> is added to the <xref:System.Xml.XmlReaderSettings> object to handle any <xref:System.Xml.Schema.XmlSeverityType.Warning> or <xref:System.Xml.Schema.XmlSeverityType.Error> events raised by errors found during the validation process of both the XML document and the schema.</span></span>  
  
 [!code-cpp[XmlSchemaSetOverall Example #1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaSetOverall Example/CPP/xmlschemasetexample.cpp#1)]
 [!code-csharp[XmlSchemaSetOverall Example #1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaSetOverall Example/CS/xmlschemasetexample.cs#1)]
 [!code-vb[XmlSchemaSetOverall Example #1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaSetOverall Example/VB/xmlschemasetexample.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="3d107-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3d107-117">See also</span></span>

- [<span data-ttu-id="3d107-118">Şema Derleme için XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="3d107-118">XmlSchemaSet for Schema Compilation</span></span>](xmlschemaset-for-schema-compilation.md)
- [<span data-ttu-id="3d107-119">XML Şemalarıyla Çalışma</span><span class="sxs-lookup"><span data-stu-id="3d107-119">Working with XML Schemas</span></span>](working-with-xml-schemas.md)
