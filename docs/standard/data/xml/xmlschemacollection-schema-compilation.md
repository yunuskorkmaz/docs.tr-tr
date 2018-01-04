---
title: "XmlSchemaCollection şema derleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 76f28770-7126-428f-9ed5-7b5ae8bad5ee
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c891736534741d1d3d3edb93d75d9f191c2dd573
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="xmlschemacollection-schema-compilation"></a>XmlSchemaCollection şema derleme
**XmlSchemaCollection** bir önbellek ya da nerede XML verileri azaltılmış (XDR) ve XML Şeması Tanım Dili (XSD) şemaları depolanabilir ve doğrulanmış kitaplığı. **XmlSchemaCollection** şemaları bir dosyaya veya URL'ye erişmesini yerine bellekte önbelleğe alarak performansı artırır.  
  
> [!NOTE]
>  Ancak **XmlSchemaCollection** sınıfı depolar XDR şemaları ve XML şemaları, yöntemi ve alır veya verir özelliği bir **XmlSchema** nesnesi XML şemaları yalnızca destekler.  
  
> [!IMPORTANT]
>  <xref:System.Xml.Schema.XmlSchemaCollection> Sınıf artık kullanımdan kalkmıştır ve ile değiştirilmiştir <xref:System.Xml.Schema.XmlSchemaSet> sınıfı. Hakkında daha fazla bilgi için <xref:System.Xml.Schema.XmlSchemaSet> sınıfı bakın, [şema derleme için XmlSchemaSet](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md).  
  
## <a name="add-schemas-to-the-collection"></a>Şema koleksiyonuna Ekle  
 Şema koleksiyonu kullanarak yüklenir **Ekle** yöntemi **XmlSchemaCollection**, aynı zamanda Şema ad alanı URI'si ile ilişkilidir. XML şemaları için ad alanı URI şeması için hedef ad alanı genellikle olacaktır. XDR şema için ad alanı URI'si ad şema koleksiyonuna zaman eklendi belirtilmiştir.  
  
## <a name="check-for-a-schema-in-the-collection"></a>Bir şema koleksiyonunda denetle  
 Kullanarak bir şema koleksiyonunda olup olmadığını görmek için kontrol edebilirsiniz **içerir** yöntemi. **İçerir** yöntemi alır ya da bir **XmlSchema** nesnesi (yalnızca XML şemaları) veya ad alanı URI'si temsil eden bir dize (XML şemaları ve XDR şemaları için) şema ile ilişkili.  
  
## <a name="retrieve-a-schema-from-the-collection"></a>Koleksiyondan bir şema Al  
 Kullanarak bir şema koleksiyondan alabilirsiniz **öğesi** özelliği. **Öğesi** özelliği ad alanı URI şeması, genellikle hedef ad alanı, ilişkili temsil eden bir dize alır ve döndüren bir **XmlSchema** nesnesi. **Öğesi** özelliği için XML şemaları yalnızca uygulanır. Nesne modeli kullanılabilir olmadığından dönüş değeri her zaman null XDR şemaları için başvurudur.  
  
## <a name="validate-xml-documents-using-xmlschemacollection"></a>XML belgeleri XmlSchemaCollection kullanarak doğrula  
 Bir XML örneği belge kullanarak doğrulayabilirsiniz bir **XmlSchemaCollection** oluşturarak **XmlSchemaCollection** , şemalar koleksiyona ekleme ve ayar nesnesi **şemaları**  özelliği **XmlValidatingReader** oluşturulan atamak için **XmlSchemaCollection** için **XmlValidatingReader**.  
  
### <a name="improved-performance"></a>Geliştirilmiş performans  
 Önerilir, birden çok belgeyi aynı şemaya karşı doğrulama varsa, kullandığınız **XmlSchemaCollection** çünkü şemaları bellekte önbelleğe alarak daha iyi performans sağlar.  
  
 Aşağıdaki kod örneği oluşturur **XmlSchemaCollection** nesne, şema koleksiyonuna ekler ve ayarlar **şemaları** özelliği.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XmlSchemaCollection ile XDR Doğrulaması](../../../../docs/standard/data/xml/xdr-validation-with-xmlschemacollection.md)  
 [XmlSchemaCollection ile XML Şeması (XSD) Doğrulaması](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemacollection.md)
