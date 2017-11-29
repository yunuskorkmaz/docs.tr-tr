---
title: "Varlık bildirimleri ve varlık başvuruları DOM okuma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 86dba977-5cc4-4567-964f-027ffabc47b2
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6370db06cbe7ff8d46258b0315059f5c37587fea
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="reading-entity-declarations-and-entity-references-into-the-dom"></a>Varlık bildirimleri ve varlık başvuruları DOM okuma
Bir varlık XML içeriği veya işaretleme yerine kullanılacak bir ad bildiren bir bildirimidir. Varlıkları iki bölümü vardır. İlk olarak, bir varlık bildirimi kullanarak değiştirme içerik için bir ad tie gerekir. Bir varlık bildirimi kullanılarak oluşturulan `<!ENTITY name "value">` bir belge türü tanımı (DTD) veya XML Şeması sözdiziminde. İkincisi, varlık bildiriminde tanımlanan adını sonradan XML'de kullanılır. XML'de kullanıldığında, bir varlık başvurusunun adı verilir. Örneğin, bir varlığın adı aşağıdaki varlık bildirimi bildirir `publisher` "Microsoft Press" içerikle ilişkili olan.  
  
```xml  
<!ENTITY publisher "Microsoft Press">  
```  
  
 Aşağıdaki örnek, bir varlık referans olarak XML'de bu varlık bildirim kullanımını göstermektedir.  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 Bir belge belleğe yüklendiğinde bazı ayrıştırıcıları varlıklar otomatik olarak genişletin. XML belleğe okuyun, bu nedenle, varlık bildirimleri hatırlanan kaydedilmiş ve. Daha sonra karşılaştığında `&;` genel varlık başvurusu tanımlamak, karakterleri ayrıştırıcı bir varlık bildirimi tablo ad arar. Başvuru `&publisher;` temsil ettiği içerik tarafından değiştirilir. Aşağıdaki XML kullanarak  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 Varlık başvurusu genişletme ve değiştirme `&publisher;` ile Microsoft Press aşağıdaki genişletilmiş XML içeriği sağlar.  
  
 **Çıktı**  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by Microsoft Press</pubinfo>  
```  
  
 Varlıkları birçok çeşit vardır. Aşağıdaki diyagramda, varlık türleri ve terminolojiyi dökümünü gösterir.  
  
 ![varlık türü hiyerarşisinin akış çizelgesi](../../../../docs/standard/data/xml/media/entity-hierarchy.gif "Entity_hierarchy")  
  
 Varlık başvuruları korumak ve XML yüklendiğinde varlıkları genişletme değil Microsoft .NET Framework uygulamasını XML belge nesne modeli (DOM) için varsayılan değer. Bir belge DOM'da yüklendiği gibi olduğu çıkarımında bulunulur Bu, bir **XmlEntityReference** başvuru değişkenini içeren düğüm `&publisher;` oluşturulmuş, varlık içeriği temsil eden alt düğümler ile DTD içinde bildirilen.  
  
 Kullanarak `<!ENTITY publisher "Microsoft Press">` varlık bildirimi, aşağıdaki diyagramda gösterilmiştir **XmlEntity** ve **XmlText** bu bildiriminden oluşturulan düğümler.  
  
 ![Varlık bildiriminden oluşturulan düğümler](../../../../docs/standard/data/xml/media/xml-entitydeclaration-node2.png "xml_entitydeclaration_node2")  
  
 Farkları varlık başvuruları genişletildiğinde ve olmadıkları zaman hangi düğümleri DOM ağaçta bellek oluşturulan içinde bir fark yapar. Oluşturulan düğümler arasındaki fark konularında açıklanan [varlık başvuruları korunur](../../../../docs/standard/data/xml/entity-references-are-preserved.md) ve [varlık başvuruları: genişletilmiş ve korunmaz](../../../../docs/standard/data/xml/entity-references-are-expanded-and-not-preserved.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML belge nesne modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
