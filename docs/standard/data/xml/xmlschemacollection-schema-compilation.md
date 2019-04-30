---
title: XmlSchemaCollection Şema Derlemesi
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 76f28770-7126-428f-9ed5-7b5ae8bad5ee
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3d47fa4d4ef7a55182dd27aa6f64542fec1fa99c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61776044"
---
# <a name="xmlschemacollection-schema-compilation"></a>XmlSchemaCollection Şema Derlemesi
**XmlSchemaCollection** bir önbellek ya da burada XML verileri azaltılmış (XDR) ve XML Şeması Tanım Dili (XSD) şemalarını depolanabilir ve doğrulanmış kitaplığı. **XmlSchemaCollection** şemaları bir dosyadan veya URL'den erişmek yerine bellekte önbelleğe alarak performansını artırır.  
  
> [!NOTE]
>  Ancak **XmlSchemaCollection** sınıfı, hem XDR şema hem de XML şemaları, herhangi bir yöntemi ve alan veya döndüren özellik depolayan bir **XmlSchema** nesnesi XML şemaları yalnızca destekler.  
  
> [!IMPORTANT]
>  <xref:System.Xml.Schema.XmlSchemaCollection> Sınıf artık kullanımdan kalkmıştır ve ile değiştirilmiştir <xref:System.Xml.Schema.XmlSchemaSet> sınıfı. Hakkında daha fazla bilgi için <xref:System.Xml.Schema.XmlSchemaSet> sınıfı bakın [şema derleme için XmlSchemaSet](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md).  
  
## <a name="add-schemas-to-the-collection"></a>Şemalar koleksiyonuna ekleme  
 Şema koleksiyonu kullanarak yüklenir **Ekle** yöntemi **XmlSchemaCollection**, aynı zamanda Şema ad alanı URI ile ilişkilidir. XML şemaları için ad alanı URI genellikle şema hedef ad alanı olacaktır. XDR Şema ad alanı URI ad alanı şema koleksiyonuna zaman eklendi belirtilmiştir.  
  
## <a name="check-for-a-schema-in-the-collection"></a>Bir şema koleksiyonunda denetle  
 Kullanarak bir şema koleksiyonunda olup olmadığını kontrol edebilirsiniz **içerir** yöntemi. **İçerir** yöntemi alır ya da bir **XmlSchema** nesnesi (yalnızca XML şemaları) veya ad alanı URI temsil eden bir dize (için XML şemaları ve XDR şema) şema ile ilişkili.  
  
## <a name="retrieve-a-schema-from-the-collection"></a>Koleksiyondan bir şema alınamıyor  
 Kullanarak bir şema koleksiyondan alabilirsiniz **öğesi** özelliği. **Öğesi** özelliği, hedef ad alanı genellikle, şema ile ilişkili URI ad alanı temsil eden bir dize alır ve döndürür bir **XmlSchema** nesne. **Öğesi** özelliği için XML şemaları yalnızca uygulanır. Nesne modeli kullanılabilir olmadığı için dönüş değeri her zaman bir null XDR şema içindir.  
  
## <a name="validate-xml-documents-using-xmlschemacollection"></a>XmlSchemaCollection kullanarak XML belgeleri doğrulamak  
 Bir XML örneği belge kullanarak doğrulayabilirsiniz bir **XmlSchemaCollection** oluşturarak **XmlSchemaCollection** , şemalar koleksiyonuna ekleme ve ayar nesnesi **şemaları**  özelliği **XmlValidatingReader** oluşturulan atamak **XmlSchemaCollection** için **XmlValidatingReader**.  
  
### <a name="improved-performance"></a>Geliştirilmiş performans  
 Tavsiye edilir, aynı şemaya birden fazla belge doğrulamakta olduğunuz varsa kullanmanızı **XmlSchemaCollection** çünkü şemaları bellekte önbelleğe alarak daha iyi performans sağlar.  
  
 Aşağıdaki kod örneği oluşturur **XmlSchemaCollection** nesnesi şemalar koleksiyonuna ekler ve ayarlar **şemaları** özelliği.  
  
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
