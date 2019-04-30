---
title: XML Şemaları Okuma ve Yazma
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: b5757c4a-ea59-467e-ac62-be2bfe24eb77
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f80157ddf394fdd058793830bfe3052b41ad1e40
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698765"
---
# <a name="reading-and-writing-xml-schemas"></a>XML Şemaları Okuma ve Yazma
Şema nesne modeli (SOM) API okuyup dosyaları veya diğer kaynakları XML Şeması Tanım Dili (XSD) şemaları yazma ve XML şemaları sınıfları kullanarak bellek içi derleme için kullanılabilir <xref:System.Xml.Schema?displayProperty=nameWithType> dünyada tanımlanan yapıları eşleyen ad alanı Wide Web Consortium (W3C) XML Şeması öneri.  
  
## <a name="reading-and-writing-xml-schemas"></a>XML Şemaları Okuma ve Yazma  
 <xref:System.Xml.Schema.XmlSchema> Sağlar sınıfını <xref:System.Xml.Schema.XmlSchema.Read%2A> ve <xref:System.Xml.Schema.XmlSchema.Write%2A> okuma ve yazma XML şemaları için yöntemleri. <xref:System.Xml.Schema.XmlSchema.Read%2A> Yöntemi döndürür bir <xref:System.Xml.Schema.XmlSchema> XML şemasını temsil eden nesne ve isteğe bağlı alan <xref:System.Xml.Schema.ValidationEventHandler> şema doğrulama uyarıları ve bir XML Şeması okurken hatayla karşılaştı hataları işlemek için bir parametre olarak.  
  
 <xref:System.Xml.Schema.XmlSchema.Write%2A> Yöntemi yazar için XML şemaları <xref:System.IO.Stream>, <xref:System.IO.TextWriter> ve <xref:System.Xml.XmlWriter> nesneleri ve isteğe bağlı olarak alabilir <xref:System.Xml.XmlNamespaceManager> bir parametre olarak nesne. Bir <xref:System.Xml.XmlNamespaceManager> ad alanları XML şemasından karşılaştı işlemek için kullanılır. Hakkında daha fazla bilgi için <xref:System.Xml.XmlNamespaceManager> sınıfı [yönetme ad alanları XML belgesinde](../../../../docs/standard/data/xml/managing-namespaces-in-an-xml-document.md).  
  
 Aşağıdaki kod örneği, gelen ve bir dosyaya XML şemaları yazma ve okuma gösterir. Kod örneği alır `example.xsd` dosyası içine okur bir <xref:System.Xml.Schema.XmlSchema> kullanarak nesne `static` <xref:System.Xml.Schema.XmlSchema.Read%2A> yöntemi ve ardından konsolu ve yeni bir dosya Yazar `new.xsd` dosya. Kod örneği de sağlar bir <xref:System.Xml.Schema.ValidationEventHandler> bir parametre olarak `static` <xref:System.Xml.Schema.XmlSchema.Read%2A> şema doğrulama uyarıları veya hataları XML Şeması okurken hatayla karşılaştı işlemek için yöntemi. Varsa <xref:System.Xml.Schema.ValidationEventHandler> belirtilmemiş (`null`), uyarı veya hata bildirdi.  
  
 [!code-cpp[XmlSchemaReadWriteExample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaReadWriteExample/CPP/XmlSchemaReadWriteExample.cpp#1)]
 [!code-csharp[XmlSchemaReadWriteExample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaReadWriteExample/CS/XmlSchemaReadWriteExample.cs#1)]
 [!code-vb[XmlSchemaReadWriteExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaReadWriteExample/VB/XmlSchemaReadWriteExample.vb#1)]  
  
 Örnek alan `example.xsd` giriş olarak.  
  
```xml  
<?xml version="1.0"?>  
<xs:schema id="play" targetNamespace="http://tempuri.org/play.xsd" elementFormDefault="qualified" xmlns="http://tempuri.org/play.xsd" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:element name='myShoeSize'>  
        <xs:complexType>  
            <xs:simpleContent>  
                <xs:extension base='xs:decimal'>  
                    <xs:attribute name='sizing' type='xs:string' />  
                </xs:extension>  
            </xs:simpleContent>  
        </xs:complexType>  
    </xs:element>  
</xs:schema>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Şema Nesne Modeline (SOM) Genel Bakış](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)
- [XML Şemaları Derleme](../../../../docs/standard/data/xml/building-xml-schemas.md)
- [XML Şemalarını Çapraz Geçirme](../../../../docs/standard/data/xml/traversing-xml-schemas.md)
- [XML Şemalarını Düzenleme](../../../../docs/standard/data/xml/editing-xml-schemas.md)
- [XML Şemalarını Dahil Etme veya İçeri Aktarma](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)
- [Şema Derleme için XmlSchemaSet](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
- [Şema Derleme Sonrası Bilgi Kümesi](../../../../docs/standard/data/xml/post-schema-compilation-infoset.md)
- [XML Belgesinde Ad Alanlarını Yönetme](../../../../docs/standard/data/xml/managing-namespaces-in-an-xml-document.md)
