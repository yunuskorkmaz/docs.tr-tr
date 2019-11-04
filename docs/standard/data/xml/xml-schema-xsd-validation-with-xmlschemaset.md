---
title: XmlSchemaSet ile XML Şeması (XSD) Doğrulaması
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 359b10eb-ec05-4cc6-ac96-c2b060afc4de
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1ac2f2a33ce66813c009d475a1f7b2b27937a0c3
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73425155"
---
# <a name="xml-schema-xsd-validation-with-xmlschemaset"></a>XmlSchemaSet ile XML Şeması (XSD) Doğrulaması
XML belgeleri, bir <xref:System.Xml.Schema.XmlSchemaSet>bir XML şeması tanım dili (XSD) şemasına göre doğrulanabilir.  
  
## <a name="validating-xml-documents"></a>XML belgelerini doğrulama  
 XML belgeleri <xref:System.Xml.XmlReader> sınıfının <xref:System.Xml.XmlReader.Create%2A> yöntemi tarafından onaylanır. Bir XML belgesini doğrulamak için, XML belgesinin doğrulanması için bir XML şeması tanım dili (XSD) şeması içeren bir <xref:System.Xml.XmlReaderSettings> nesnesi oluşturun.  
  
> [!NOTE]
> <xref:System.Xml.Schema> ad alanı, [LINQ to XMLC#()](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) ve [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md)kullanılırken bir xsd dosyasına yönelik bir xml ağacının doğrulanmasını kolaylaştıran uzantı yöntemleri içerir. LINQ to XML ile XML belgelerinin doğrulanması hakkında daha fazla bilgi için bkz. [nasıl yapılır: XSD kullanarak doğrulama (LINQ to XML)C#()](../../../csharp/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md) ve [nasıl yapılır: doğrulama (LINQ to XML) (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md).  
  
 Tek bir şema veya bir şema kümesi (<xref:System.Xml.Schema.XmlSchemaSet>olarak), <xref:System.Xml.Schema.XmlSchemaSet><xref:System.Xml.Schema.XmlSchemaSet.Add%2A> yöntemine parametre olarak geçirerek bir <xref:System.Xml.Schema.XmlSchemaSet> eklenebilir. Bir belge doğrulanırken belgenin hedef ad alanının şema kümesindeki şemanın hedef ad alanıyla eşleşmesi gerektiğini unutmayın.  
  
 Aşağıda örnek bir XML belgesi verilmiştir.  
  
 [!code-xml[XSDInference Examples#5](../../../../samples/snippets/xml/VS_Snippets_Data/XSDInference Examples/XML/contosoBooks.xml#5)]  
  
 Örnek XML belgesini doğrulayan şema aşağıda verilmiştir.  
  
 [!code-xml[XSDInference Examples#6](../../../../samples/snippets/xml/VS_Snippets_Data/XSDInference Examples/XML/contosoBooks.xsd#6)]  
  
 Aşağıdaki kod örneğinde, yukarıdaki şema <xref:System.Xml.XmlReaderSettings> nesnesinin <xref:System.Xml.Schema.XmlSchemaSet><xref:System.Xml.XmlReaderSettings.Schemas%2A> özelliğine eklenir. <xref:System.Xml.XmlReaderSettings> nesnesi, yukarıdaki XML belgesini doğrulayan <xref:System.Xml.XmlReader> nesnesinin <xref:System.Xml.XmlReader.Create%2A> yöntemine bir parametre olarak geçirilir.  
  
 <xref:System.Xml.XmlReaderSettings> nesnesinin <xref:System.Xml.XmlReaderSettings.ValidationType%2A> özelliği, <xref:System.Xml.XmlReader> nesnesinin <xref:System.Xml.XmlReader.Create%2A> yöntemi tarafından XML belgesinin doğrulanmasını zorlamak için `Schema` olarak ayarlanmıştır. Hem XML belgesi hem de şemanın doğrulama işlemi sırasında bulunan hatalara göre oluşturulan <xref:System.Xml.Schema.XmlSeverityType.Warning> veya <xref:System.Xml.Schema.XmlSeverityType.Error> olayları işlemek için <xref:System.Xml.XmlReaderSettings> nesnesine bir <xref:System.Xml.Schema.ValidationEventHandler> eklenir.  
  
 [!code-cpp[XmlSchemaSetOverall Example#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaSetOverall Example/CPP/xmlschemasetexample.cpp#1)]
 [!code-csharp[XmlSchemaSetOverall Example#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaSetOverall Example/CS/xmlschemasetexample.cs#1)]
 [!code-vb[XmlSchemaSetOverall Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaSetOverall Example/VB/xmlschemasetexample.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Şema Derleme için XmlSchemaSet](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
- [XML Şemalarıyla Çalışma](../../../../docs/standard/data/xml/working-with-xml-schemas.md)
