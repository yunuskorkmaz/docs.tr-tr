---
title: XML Şeması (XSD) doğrulama XmlSchemaSet ile
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 359b10eb-ec05-4cc6-ac96-c2b060afc4de
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4036b98cc98736033a2be1682ec6d5355939d3ad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33570563"
---
# <a name="xml-schema-xsd-validation-with-xmlschemaset"></a>XML Şeması (XSD) doğrulama XmlSchemaSet ile
XML belgeleri doğrulanmış bir XML Şeması Tanım Dili (XSD) şemasında karşı bir <xref:System.Xml.Schema.XmlSchemaSet>.  
  
## <a name="validating-xml-documents"></a>XML belgeleri doğrulanıyor  
 XML belgeleri tarafından doğrulanır <xref:System.Xml.XmlReader.Create%2A> yöntemi <xref:System.Xml.XmlReader> sınıfı. Bir XML belgesi doğrulamak için oluşturmak bir <xref:System.Xml.XmlReaderSettings> bir XML Şeması Tanım Dili (XSD) şemasıyla XML belgesi doğrulamak içeren nesne.  
  
> [!NOTE]
>  <xref:System.Xml.Schema> Ad alanı, kolaylaştıran kullanırken bir XML ağacı bir XSD dosyası karşı doğrulamak genişletme yöntemleri içerir [LINQ-XML](https://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13). LINQ-XML ile XML belgelerini doğrulama ile ilgili daha fazla bilgi için bkz: [nasıl yapılır: kullanarak XSD doğrulama](https://msdn.microsoft.com/library/481a97fa-6e96-46f2-8c9a-415555fac33b).  
  
 Tek bir şema veya şema kümesine (olarak bir <xref:System.Xml.Schema.XmlSchemaSet>) eklenebilir bir <xref:System.Xml.Schema.XmlSchemaSet> ya da bir parametre olarak geçirerek <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> yöntemi <xref:System.Xml.Schema.XmlSchemaSet>. Bir belge doğrularken belgenin hedef ad alanı şema kümesini şemada hedef ad alanı eşleşmesi gerektiğini unutmayın.  
  
 Aşağıdaki örnek XML dosyasıdır.  
  
 [!code-xml[XSDInference Examples#5](../../../../samples/snippets/xml/VS_Snippets_Data/XSDInference Examples/XML/contosoBooks.xml#5)]  
  
 Bu örnek XML belge doğrular şema verilmiştir.  
  
 [!code-xml[XSDInference Examples#6](../../../../samples/snippets/xml/VS_Snippets_Data/XSDInference Examples/XML/contosoBooks.xsd#6)]  
  
 Aşağıdaki kod örneğinde, yukarıdaki şemayı eklenen <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.XmlReaderSettings.Schemas%2A> özelliği <xref:System.Xml.XmlReaderSettings> nesnesi. <xref:System.Xml.XmlReaderSettings> Nesnesini parametre olarak geçirilen <xref:System.Xml.XmlReader.Create%2A> yöntemi <xref:System.Xml.XmlReader> yukarıdaki XML belgesi doğrular nesnesi.  
  
 <xref:System.Xml.XmlReaderSettings.ValidationType%2A> Özelliği <xref:System.Xml.XmlReaderSettings> nesne ayarlanmış `Schema` XML belgesi tarafından doğrulanmasını zorlamak için <xref:System.Xml.XmlReader.Create%2A> yöntemi <xref:System.Xml.XmlReader> nesnesi. A <xref:System.Xml.Schema.ValidationEventHandler> eklenen <xref:System.Xml.XmlReaderSettings> herhangi işlenecek nesne <xref:System.Xml.Schema.XmlSeverityType.Warning> veya <xref:System.Xml.Schema.XmlSeverityType.Error> XML belgesi ve şema doğrulama işlemi sırasında bulunan hatalar tarafından başlatılan olayları.  
  
 [!code-cpp[XmlSchemaSetOverall Example#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaSetOverall Example/CPP/xmlschemasetexample.cpp#1)]
 [!code-csharp[XmlSchemaSetOverall Example#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaSetOverall Example/CS/xmlschemasetexample.cs#1)]
 [!code-vb[XmlSchemaSetOverall Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaSetOverall Example/VB/xmlschemasetexample.vb#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Şema Derleme için XmlSchemaSet](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
 [XML Şemalarıyla Çalışma](../../../../docs/standard/data/xml/working-with-xml-schemas.md)
