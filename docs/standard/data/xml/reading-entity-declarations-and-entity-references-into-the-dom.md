---
title: Varlık bildirimleri ve varlık başvuruları DOM okuma
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 86dba977-5cc4-4567-964f-027ffabc47b2
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 986f0f1d6ce20722b85ac0cfa9e3fe3fa351b75e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33569661"
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
  
 **Output**  
  
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
 [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
