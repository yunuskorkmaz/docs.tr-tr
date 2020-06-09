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
ms.openlocfilehash: 995323d1882da13d45cdac516518d5b67845715a
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594510"
---
# <a name="xml-schema-xsd-validation-with-xmlschemaset"></a>XmlSchemaSet ile XML şeması (XSD) doğrulaması

XML belgeleri, bir XML şeması tanım dili (XSD) şemasına göre doğrulanabilir <xref:System.Xml.Schema.XmlSchemaSet> .  
  
## <a name="validate-xml-documents"></a>XML belgelerini doğrula  
 XML belgeleri, <xref:System.Xml.XmlReader.Create%2A> sınıfının yöntemi tarafından onaylanır <xref:System.Xml.XmlReader> . XML belgesini doğrulamak için, XML <xref:System.Xml.XmlReaderSettings> belgesi doğrulanacak BIR XML şeması tanım dili (xsd) şeması içeren bir nesne oluşturun.  
  
> [!NOTE]
> <xref:System.Xml.Schema>Ad alanı, [LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) ve [LINQ to XML (VISUAL BASIC)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md)kullanırken bir xml ağacının xsd dosyasına karşı doğrulanmasını kolaylaştıran uzantı yöntemleri içerir. LINQ to XML ile XML belgelerinin doğrulanması hakkında daha fazla bilgi için bkz. [xsd (LINQ to XML) (C#)](../../../csharp/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md) ve [nasıl yapılır: XSD kullanarak doğrulama (LINQ to XML) (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md).
  
 Tek bir şema veya bir şema kümesi (olarak <xref:System.Xml.Schema.XmlSchemaSet> ) öğesine bir <xref:System.Xml.Schema.XmlSchemaSet> parametre olarak bir parametresi geçirerek öğesine eklenebilir <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> <xref:System.Xml.Schema.XmlSchemaSet> . Bir belge doğrulanırken, belgenin hedef ad alanı, şema kümesindeki şemanın hedef ad alanıyla aynı olmalıdır.  
  
 Aşağıda örnek bir XML belgesi verilmiştir.  
  
 [!code-xml[XSDInference Examples #5](../../../../samples/snippets/xml/VS_Snippets_Data/XSDInference Examples/XML/contosoBooks.xml#5)]  
  
 Örnek XML belgesini doğrulayan şema aşağıda verilmiştir.  
  
 [!code-xml[XSDInference Examples #6](../../../../samples/snippets/xml/VS_Snippets_Data/XSDInference Examples/XML/contosoBooks.xsd#6)]  
  
 Aşağıdaki kod örneğinde, yukarıdaki şema <xref:System.Xml.XmlReaderSettings.Schemas%2A> nesnenin özelliğine eklenir <xref:System.Xml.XmlReaderSettings> . <xref:System.Xml.XmlReaderSettings>Nesnesi, <xref:System.Xml.XmlReader.Create%2A> <xref:System.Xml.XmlReader> Yukarıdaki XML belgesini doğrulayan nesnesinin yöntemine bir parametre olarak geçirilir.  
  
 <xref:System.Xml.XmlReaderSettings.ValidationType%2A>Nesnesinin özelliği, <xref:System.Xml.XmlReaderSettings> `Schema` nesne yöntemi tarafından XML belgesinin doğrulanmasını zorlamak için olarak ayarlanır <xref:System.Xml.XmlReader.Create%2A> <xref:System.Xml.XmlReader> . <xref:System.Xml.Schema.ValidationEventHandler> <xref:System.Xml.XmlReaderSettings> <xref:System.Xml.Schema.XmlSeverityType.Warning> <xref:System.Xml.Schema.XmlSeverityType.Error> , Hem XML belgesi hem de şemanın doğrulama işlemi sırasında bulunan hatalara göre oluşan herhangi bir veya olayı işlemek için nesnesine eklenir.  
  
 [!code-cpp[XmlSchemaSetOverall Example #1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaSetOverall Example/CPP/xmlschemasetexample.cpp#1)]
 [!code-csharp[XmlSchemaSetOverall Example #1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaSetOverall Example/CS/xmlschemasetexample.cs#1)]
 [!code-vb[XmlSchemaSetOverall Example #1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaSetOverall Example/VB/xmlschemasetexample.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Şema Derleme için XmlSchemaSet](xmlschemaset-for-schema-compilation.md)
- [XML Şemalarıyla Çalışma](working-with-xml-schemas.md)
