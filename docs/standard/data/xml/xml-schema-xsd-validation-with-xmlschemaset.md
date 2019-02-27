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
# <a name="xml-schema-xsd-validation-with-xmlschemaset"></a>XmlSchemaSet ile XML Şeması (XSD) doğrulaması
XML belgeleri doğrulanmış bir XML Şeması Tanım Dili (XSD) şemaya karşı bir <xref:System.Xml.Schema.XmlSchemaSet>.  
  
## <a name="validating-xml-documents"></a>XML belgeleri doğrulanıyor  
 XML belgeleri tarafından doğrulanır <xref:System.Xml.XmlReader.Create%2A> yöntemi <xref:System.Xml.XmlReader> sınıfı. Bir XML belgesi doğrulamak için oluşturmak bir <xref:System.Xml.XmlReaderSettings> içeren bir XML Şeması Tanım Dili (XSD) şemaya XML belgeyi doğrulamak kullanılacak nesne.  
  
> [!NOTE]
>  <xref:System.Xml.Schema> Ad alanı, kolayca kullanırken bir XML ağacı XSD dosyası karşı doğrulamak genişletme yöntemleri içerir [LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml.md) ve [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md). XML belgelerini LINQ to XML ile doğrulama ile ilgili daha fazla bilgi için bkz: [nasıl yapılır: XSD (LINQ to XML) kullanarak doğrulama (C#)](../../../csharp/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md) ve [nasıl yapılır: XSD (LINQ to XML) kullanarak doğrulama (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md).  
  
 Tek bir şema veya şema kümesine (olarak bir <xref:System.Xml.Schema.XmlSchemaSet>) eklenebilen bir <xref:System.Xml.Schema.XmlSchemaSet> ya da tek bir parametre olarak geçirerek <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> yöntemi <xref:System.Xml.Schema.XmlSchemaSet>. Bir belge doğrularken belgesinin hedef ad alanı için şema kümesindeki şema hedef ad alanı eşleşmesi gerektiğini unutmayın.  
  
 Bir örneği XML belgesi verilmiştir.  
  
 [!code-xml[XSDInference Examples#5](../../../../samples/snippets/xml/VS_Snippets_Data/XSDInference Examples/XML/contosoBooks.xml#5)]  
  
 Örnek XML belgesi doğrulama şeması verilmiştir.  
  
 [!code-xml[XSDInference Examples#6](../../../../samples/snippets/xml/VS_Snippets_Data/XSDInference Examples/XML/contosoBooks.xsd#6)]  
  
 Yukarıdaki şemayı eklenir aşağıdaki kod örneğinde <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.XmlReaderSettings.Schemas%2A> özelliği <xref:System.Xml.XmlReaderSettings> nesne. <xref:System.Xml.XmlReaderSettings> Nesnesi bir parametre olarak geçirilir <xref:System.Xml.XmlReader.Create%2A> yöntemi <xref:System.Xml.XmlReader> yukarıdaki XML belgesi doğrulama nesnesi.  
  
 <xref:System.Xml.XmlReaderSettings.ValidationType%2A> Özelliği <xref:System.Xml.XmlReaderSettings> nesne ayarlandığında `Schema` tarafından XML belgesi doğrulama zorlamak için <xref:System.Xml.XmlReader.Create%2A> yöntemi <xref:System.Xml.XmlReader> nesne. A <xref:System.Xml.Schema.ValidationEventHandler> eklenir <xref:System.Xml.XmlReaderSettings> herhangi işlemek için nesne <xref:System.Xml.Schema.XmlSeverityType.Warning> veya <xref:System.Xml.Schema.XmlSeverityType.Error> hem XML belgesi ve şema doğrulama işlemi sırasında bulunan hataları tarafından oluşturulan olayları.  
  
 [!code-cpp[XmlSchemaSetOverall Example#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaSetOverall Example/CPP/xmlschemasetexample.cpp#1)]
 [!code-csharp[XmlSchemaSetOverall Example#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaSetOverall Example/CS/xmlschemasetexample.cs#1)]
 [!code-vb[XmlSchemaSetOverall Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaSetOverall Example/VB/xmlschemasetexample.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Şema Derleme için XmlSchemaSet](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
- [XML Şemalarıyla Çalışma](../../../../docs/standard/data/xml/working-with-xml-schemas.md)
