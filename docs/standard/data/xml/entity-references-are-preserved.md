---
title: Varlık Başvuruları Korunur
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 000a6cae-5972-40d6-bd6c-a9b7d9649b3c
ms.openlocfilehash: 0fd427388a065bd4c689d087c22fd6d69046b8a9
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710927"
---
# <a name="entity-references-are-preserved"></a>Varlık Başvuruları Korunur
Varlık başvurusu genişletilmemişse ancak korunmadığında, XML Belge Nesne Modeli (DOM) bir varlık başvurusuyla karşılaştığında bir **XmlEntityReference** düğümü oluşturur.  
  
 Aşağıdaki XML 'i kullanarak  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 DOM, `&publisher;` başvurusuyla karşılaştığında bir **XmlEntityReference** düğümü oluşturur. **XmlEntityReference** , varlık bildiriminde içerikten kopyalanmış alt düğümleri içerir. Önceki kod örneği varlık bildiriminde metin içerir, bu nedenle bir **XmlText** düğümü varlık başvurusu düğümünün alt düğümü olarak oluşturulur.  
  
 ![Korunan varlık başvuruları için ağaç yapısı](../../../../docs/standard/data/xml/media/xmlentityref-notexpanded-nodes.gif "xmlentityref_notexpanded_nodes")  
Korunan varlık başvuruları için ağaç yapısı  
  
 **XmlEntityReference** alt düğümleri, varlık bildirimi Ile karşılaşıldığında **XmlEntity** düğümünden oluşturulan tüm alt düğümlerin kopyalardır.  
  
> [!NOTE]
> **XmlEntity** 'den kopyalanmış düğümler, varlık başvurusu düğümü altına yerleştirildiğinde her zaman tam kopya değildir. Varlık başvurusu düğümünde kapsamda olan ve alt düğümlerin son yapılandırmasını etkileyen ad alanları olabilir.  
  
 Varsayılan olarak, `&abc;` gibi genel varlıklar korunur ve **XmlEntityReference** düğümleri her zaman oluşturulur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
