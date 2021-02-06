---
description: 'Hakkında daha fazla bilgi edinin: varlık başvuruları korunur'
title: Varlık Başvuruları Korunur
ms.date: 03/30/2017
ms.assetid: 000a6cae-5972-40d6-bd6c-a9b7d9649b3c
ms.openlocfilehash: 189096d2dd87731a06fdb805ba5f041c041e26b9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99629636"
---
# <a name="entity-references-are-preserved"></a>Varlık Başvuruları Korunur

Varlık başvurusu genişletilmemişse ancak korunmadığında, XML Belge Nesne Modeli (DOM) bir varlık başvurusuyla karşılaştığında bir **XmlEntityReference** düğümü oluşturur.  
  
 Aşağıdaki XML 'i kullanarak  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 DOM, başvuruyla karşılaştığında bir **XmlEntityReference** düğümü oluşturur `&publisher;` . **XmlEntityReference** , varlık bildiriminde içerikten kopyalanmış alt düğümleri içerir. Önceki kod örneği varlık bildiriminde metin içerir, bu nedenle bir **XmlText** düğümü varlık başvurusu düğümünün alt düğümü olarak oluşturulur.  
  
 ![Korunan varlık başvuruları için ağaç yapısı](media/xmlentityref-notexpanded-nodes.gif "xmlentityref_notexpanded_nodes")  
Korunan varlık başvuruları için ağaç yapısı  
  
 **XmlEntityReference** alt düğümleri, varlık bildirimi Ile karşılaşıldığında **XmlEntity** düğümünden oluşturulan tüm alt düğümlerin kopyalardır.  
  
> [!NOTE]
> **XmlEntity** 'den kopyalanmış düğümler, varlık başvurusu düğümü altına yerleştirildiğinde her zaman tam kopya değildir. Varlık başvurusu düğümünde kapsamda olan ve alt düğümlerin son yapılandırmasını etkileyen ad alanları olabilir.  
  
 Varsayılan olarak, gibi genel varlıklar `&abc;` korunur ve **XmlEntityReference** düğümleri her zaman oluşturulur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](xml-document-object-model-dom.md)
