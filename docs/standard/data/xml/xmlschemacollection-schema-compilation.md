---
title: XmlSchemaCollection Şema Derlemesi
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 76f28770-7126-428f-9ed5-7b5ae8bad5ee
ms.openlocfilehash: 1f300bab01f94af8c70c8b67a69a73fbc5ba5bac
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709835"
---
# <a name="xmlschemacollection-schema-compilation"></a>XmlSchemaCollection Şema Derlemesi
**XmlSchemaCollection** , XML verileri AZALTıLMıŞ (xdr) ve XML şeması tanım DILI (xsd) şemaları depolanabilecek ve doğrulanabilen bir önbellek veya kitaplıktır. **XmlSchemaCollection** , şemaları bir dosya veya URL 'den erişmek yerine bellekte önbelleğe alarak performansı geliştirir.  
  
> [!NOTE]
> **XmlSchemaCollection** sınıfı hem XDR şemaları hem de XML şemaları depolasa da, **XmlSchema** nesnesi alan veya döndüren herhangi bir yöntem ve özellik yalnızca XML şemalarını destekler.  
  
> [!IMPORTANT]
> <xref:System.Xml.Schema.XmlSchemaCollection> sınıf artık kullanımdan kalkmıştır ve <xref:System.Xml.Schema.XmlSchemaSet> sınıfıyla değiştirilmiştir. <xref:System.Xml.Schema.XmlSchemaSet> sınıfı hakkında daha fazla bilgi için bkz. [şema derlemesi Için XmlSchemaSet](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md).  
  
## <a name="add-schemas-to-the-collection"></a>Koleksiyona şemalar ekleme  
 Şemalar, şema bir ad alanı URI 'siyle ilişkili olan **XmlSchemaCollection**'ın **Add** yöntemi kullanılarak koleksiyona yüklenir. XML şemaları için ad alanı URI 'SI genellikle şemanın hedef ad alanı olacaktır. XDR şemaları için ad alanı URI 'SI, şema koleksiyona eklendiğinde belirtilen ad alanıdır.  
  
## <a name="check-for-a-schema-in-the-collection"></a>Koleksiyondaki şemayı denetle  
 **Contains** metodunu kullanarak bir şemanın koleksiyonda olup olmadığını kontrol edebilirsiniz. **Contains** yöntemi bir **XmlSchema** nesnesi (yalnızca XML şemaları için) ya da ŞEMAYLA ilişkili ad alanı URI 'sini temsil eden bir dizeyi (XML şemaları ve XDR şemaları için) alır.  
  
## <a name="retrieve-a-schema-from-the-collection"></a>Koleksiyondan bir şema alma  
 **Öğe** özelliğini kullanarak koleksiyondan bir şema alabilirsiniz. **Öğe** özelliği, şemayla ilişkili ad alanı URI 'sini temsil eden bir dize alır, genellikle hedef ad alanı ve bir **XmlSchema** nesnesi döndürür. **Öğe** ÖZELLIĞI yalnızca XML şemaları için geçerlidir. Bir nesne modeli mevcut olmadığından, dönüş değeri her zaman XDR şemaları için bir null başvurudur.  
  
## <a name="validate-xml-documents-using-xmlschemacollection"></a>XmlSchemaCollection kullanarak XML belgelerini doğrulama  
 **XmlSchemaCollection nesnesini oluşturarak** , şemalarınızı koleksiyona ekleyerek ve **XmlValidatingReader** üzerinde oluşturulan **XmlSchemaCollection** 'ı atamak için, XmlValidatingReader üzerinde **şemalar** özelliğini ayarlayarak bir **XmlSchemaCollection** kullanarak bir XML örnek belgesini **doğrulayabilirsiniz.**  
  
### <a name="improved-performance"></a>İyileştirilmiş performans  
 Aynı şemaya karşı birden fazla belge doğrulmanız önerilir, bu, bir şemayı bellekte önbelleğe alarak daha iyi performans sağladığından, **XmlSchemaCollection** 'ı kullanıyorsunuz.  
  
 Aşağıdaki kod örneği, **XmlSchemaCollection** nesnesini oluşturur, koleksiyona şemalar ekler ve **şemalar** özelliğini ayarlar.  
  
```vb  
Dim tr as XmlTextReader = new XmlTextReader("Books.xml")  
Dim vr as XmlValidatingReader = new XmlValidatingReader(tr)  
Dim xsc as XmlSchemaCollection = new XmlSchemaCollection  
xsc.Add("urn:bookstore-schema", "Books.xsd")  
vr.Schemas.Add(xsc)  
```  
  
```csharp  
XmlTextReader tr = new XmlTextReader("Books.xml");  
XmlValidatingReader vr = new XmlValidatingReader(tr);  
XmlSchemaCollection xsc = new XmlSchemaCollection();  
xsc.Add("urn:bookstore-schema", "Books.xsd");    
vr.Schemas.Add(xsc);  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XmlSchemaCollection ile XDR Doğrulaması](../../../../docs/standard/data/xml/xdr-validation-with-xmlschemacollection.md)
- [XmlSchemaCollection ile XML Şeması (XSD) Doğrulaması](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemacollection.md)
