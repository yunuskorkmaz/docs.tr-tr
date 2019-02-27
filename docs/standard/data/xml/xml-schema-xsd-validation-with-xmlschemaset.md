---
title: XmlSchemaSet ile XML Şeması (XSD) doğrulaması
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 359b10eb-ec05-4cc6-ac96-c2b060afc4de
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7db1b0fe3d4b884bca2c2b00cc95c0872bfa7e7a
ms.sourcegitcommit: bd28ff1e312eaba9718c4f7ea272c2d4781a7cac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2019
ms.locfileid: "56835583"
---
# <a name="xml-schema-xsd-validation-with-xmlschemaset"></a><span data-ttu-id="ac888-102">XmlSchemaSet ile XML Şeması (XSD) doğrulaması</span><span class="sxs-lookup"><span data-stu-id="ac888-102">XML Schema (XSD) Validation with XmlSchemaSet</span></span>
<span data-ttu-id="ac888-103">XML belgeleri doğrulanmış bir XML Şeması Tanım Dili (XSD) şemaya karşı bir <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="ac888-103">XML documents can be validated against an XML schema definition language (XSD) schema in an <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
## <a name="validating-xml-documents"></a><span data-ttu-id="ac888-104">XML belgeleri doğrulanıyor</span><span class="sxs-lookup"><span data-stu-id="ac888-104">Validating XML Documents</span></span>  
 <span data-ttu-id="ac888-105">XML belgeleri tarafından doğrulanır <xref:System.Xml.XmlReader.Create%2A> yöntemi <xref:System.Xml.XmlReader> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="ac888-105">XML documents are validated by the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> class.</span></span> <span data-ttu-id="ac888-106">Bir XML belgesi doğrulamak için oluşturmak bir <xref:System.Xml.XmlReaderSettings> içeren bir XML Şeması Tanım Dili (XSD) şemaya XML belgeyi doğrulamak kullanılacak nesne.</span><span class="sxs-lookup"><span data-stu-id="ac888-106">To validate an XML document, construct an <xref:System.Xml.XmlReaderSettings> object that contains an XML schema definition language (XSD) schema with which to validate the XML document.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ac888-107"><xref:System.Xml.Schema> Ad alanı, kolayca kullanırken bir XML ağacı XSD dosyası karşı doğrulamak genişletme yöntemleri içerir [LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml.md) ve [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="ac888-107">The <xref:System.Xml.Schema> namespace contains extension methods that make it easy to validate an XML tree against an XSD file when using [LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml.md) and [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md).</span></span> <span data-ttu-id="ac888-108">XML belgelerini LINQ to XML ile doğrulama ile ilgili daha fazla bilgi için bkz: [nasıl yapılır: XSD (LINQ to XML) kullanarak doğrulama (C#)](../../../csharp/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md) ve [nasıl yapılır: XSD (LINQ to XML) kullanarak doğrulama (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="ac888-108">For more information on validating XML documents with LINQ to XML, see [How to: Validate Using XSD (LINQ to XML) (C#)](../../../csharp/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md) and [How to: Validate Using XSD (LINQ to XML) (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="ac888-109">Tek bir şema veya şema kümesine (olarak bir <xref:System.Xml.Schema.XmlSchemaSet>) eklenebilen bir <xref:System.Xml.Schema.XmlSchemaSet> ya da tek bir parametre olarak geçirerek <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> yöntemi <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="ac888-109">An individual schema or a set of schemas (as an <xref:System.Xml.Schema.XmlSchemaSet>) can be added to an <xref:System.Xml.Schema.XmlSchemaSet> by passing either one as a parameter to the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method of <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="ac888-110">Bir belge doğrularken belgesinin hedef ad alanı için şema kümesindeki şema hedef ad alanı eşleşmesi gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="ac888-110">Note that when validating a document the target namespace of the document must match the target namespace of the schema in the schema set.</span></span>  
  
 <span data-ttu-id="ac888-111">Bir örneği XML belgesi verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ac888-111">The following is an example XML document.</span></span>  
  
 [!code-xml[XSDInference Examples#5](../../../../samples/snippets/xml/VS_Snippets_Data/XSDInference Examples/XML/contosoBooks.xml#5)]  
  
 <span data-ttu-id="ac888-112">Örnek XML belgesi doğrulama şeması verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ac888-112">The following is the schema that validates the example XML document.</span></span>  
  
 [!code-xml[XSDInference Examples#6](../../../../samples/snippets/xml/VS_Snippets_Data/XSDInference Examples/XML/contosoBooks.xsd#6)]  
  
 <span data-ttu-id="ac888-113">Yukarıdaki şemayı eklenir aşağıdaki kod örneğinde <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.XmlReaderSettings.Schemas%2A> özelliği <xref:System.Xml.XmlReaderSettings> nesne.</span><span class="sxs-lookup"><span data-stu-id="ac888-113">In the code example that follows, the schema above is added to the <xref:System.Xml.Schema.XmlSchemaSet><xref:System.Xml.XmlReaderSettings.Schemas%2A> property of the <xref:System.Xml.XmlReaderSettings> object.</span></span> <span data-ttu-id="ac888-114"><xref:System.Xml.XmlReaderSettings> Nesnesi bir parametre olarak geçirilir <xref:System.Xml.XmlReader.Create%2A> yöntemi <xref:System.Xml.XmlReader> yukarıdaki XML belgesi doğrulama nesnesi.</span><span class="sxs-lookup"><span data-stu-id="ac888-114">The <xref:System.Xml.XmlReaderSettings> object is passed as a parameter to the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> object, which validates the XML document above.</span></span>  
  
 <span data-ttu-id="ac888-115"><xref:System.Xml.XmlReaderSettings.ValidationType%2A> Özelliği <xref:System.Xml.XmlReaderSettings> nesne ayarlandığında `Schema` tarafından XML belgesi doğrulama zorlamak için <xref:System.Xml.XmlReader.Create%2A> yöntemi <xref:System.Xml.XmlReader> nesne.</span><span class="sxs-lookup"><span data-stu-id="ac888-115">The <xref:System.Xml.XmlReaderSettings.ValidationType%2A> property of the <xref:System.Xml.XmlReaderSettings> object is set to `Schema` to enforce validation of the XML document by the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="ac888-116">A <xref:System.Xml.Schema.ValidationEventHandler> eklenir <xref:System.Xml.XmlReaderSettings> herhangi işlemek için nesne <xref:System.Xml.Schema.XmlSeverityType.Warning> veya <xref:System.Xml.Schema.XmlSeverityType.Error> hem XML belgesi ve şema doğrulama işlemi sırasında bulunan hataları tarafından oluşturulan olayları.</span><span class="sxs-lookup"><span data-stu-id="ac888-116">A <xref:System.Xml.Schema.ValidationEventHandler> is added to the <xref:System.Xml.XmlReaderSettings> object to handle any <xref:System.Xml.Schema.XmlSeverityType.Warning> or <xref:System.Xml.Schema.XmlSeverityType.Error> events raised by errors found during the validation process of both the XML document and the schema.</span></span>  
  
 [!code-cpp[XmlSchemaSetOverall Example#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaSetOverall Example/CPP/xmlschemasetexample.cpp#1)]
 [!code-csharp[XmlSchemaSetOverall Example#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaSetOverall Example/CS/xmlschemasetexample.cs#1)]
 [!code-vb[XmlSchemaSetOverall Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaSetOverall Example/VB/xmlschemasetexample.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="ac888-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ac888-117">See also</span></span>

- [<span data-ttu-id="ac888-118">Şema Derleme için XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="ac888-118">XmlSchemaSet for Schema Compilation</span></span>](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
- [<span data-ttu-id="ac888-119">XML Şemalarıyla Çalışma</span><span class="sxs-lookup"><span data-stu-id="ac888-119">Working with XML Schemas</span></span>](../../../../docs/standard/data/xml/working-with-xml-schemas.md)
