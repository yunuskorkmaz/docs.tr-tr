---
title: Varlık başvuruları genişletilir ve korunmaz olan
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: ffd97806-ab43-4538-8de2-5828bfbbde57
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7a55aa71ff3976241b96dd12baef06a9a13ef9dd
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43873740"
---
# <a name="entity-references-are-expanded-and-not-preserved"></a>Varlık başvuruları genişletilir ve korunmaz olan
Varlık başvurusu genişletilmiş ve temsil ettiği metin tarafından değiştirilen **XmlEntityReference** düğüm oluşturulmaz. Bunun yerine, varlık bildirimi ayrıştırılır ve bildirimde içeriğinden oluşturulan düğümler yerine, kopyalanır **XmlEntityReference**. Bu nedenle `&publisher;` örnek, `&publisher;` , ancak bunun yerine, kaydedilmemiş bir **XmlText** düğüm oluşturulur.  
  
 ![Genişletilmiş ağaç yapısı](../../../../docs/standard/data/xml/media/xmlentityref-expanded-nodes.gif "xmlentityref_expanded_nodes")  
Genişletilmiş varlık başvuruları için ağaç yapısı  
  
 Varlıklar gibi karakter `B` veya `<` korunmaz. Bunun yerine, bunlar her zaman genişletilmiş ve metin düğümleri temsil edilir.  
  
 Korumak için **XmlEntityReference** ayarlayın, düğümleri ve alt düğümleri varlık başvurusunun iliştirilmiş **EntityHandling** bayrak **ExpandCharEntities**. Aksi halde bırakın **EntityHandling** için varsayılan bayrağı **ExpandEntities**. Bu durumda, varlık başvurusu düğümler yerli görmezsiniz Düğümlerinin alt düğümleri varlık bildirimin kopyalarını düğümleri tarafından değiştirilir.  
  
 Varlık başvuruları koruma değil bir yan etkisi, Belge kaydedildiğinde ve başka bir uygulama için geçen zaman alıcı uygulama düğümleri bir varlık başvurusu tarafından oluşturulan tanımadığını ' dir. Ancak, varlık başvuruları korunur, alıcı uygulamanın bir varlık başvurusu görür ve alt düğümleri okur. Alt düğümler varlık bildiriminde bilgilerin temsil açıktır. Örneğin, varlık başvuruları korunur, DOM teorik olarak aşağıdaki yapıya sahiptir.  
  
 XmlElement: Yayımcı  
  
 XmlEntityReference: `&publisher;`  
  
 XmlText: Microsoft Press  
  
 Varsayılan yöntemi olan DOM'da varlık başvuruları genişletilir, bu tür bir ağaç yapısı vardır:  
  
 XmlElement: Yayımcı  
  
 XmlText: Microsoft Press  
  
 Varlık referans düğümün kalktığını ve alıcı uygulama, bilgi Uyarısı **XmlText** düğümünü "Microsoft Press" içeren bir varlık bildiriminden oluşturuldu.  
  
 Varlıklar, çözümlenemiyor bir okuyucu kullanırsanız **yük** yöntemi, bir varlık başvurusu karşılaştığında bir özel durum oluşturur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
