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
ms.openlocfilehash: d1c15c1e63573d6ebdf25f802a380defbe4c97e2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54535430"
---
# <a name="xml-schema-xsd-validation-with-xmlschemaset"></a>XmlSchemaSet ile XML Şeması (XSD) doğrulaması
XML belgeleri doğrulanmış bir XML Şeması Tanım Dili (XSD) şemaya karşı bir <xref:System.Xml.Schema.XmlSchemaSet>.  
  
## <a name="validating-xml-documents"></a>XML belgeleri doğrulanıyor  
 XML belgeleri tarafından doğrulanır <xref:System.Xml.XmlReader.Create%2A> yöntemi <xref:System.Xml.XmlReader> sınıfı. Bir XML belgesi doğrulamak için oluşturmak bir <xref:System.Xml.XmlReaderSettings> içeren bir XML Şeması Tanım Dili (XSD) şemaya XML belgeyi doğrulamak kullanılacak nesne.  
  
> [!NOTE]
>  <xref:System.Xml.Schema> Ad alanı, kolayca kullanırken bir XML ağacı XSD dosyası karşı doğrulamak genişletme yöntemleri içerir [LINQ to XML](https://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13). XML belgelerini LINQ to XML ile doğrulama ile ilgili daha fazla bilgi için bkz: [nasıl yapılır: XSD kullanarak doğrulama](https://msdn.microsoft.com/library/481a97fa-6e96-46f2-8c9a-415555fac33b).  
  
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
