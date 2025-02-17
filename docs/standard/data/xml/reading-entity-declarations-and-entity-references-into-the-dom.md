---
description: "Hakkında daha fazla bilgi edinin: DOM 'a varlık bildirimleri ve varlık başvuruları okuma"
title: DOM’da Varlık Bildirimleri ve Varlık Başvuruları Okuma
ms.date: 03/30/2017
ms.assetid: 86dba977-5cc4-4567-964f-027ffabc47b2
ms.openlocfilehash: 312fd215076f4b0eee280767b8c367d34ffe6bb6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783228"
---
# <a name="reading-entity-declarations-and-entity-references-into-the-dom"></a>DOM’da Varlık Bildirimleri ve Varlık Başvuruları Okuma

Varlık, içerik veya biçimlendirme yerine XML 'de kullanılacak adı belirten bir bildirimidir. Varlıkların iki bölümü vardır. İlk olarak, bir varlık bildirimi kullanarak bir adı değiştirme içeriğine bağlamamalısınız. Bir varlık bildirimi, `<!ENTITY name "value">` bir belge türü tanımı (DTD) veya XML şemasında sözdizimi kullanılarak oluşturulur. İkinci olarak, varlık bildiriminde tanımlanan ad daha sonra XML 'de kullanılır. XML 'de kullanıldığında, bir varlık başvurusu olarak adlandırılır. Örneğin, aşağıdaki varlık bildirimi `publisher` "Microsoft Press" içeriğiyle ilişkili olan adın bir varlığını bildirir.  
  
```xml  
<!ENTITY publisher "Microsoft Press">  
```  
  
 Aşağıdaki örnek bir varlık başvurusu olarak XML 'de bu varlık bildiriminin kullanımını gösterir.  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 Bazı çözümleyiciler, bir belge belleğe yüklendiğinde varlıkları otomatik olarak genişletir. Bu nedenle, XML belleğe okunmakta olduğunda, varlık bildirimleri hatırlanır ve kaydedilir. Ayrıştırıcı daha sonra `&;` genel bir varlık başvurusunu tanımlayan karakterlerle karşılaştığında, ayrıştırıcı bu adı bir varlık bildirim tablosunda arar. Başvuru, `&publisher;` gösterdiği içerikle değiştirilmiştir. Aşağıdaki XML 'i kullanarak  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 varlık başvurusunu genişletmek ve `&publisher;` Microsoft Press içeriğiyle değiştirmek, aşağıdaki GENIŞLETILMIŞ XML 'yi sağlar.  
  
 **Çıktı**  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by Microsoft Press</pubinfo>  
```  
  
 Birçok varlık türü vardır. Aşağıdaki diyagramda, varlık türlerinin ve terminolojinin dökümü gösterilmektedir.  
  
 ![varlık türü hiyerarşisinin akış grafiği](media/entity-hierarchy.gif "Entity_hierarchy")  
  
 XML Belge Nesne Modeli (DOM) Microsoft .NET Framework uygulamasının varsayılan örneği, varlıkların başvurularını korumasıdır ve XML yüklendiğinde varlıkları genişletmez. Bu, DOM 'da bir belge yüklendiği için,  `&publisher;` DTD 'de bildirildiği varlıktaki içeriği temsil eden alt düğümler ile başvuru değişkenini içeren bir XmlEntityReference düğümü oluşturulur.  
  
 `<!ENTITY publisher "Microsoft Press">`Varlık bildirimini kullanarak, aşağıdaki diyagramda bu bildirimden oluşturulan **XmlEntity** ve **XmlText** düğümleri gösterilmektedir.  
  
 ![varlık bildiriminden oluşturulan düğümler](media/xml-entitydeclaration-node2.png "xml_entitydeclaration_node2")  
  
 Varlık başvurularının genişletilme ve bu durumlarda, DOM ağacında bellek içinde oluşturulan düğümlerin bir farkı olmayan farklar. Oluşturulan düğümlerdeki fark, [varlık başvuruları korunur](entity-references-are-preserved.md) ve [varlık başvuruları genişletilir ve korunmaz](entity-references-are-expanded-and-not-preserved.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](xml-document-object-model-dom.md)
