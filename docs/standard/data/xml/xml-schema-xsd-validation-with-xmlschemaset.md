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
ms.openlocfilehash: 9bdcfe785d6f5f81d721acd45eebb580b08b2d14
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916068"
---
# <a name="xml-schema-xsd-validation-with-xmlschemaset"></a>XmlSchemaSet ile XML Şeması (XSD) Doğrulaması
XML belgeleri, bir <xref:System.Xml.Schema.XmlSchemaSet>XML şeması tanım dili (xsd) şemasına göre doğrulanabilir.  
  
## <a name="validating-xml-documents"></a>XML belgelerini doğrulama  
 XML belgeleri, <xref:System.Xml.XmlReader.Create%2A> <xref:System.Xml.XmlReader> sınıfının yöntemi tarafından onaylanır. XML belgesini doğrulamak için, XML belgesi doğrulanacak <xref:System.Xml.XmlReaderSettings> bir XML şeması tanım dili (xsd) şeması içeren bir nesne oluşturun.  
  
> [!NOTE]
> Ad <xref:System.Xml.Schema> alanı, [LINQ to XMLC#()](../../../csharp/programming-guide/concepts/linq/linq-to-xml.md) ve [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md)kullanırken bir xml ağacının xsd dosyasına karşı doğrulanmasını kolaylaştıran uzantı yöntemleri içerir. LINQ to XML ile XML belgelerinin doğrulanması hakkında daha fazla bilgi için bkz [. nasıl yapılır: XSD (LINQ to XML) (C#)](../../../csharp/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md) kullanarak doğrulayın ve [şunları yapın: XSD kullanarak doğrulayın (LINQ to XML) (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md).  
  
 Tek bir şema veya bir şema kümesi ( <xref:System.Xml.Schema.XmlSchemaSet>olarak) <xref:System.Xml.Schema.XmlSchemaSet> öğesine bir <xref:System.Xml.Schema.XmlSchemaSet>parametre <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> olarak bir parametresi geçirerek öğesine eklenebilir. Bir belge doğrulanırken belgenin hedef ad alanının şema kümesindeki şemanın hedef ad alanıyla eşleşmesi gerektiğini unutmayın.  
  
 Aşağıda örnek bir XML belgesi verilmiştir.  
  
 [!code-xml[XSDInference Examples#5](../../../../samples/snippets/xml/VS_Snippets_Data/XSDInference Examples/XML/contosoBooks.xml#5)]  
  
 Örnek XML belgesini doğrulayan şema aşağıda verilmiştir.  
  
 [!code-xml[XSDInference Examples#6](../../../../samples/snippets/xml/VS_Snippets_Data/XSDInference Examples/XML/contosoBooks.xsd#6)]  
  
 Aşağıdaki kod örneğinde, yukarıdaki şema <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.XmlReaderSettings> nesnenin <xref:System.Xml.XmlReaderSettings.Schemas%2A> özelliğine eklenir. Nesnesi, yukarıdaki XML belgesini doğrulayan <xref:System.Xml.XmlReader> nesnesinin <xref:System.Xml.XmlReader.Create%2A> yöntemine bir parametre olarak geçirilir. <xref:System.Xml.XmlReaderSettings>  
  
 <xref:System.Xml.XmlReaderSettings.ValidationType%2A> <xref:System.Xml.XmlReader.Create%2A> Nesnesinin özelliği ,nesne<xref:System.Xml.XmlReader> yöntemi tarafından XML belgesinin `Schema` doğrulanmasını zorlamak için olarak ayarlanır. <xref:System.Xml.XmlReaderSettings> , <xref:System.Xml.Schema.ValidationEventHandler> Hem XML belgesi hem <xref:System.Xml.XmlReaderSettings> de şemanın doğrulama işlemi sırasında <xref:System.Xml.Schema.XmlSeverityType.Error> bulunan hatalara göre oluşan herhangi <xref:System.Xml.Schema.XmlSeverityType.Warning> bir veya olayı işlemek için nesnesine eklenir.  
  
 [!code-cpp[XmlSchemaSetOverall Example#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaSetOverall Example/CPP/xmlschemasetexample.cpp#1)]
 [!code-csharp[XmlSchemaSetOverall Example#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaSetOverall Example/CS/xmlschemasetexample.cs#1)]
 [!code-vb[XmlSchemaSetOverall Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaSetOverall Example/VB/xmlschemasetexample.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Şema Derleme için XmlSchemaSet](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
- [XML Şemalarıyla Çalışma](../../../../docs/standard/data/xml/working-with-xml-schemas.md)
