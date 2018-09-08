---
title: DOM'da varlık bildirimleri ve varlık başvuruları okuma
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 86dba977-5cc4-4567-964f-027ffabc47b2
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e30b52b8cdfb4d185687d58c80f4475730031c86
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44185801"
---
# <a name="reading-entity-declarations-and-entity-references-into-the-dom"></a>DOM'da varlık bildirimleri ve varlık başvuruları okuma
XML içeriği veya biçimlendirme yerine kullanılmak üzere bir adını belirten bir bildirimi bir varlıktır. Varlıkları iki bölümü vardır. İlk olarak, bir ad kullanarak bir varlık bildirimi değiştirme içerik bağlamak gerekir. Bir varlık bildirimi kullanılarak oluşturulan `<!ENTITY name "value">` belge türü tanımı (DTD'nin) veya XML şema söz dizimi. İkincisi, varlık bildiriminde tanımlanan adını XML bundan sonra kullanılır. XML'de kullanıldığında, bir varlık başvurusu adı verilir. Örneğin, aşağıdaki varlık bildirimi varlığın adını bildirir `publisher` "Microsoft Press" içeriğini ile ilişkilendiriliyor.  
  
```xml  
<!ENTITY publisher "Microsoft Press">  
```  
  
 Aşağıdaki örnek, bir varlık başvurusu XML içinde bu varlık bildirim kullanımını göstermektedir.  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 Bir belge belleğe yüklendiğinde bazı Çözümleyicileri varlıkları otomatik olarak genişletin. XML belleğe okuyun, bu nedenle, varlık bildirimleri anımsanacak kaydedildi ve. Daha sonra karşılaştığında `&;` , genel varlık başvurusu tanımlayın, karakterler ayrıştırıcı bir varlık bildirimi tablosunun ad arar. Başvuru `&publisher;` temsil ettiği içerik ile değiştirilir. Aşağıdaki XML kullanarak  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 Varlık başvurusu genişletme ve değiştirerek `&publisher;` ile Microsoft Press, şu genişletilmiş XML içeriği sağlar.  
  
 **Output**  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by Microsoft Press</pubinfo>  
```  
  
 Varlıkları birçok çeşit vardır. Aşağıdaki diyagramda, terminolojisi ve varlık türleri dökümünü gösterir.  
  
 ![Akış Çizelgesi varlık türü hiyerarşisinin](../../../../docs/standard/data/xml/media/entity-hierarchy.gif "Entity_hierarchy")  
  
 Microsoft .NET Framework uygulaması XML belge nesne modeli (DOM) için varsayılan varlık başvuruları korur ve XML yüklendiğinde varlıkları genişletme değil sağlamaktır. Bir belge DOM, yüklü olan bu olduğu çıkarımında bir **XmlEntityReference** başvuru değişkenini içeren düğüm `&publisher;` oluşturulmuş, varlık içeriği temsil eden alt düğümler ile DTD'nin içinde bildirilmiş.  
  
 Kullanarak `<!ENTITY publisher "Microsoft Press">` varlık bildirimi, aşağıdaki diyagramda gösterilmiştir **XmlEntity** ve **XmlText** düğümleri bu bildirimden oluşturulur.  
  
 ![Varlık bildiriminden oluşturulan düğümler](../../../../docs/standard/data/xml/media/xml-entitydeclaration-node2.png "xml_entitydeclaration_node2")  
  
 Farklar varlık başvuruları genişletilir ve onlara hangi düğümleri DOM ağacında, bellekte oluşturulan içinde bir fark yapar. Oluşturulan düğümler arasındaki fark konularında açıklanan [varlık başvuruları korunur](../../../../docs/standard/data/xml/entity-references-are-preserved.md) ve [varlık başvuruları genişletilir ve korunmaz olan](../../../../docs/standard/data/xml/entity-references-are-expanded-and-not-preserved.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
