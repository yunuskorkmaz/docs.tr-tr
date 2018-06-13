---
title: Okuma ve yazma XML şemaları
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: b5757c4a-ea59-467e-ac62-be2bfe24eb77
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b652adb27c3bb075fe86c09d7c9ab33511371279
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33570459"
---
# <a name="reading-and-writing-xml-schemas"></a>Okuma ve yazma XML şemaları
Şema nesne modeli (SOM) API okumak ve XML Şeması Tanım Dili (XSD) şemaları dosyaları veya diğer kaynakları yazma ve XML şemaları sınıflarda kullanarak bellek içi oluşturmak için kullanılan <xref:System.Xml.Schema?displayProperty=nameWithType> dünyada tanımlanan yapıları Eşle ad alanı Wide Web Konsorsiyumu (W3C) XML Şeması öneri.  
  
## <a name="reading-and-writing-xml-schemas"></a>Okuma ve yazma XML şemaları  
 <xref:System.Xml.Schema.XmlSchema> SAX <xref:System.Xml.Schema.XmlSchema.Read%2A> ve <xref:System.Xml.Schema.XmlSchema.Write%2A> XML şemaları okumasına ve yazmasına yöntemleri. <xref:System.Xml.Schema.XmlSchema.Read%2A> Yöntemi döndürür bir <xref:System.Xml.Schema.XmlSchema> XML Şeması temsil eden nesne ve isteğe bağlı bir alan <xref:System.Xml.Schema.ValidationEventHandler> şema doğrulama uyarıları ve XML Şeması okunurken karşılaşılan hataları işlemek için bir parametre olarak.  
  
 <xref:System.Xml.Schema.XmlSchema.Write%2A> Yöntemi için XML şemaları Yazar <xref:System.IO.Stream>, <xref:System.IO.TextWriter> ve <xref:System.Xml.XmlWriter> nesneleri ve isteğe bağlı bir alabilir <xref:System.Xml.XmlNamespaceManager> nesnesini parametre olarak. Bir <xref:System.Xml.XmlNamespaceManager> ad alanları bir XML Şeması karşılaştı işlemek için kullanılır. Hakkında daha fazla bilgi için <xref:System.Xml.XmlNamespaceManager> sınıfı için bkz: [ad alanları bir XML belgesi yönetme](../../../../docs/standard/data/xml/managing-namespaces-in-an-xml-document.md).  
  
 Aşağıdaki kod örneğinde, okuma ve XML şemaları gelen ve bir dosyaya yazma gösterilmektedir. Kod örneği alır `example.xsd` dosyası içine okur bir <xref:System.Xml.Schema.XmlSchema> kullanarak nesne `static` <xref:System.Xml.Schema.XmlSchema.Read%2A> yöntemi ve ardından konsolu ve yeni bir dosya Yazar `new.xsd` dosya. Kod örneği de sağlar bir <xref:System.Xml.Schema.ValidationEventHandler> bir parametre olarak `static` <xref:System.Xml.Schema.XmlSchema.Read%2A> herhangi bir şema doğrulama uyarıları veya XML Şeması okunurken karşılaşılan hataları işlemek için yöntem. Varsa <xref:System.Xml.Schema.ValidationEventHandler> belirtilmemiş (`null`), hiçbir uyarı veya hata bildirdi.  
  
 [!code-cpp[XmlSchemaReadWriteExample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaReadWriteExample/CPP/XmlSchemaReadWriteExample.cpp#1)]
 [!code-csharp[XmlSchemaReadWriteExample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaReadWriteExample/CS/XmlSchemaReadWriteExample.cs#1)]
 [!code-vb[XmlSchemaReadWriteExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaReadWriteExample/VB/XmlSchemaReadWriteExample.vb#1)]  
  
 Örnek alır `example.xsd` giriş olarak.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML Şema Nesne Modeline (SOM) Genel Bakış](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)  
 [XML Şemaları Derleme](../../../../docs/standard/data/xml/building-xml-schemas.md)  
 [XML Şemalarını Çapraz Geçirme](../../../../docs/standard/data/xml/traversing-xml-schemas.md)  
 [XML Şemalarını Düzenleme](../../../../docs/standard/data/xml/editing-xml-schemas.md)  
 [XML Şemalarını Dahil Etme veya İçeri Aktarma](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)  
 [Şema Derleme için XmlSchemaSet](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
 [Şema Derleme Sonrası Bilgi Kümesi](../../../../docs/standard/data/xml/post-schema-compilation-infoset.md)  
 [XML Belgesinde Ad Alanlarını Yönetme](../../../../docs/standard/data/xml/managing-namespaces-in-an-xml-document.md)
