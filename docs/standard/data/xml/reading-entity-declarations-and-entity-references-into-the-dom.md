---
title: DOM’da Varlık Bildirimleri ve Varlık Başvuruları Okuma
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 86dba977-5cc4-4567-964f-027ffabc47b2
ms.openlocfilehash: fa650e75d7661eeafea74146f5cbb61878978575
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710407"
---
# <a name="reading-entity-declarations-and-entity-references-into-the-dom"></a>DOM’da Varlık Bildirimleri ve Varlık Başvuruları Okuma
Varlık, içerik veya biçimlendirme yerine XML 'de kullanılacak adı belirten bir bildirimidir. Varlıkların iki bölümü vardır. İlk olarak, bir varlık bildirimi kullanarak bir adı değiştirme içeriğine bağlamamalısınız. Bir varlık bildirimi, bir belge türü tanımı (DTD) veya XML şemasında `<!ENTITY name "value">` söz dizimi kullanılarak oluşturulur. İkinci olarak, varlık bildiriminde tanımlanan ad daha sonra XML 'de kullanılır. XML 'de kullanıldığında, bir varlık başvurusu olarak adlandırılır. Örneğin, aşağıdaki varlık bildirimi, "Microsoft Press" içeriğiyle ilişkili `publisher` adının bir varlığını bildirir.  
  
```xml  
<!ENTITY publisher "Microsoft Press">  
```  
  
 Aşağıdaki örnek bir varlık başvurusu olarak XML 'de bu varlık bildiriminin kullanımını gösterir.  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 Bazı çözümleyiciler, bir belge belleğe yüklendiğinde varlıkları otomatik olarak genişletir. Bu nedenle, XML belleğe okunmakta olduğunda, varlık bildirimleri hatırlanır ve kaydedilir. Ayrıştırıcı daha sonra genel bir varlık başvurusunu tanımlayan `&;` karakterlerle karşılaştığında, ayrıştırıcı bu adı bir varlık bildirim tablosunda arar. Başvuru, `&publisher;` gösterdiği içerikle değiştirilmiştir. Aşağıdaki XML 'i kullanarak  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 varlık başvurusunu genişletmek ve `&publisher;` Microsoft Press içeriğiyle değiştirmek, aşağıdaki genişletilmiş XML 'yi sağlar.  
  
 **Output**  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by Microsoft Press</pubinfo>  
```  
  
 Birçok varlık türü vardır. Aşağıdaki diyagramda, varlık türlerinin ve terminolojinin dökümü gösterilmektedir.  
  
 ![varlık türü hiyerarşisinin akış grafiği](../../../../docs/standard/data/xml/media/entity-hierarchy.gif "Entity_hierarchy")  
  
 XML Belge Nesne Modeli (DOM) Microsoft .NET Framework uygulamasının varsayılan örneği, varlıkların başvurularını korumasıdır ve XML yüklendiğinde varlıkları genişletmez. Bunun, DOM 'a bir belge yüklendiği, DTD 'de bildirildiği varlıktaki içeriği temsil eden alt düğümler ile `&publisher;` başvuru değişkenini içeren bir **XmlEntityReference** düğümünün oluşturulduğu bir ifade.  
  
 `<!ENTITY publisher "Microsoft Press">` varlık bildirimini kullanarak, aşağıdaki diyagramda bu bildirimden oluşturulan **XmlEntity** ve **XmlText** düğümleri gösterilmektedir.  
  
 ![varlık bildiriminden oluşturulan düğümler](../../../../docs/standard/data/xml/media/xml-entitydeclaration-node2.png "xml_entitydeclaration_node2")  
  
 Varlık başvurularının genişletilme ve bu durumlarda, DOM ağacında bellek içinde oluşturulan düğümlerin bir farkı olmayan farklar. Oluşturulan düğümlerdeki fark, [varlık başvuruları korunur](../../../../docs/standard/data/xml/entity-references-are-preserved.md) ve [varlık başvuruları genişletilir ve korunmaz](../../../../docs/standard/data/xml/entity-references-are-expanded-and-not-preserved.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
