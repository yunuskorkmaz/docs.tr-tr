---
title: XmlSchemaSet ile XML Şeması (XSD) Doğrulaması
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 359b10eb-ec05-4cc6-ac96-c2b060afc4de
ms.openlocfilehash: 34215c2b06db08a74b5b9c13589ac84f26a2ef8f
ms.sourcegitcommit: c2c1269a81ffdcfc8675bcd9a8505b1a11ffb271
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/25/2020
ms.locfileid: "82158586"
---
# <a name="xml-schema-xsd-validation-with-xmlschemaset"></a>XmlSchemaSet ile XML şeması (XSD) doğrulaması

XML belgeleri, bir <xref:System.Xml.Schema.XmlSchemaSet>XML şeması tanım DILI (xsd) şemasına göre doğrulanabilir.  
  
## <a name="validate-xml-documents"></a>XML belgelerini doğrula  
 XML belgeleri, <xref:System.Xml.XmlReader.Create%2A> <xref:System.Xml.XmlReader> sınıfının yöntemi tarafından onaylanır. XML belgesini doğrulamak için, XML belgesi doğrulanacak <xref:System.Xml.XmlReaderSettings> bir XML şeması tanım DILI (xsd) şeması içeren bir nesne oluşturun.  
  
> [!NOTE]
> Ad <xref:System.Xml.Schema> alanı, [LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) ve [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md)kullanırken bir xml ağacının xsd dosyasına karşı doğrulanmasını kolaylaştıran uzantı yöntemleri içerir. LINQ to XML ile XML belgelerinin doğrulanması hakkında daha fazla bilgi için bkz. [xsd (LINQ to XML) (C#)](../../../csharp/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md) ve [nasıl yapılır: XSD kullanarak doğrulama (LINQ to XML) (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md).
  
 Tek bir şema veya bir şema kümesi ( <xref:System.Xml.Schema.XmlSchemaSet>olarak) öğesine bir parametre olarak bir parametresi <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> geçirerek öğesine eklenebilir. <xref:System.Xml.Schema.XmlSchemaSet> Bir belge doğrulanırken, belgenin hedef ad alanı, şema kümesindeki şemanın hedef ad alanıyla aynı olmalıdır.  
  
 Aşağıda örnek bir XML belgesi verilmiştir.  
  
 [!code-xml[XSDInference Examples #5](../../../../samples/snippets/xml/VS_Snippets_Data/XSDInference Examples/XML/contosoBooks.xml#5)]  
  
 Örnek XML belgesini doğrulayan şema aşağıda verilmiştir.  
  
 [!code-xml[XSDInference Examples #6](../../../../samples/snippets/xml/VS_Snippets_Data/XSDInference Examples/XML/contosoBooks.xsd#6)]  
  
 Aşağıdaki kod örneğinde, yukarıdaki şema <xref:System.Xml.XmlReaderSettings.Schemas%2A> <xref:System.Xml.XmlReaderSettings> nesnenin özelliğine eklenir. <xref:System.Xml.XmlReaderSettings> Nesnesi, yukarıdaki XML belgesini doğrulayan <xref:System.Xml.XmlReader.Create%2A> <xref:System.Xml.XmlReader> nesnesinin yöntemine bir parametre olarak geçirilir.  
  
 <xref:System.Xml.XmlReaderSettings> Nesnesinin <xref:System.Xml.XmlReaderSettings.ValidationType%2A> özelliği <xref:System.Xml.XmlReader.Create%2A> , <xref:System.Xml.XmlReader> nesne yöntemi tarafından XML belgesinin `Schema` doğrulanmasını zorlamak için olarak ayarlanır. , <xref:System.Xml.Schema.ValidationEventHandler> Hem XML belgesi hem <xref:System.Xml.XmlReaderSettings> de şemanın doğrulama işlemi <xref:System.Xml.Schema.XmlSeverityType.Warning> sırasında <xref:System.Xml.Schema.XmlSeverityType.Error> bulunan hatalara göre oluşan herhangi bir veya olayı işlemek için nesnesine eklenir.  
  
 [!code-cpp[XmlSchemaSetOverall Example #1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaSetOverall Example/CPP/xmlschemasetexample.cpp#1)]
 [!code-csharp[XmlSchemaSetOverall Example #1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaSetOverall Example/CS/xmlschemasetexample.cs#1)]
 [!code-vb[XmlSchemaSetOverall Example #1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaSetOverall Example/VB/xmlschemasetexample.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Şema Derleme için XmlSchemaSet](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
- [XML Şemalarıyla Çalışma](../../../../docs/standard/data/xml/working-with-xml-schemas.md)
