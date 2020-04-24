---
title: Varlık Başvuruları Genişletilir ve Korunmaz
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: ffd97806-ab43-4538-8de2-5828bfbbde57
ms.openlocfilehash: ae3db77d7659b7e1d36a9bccf7143f52c536dbbf
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710940"
---
# <a name="entity-references-are-expanded-and-not-preserved"></a>Varlık Başvuruları Genişletilir ve Korunmaz
Varlık başvurusu genişletildiğinde ve gösterdiği metin tarafından değiştirildiğinde, **XmlEntityReference** düğümü oluşturulmaz. Bunun yerine, varlık bildirimi ayrıştırılır ve bildirimdeki içerikten oluşturulan düğümler **XmlEntityReference**yerine kopyalanır. Bu nedenle, `&publisher;` örnekte `&publisher;` kaydedilmez, ancak bunun yerine **XmlText** düğümü oluşturulur.  
  
 ![Genişletilmiş ağaç yapısı](../../../../docs/standard/data/xml/media/xmlentityref-expanded-nodes.gif "xmlentityref_expanded_nodes")  
Genişletilmiş varlık başvuruları için ağaç yapısı  
  
 `B` Veya `<` gibi karakter varlıkları korunmaz. Bunun yerine, her zaman genişletilir ve metin düğümleri olarak gösterilir.  
  
 **XmlEntityReference** düğümlerini ve ona iliştirilmiş Varlık başvurusunun alt düğümlerini korumak Için, **EntityHandling** bayrağını **ExpandCharEntities**olarak ayarlayın. Aksi halde, **EntityHandling** bayrağını varsayılan konumda bırakın, bu, **ExpandEntities**. Bu durumda, DOM 'da varlık başvurusu düğümlerini görmezsiniz. Düğümler, varlık bildiriminin alt düğümlerinin kopyaları olan düğümlerle değiştirilmiştir.  
  
 Varlık başvurularını korumadan bir yan etkisi, belge kaydedilip başka bir uygulamaya geçirildiğinde, alıcı uygulamanın düğümlerin bir varlık başvurusu tarafından oluşturulduğunu bilmez. Ancak, varlık başvuruları korunduğunda, alıcı bir uygulama bir varlık başvurusu görür ve alt düğümleri okur. Alt düğümlerin varlık bildiriminde bulunan bilgileri temsil ettiği görünür. Örneğin, varlık başvuruları korunsa, DOM teorik olarak aşağıdaki yapıya sahiptir.  
  
 XmlElement: Yayımcı  
  
 XmlEntityReference:`&publisher;`  
  
 XmlText: Microsoft Press  
  
 Varlık başvuruları DOM 'da genişletilmişse (varsayılan yöntem), yapı bu ağaç türüne sahiptir:  
  
 XmlElement: Yayımcı  
  
 XmlText: Microsoft Press  
  
 Varlık başvurusu düğümünün kaybolduğuna ve alıcı uygulamanın "Microsoft Press" içeren **XmlText** düğümünün bir varlık bildiriminden oluşturulduğunu söylüdiğine dikkat edin.  
  
 Varlıkları çözümleyemediği bir okuyucu kullanıyorsanız, **Load** yöntemi bir varlık başvurusuyla karşılaştığında bir özel durum oluşturur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
