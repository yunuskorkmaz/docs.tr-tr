---
title: XML Şemaları Okuma ve Yazma
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: b5757c4a-ea59-467e-ac62-be2bfe24eb77
ms.openlocfilehash: 889c5f85a2ea3fc08dadefda5509de0fcfab76ec
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710420"
---
# <a name="reading-and-writing-xml-schemas"></a>XML Şemaları Okuma ve Yazma
Şema nesne modeli (SOM) API 'SI, dosyalardan veya diğer kaynaklardan XML şeması tanım dili (XSD) şemaları okumak ve yazmak ve World Wide Web Konsorsiyumu (W3C) XML şeması önerisi içinde tanımlanan yapılara eşlenen <xref:System.Xml.Schema?displayProperty=nameWithType> ad alanındaki sınıfları kullanarak XML şemaları oluşturmak için kullanılabilir.  
  
## <a name="reading-and-writing-xml-schemas"></a>XML Şemaları Okuma ve Yazma  
 <xref:System.Xml.Schema.XmlSchema> sınıfı, XML şemaları okumak ve yazmak için <xref:System.Xml.Schema.XmlSchema.Read%2A> ve <xref:System.Xml.Schema.XmlSchema.Write%2A> yöntemleri sağlar. <xref:System.Xml.Schema.XmlSchema.Read%2A> yöntemi, XML şemasını temsil eden bir <xref:System.Xml.Schema.XmlSchema> nesnesi döndürür ve şema doğrulama uyarılarını işlemek için bir parametre olarak isteğe bağlı bir <xref:System.Xml.Schema.ValidationEventHandler> ve bir XML Şeması okunurken karşılaşılan hataları alır.  
  
 <xref:System.Xml.Schema.XmlSchema.Write%2A> yöntemi, <xref:System.IO.Stream>, <xref:System.IO.TextWriter> ve <xref:System.Xml.XmlWriter> nesnelerine XML şemaları Yazar ve isteğe bağlı bir <xref:System.Xml.XmlNamespaceManager> nesnesini parametre olarak alabilir. Bir <xref:System.Xml.XmlNamespaceManager> bir XML şemasında karşılaşılan ad alanlarını işlemek için kullanılır. <xref:System.Xml.XmlNamespaceManager> sınıfı hakkında daha fazla bilgi için bkz. [XML belgesinde ad alanlarını yönetme](../../../../docs/standard/data/xml/managing-namespaces-in-an-xml-document.md).  
  
 Aşağıdaki kod örneği, ve bir dosyasına XML şemaları okuma ve yazma hakkında bilgi gösterir. Kod örneği `example.xsd` dosyayı alır, `static`<xref:System.Xml.Schema.XmlSchema.Read%2A> yöntemini kullanarak dosyayı bir <xref:System.Xml.Schema.XmlSchema> nesnesine okur ve sonra dosyayı konsola ve yeni bir `new.xsd` dosyasına yazar. Kod örneği Ayrıca, XML Şeması okunurken herhangi bir şema doğrulama uyarısı veya hata ile karşılaşılan hataları işlemek için `static`<xref:System.Xml.Schema.XmlSchema.Read%2A> metoduna parametre olarak bir <xref:System.Xml.Schema.ValidationEventHandler> sağlar. <xref:System.Xml.Schema.ValidationEventHandler> belirtilmemişse (`null`), hiçbir uyarı veya hata bildirilmemiştir.  
  
 [!code-cpp[XmlSchemaReadWriteExample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaReadWriteExample/CPP/XmlSchemaReadWriteExample.cpp#1)]
 [!code-csharp[XmlSchemaReadWriteExample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaReadWriteExample/CS/XmlSchemaReadWriteExample.cs#1)]
 [!code-vb[XmlSchemaReadWriteExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaReadWriteExample/VB/XmlSchemaReadWriteExample.vb#1)]  
  
 Örnek, `example.xsd` giriş olarak alır.  
  
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
