---
title: Genişletilmiş ve korunmaz varlık başvuruları olan
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: ffd97806-ab43-4538-8de2-5828bfbbde57
author: mairaw
ms.author: mairaw
ms.openlocfilehash: aa03532200a89aa164648c1278c9dbafc2aee214
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="entity-references-are-expanded-and-not-preserved"></a>Genişletilmiş ve korunmaz varlık başvuruları olan
Varlık başvurusu genişletilmiş ve temsil ettiği, metnin tarafından yerine **XmlEntityReference** düğümü oluşturulmadı. Bunun yerine, varlık bildirimi ayrıştırılır ve bildiriminde içerikten oluşturulan düğümler yerine, kopyaladığınız **XmlEntityReference**. Bu nedenle, içinde `&publisher;` örnek, `&publisher;` , ancak bunun yerine, kaydedilmez bir **XmlText** düğüm oluşturulur.  
  
 ![Genişletilmiş ağaç yapısı](../../../../docs/standard/data/xml/media/xmlentityref-expanded-nodes.gif "xmlentityref_expanded_nodes")  
Genişletilmiş varlık başvuruları için ağaç yapısı  
  
 Varlıklar gibi karakter `B` veya `<` korunmaz. Bunun yerine, bunlar her zaman genişletilmiş ve metin düğümleri olarak temsil.  
  
 Korumak için **XmlEntityReference** düğümleri ve alt düğümleri varlık başvurusunun bağlı şekilde, Ayarla **EntityHandling** bayrağını **ExpandCharEntities**. Aksi takdirde bırakın **EntityHandling** için varsayılan olarak bayrağına **ExpandEntities**. Bu durumda, varlık başvurusu düğümler DOM görmezsiniz Düğümleri varlık bildirim alt düğümleri kopyalarıdır düğümleri tarafından değiştirilir.  
  
 Varlık başvuruları koruma değil bir yan etkisi, Belge kaydedildiğinde ve başka bir uygulama için geçen zaman alıcı uygulama düğümleri varlık başvurusu tarafından oluşturulan bilmez emin olur. Bununla birlikte, varlık başvuruları korunur, alıcı uygulamanın bir varlık başvurusunun görür ve alt düğümleri okur. Alt düğümler varlık bildiriminde olan bilgileri temsil açıktır. Örneğin, varlık başvuruları korunur, DOM teorik olarak aşağıdaki yapısını olmaz.  
  
 XmlElement: Yayımcı  
  
 XmlEntityReference: `&publisher;`  
  
 XmlText: Microsoft Press  
  
 Varlık başvuruları varsayılan yöntemi olan DOM'da genişlettiyseniz bu tür bir ağaç yapısı vardır:  
  
 XmlElement: Yayımcı  
  
 XmlText: Microsoft Press  
  
 Varlık referans düğümün kayboluyor ve alma işlemini yapan uygulamanın, bildiremez bildirimi **XmlText** düğümü "Microsoft Press" içeren bir varlık bildiriminden oluşturuldu.  
  
 Varlıkları çözümlenemiyor bir okuyucu kullanıyorsanız **yük** yöntemi, bir varlık başvurusunun karşılaştığında bir özel durum oluşturur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
