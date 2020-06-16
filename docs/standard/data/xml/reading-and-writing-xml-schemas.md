---
title: XML Şemaları Okuma ve Yazma
description: Şema nesne modeli (SOM) API 'sini kullanarak, .NET 'teki dosyalardan veya diğer kaynaklardan XML şeması tanım dili (XSD) şemalarını okuyun ve yazın.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: b5757c4a-ea59-467e-ac62-be2bfe24eb77
ms.openlocfilehash: 874b0bdb0e13d545cfff4c813881f1398a8f9487
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/15/2020
ms.locfileid: "84767669"
---
# <a name="reading-and-writing-xml-schemas"></a>XML Şemaları Okuma ve Yazma
Şema nesne modeli (SOM) API 'SI, dosyalardan veya diğer kaynaklardan XML şeması tanım dili (XSD) şemalarını okumak ve yazmak ve <xref:System.Xml.Schema?displayProperty=nameWithType> World Wide Web Konsorsiyumu (W3C) XML şeması önerisi içinde tanımlanan yapılara eşlenen ad alanındaki sınıfları kullanarak XML şemaları oluşturmak için kullanılabilir.  
  
## <a name="reading-and-writing-xml-schemas"></a>XML Şemaları Okuma ve Yazma  
 <xref:System.Xml.Schema.XmlSchema>Sınıfı, <xref:System.Xml.Schema.XmlSchema.Read%2A> ve <xref:System.Xml.Schema.XmlSchema.Write%2A> XML şemaları okumak ve yazmak için yöntemler sağlar. <xref:System.Xml.Schema.XmlSchema.Read%2A>Yöntemi, <xref:System.Xml.Schema.XmlSchema> XML şemasını temsil eden bir nesne döndürür ve <xref:System.Xml.Schema.ValidationEventHandler> şema doğrulama UYARıLARıNı ve bir XML Şeması okunurken karşılaşılan hataları işlemek için isteğe bağlı olarak bir parametre olarak alır.  
  
 <xref:System.Xml.Schema.XmlSchema.Write%2A>Yöntemi <xref:System.IO.Stream> , ve nesnelerine XML şemaları Yazar <xref:System.IO.TextWriter> <xref:System.Xml.XmlWriter> ve isteğe bağlı bir <xref:System.Xml.XmlNamespaceManager> nesneyi parametre olarak alabilir. Bir <xref:System.Xml.XmlNamespaceManager> XML şemasında karşılaşılan ad alanlarını işlemek için kullanılır. Sınıfı hakkında daha fazla bilgi için <xref:System.Xml.XmlNamespaceManager> bkz. [XML belgesinde ad alanlarını yönetme](managing-namespaces-in-an-xml-document.md).  
  
 Aşağıdaki kod örneği, ve bir dosyasına XML şemaları okuma ve yazma hakkında bilgi gösterir. Kod örneği `example.xsd` dosyayı alır, <xref:System.Xml.Schema.XmlSchema> yöntemini kullanarak bir nesnesine okur `static` <xref:System.Xml.Schema.XmlSchema.Read%2A> ve sonra dosyayı konsola ve yeni bir `new.xsd` dosyaya yazar. Kod örneği Ayrıca, <xref:System.Xml.Schema.ValidationEventHandler> `static` <xref:System.Xml.Schema.XmlSchema.Read%2A> XML şemasını okurken herhangi bir şema doğrulama uyarısı veya hata ile karşılaşılan hataları işlemek için yöntemine bir parametre olarak da sağlar. Belirtilmemişse, <xref:System.Xml.Schema.ValidationEventHandler> `null` hiçbir uyarı veya hata bildirilmemiştir.  
  
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

- [XML Şema Nesne Modeline (SOM) Genel Bakış](xml-schema-object-model-overview.md)
- [XML Şemaları Derleme](building-xml-schemas.md)
- [XML Şemalarını Çapraz Geçirme](traversing-xml-schemas.md)
- [XML Şemalarını Düzenleme](editing-xml-schemas.md)
- [XML Şemalarını Dahil Etme veya İçeri Aktarma](including-or-importing-xml-schemas.md)
- [Şema Derleme için XmlSchemaSet](xmlschemaset-for-schema-compilation.md)
- [Şema Derleme Sonrası Bilgi Kümesi](post-schema-compilation-infoset.md)
- [XML Belgesinde Ad Alanlarını Yönetme](managing-namespaces-in-an-xml-document.md)
