---
title: Varlık Başvuruları Korunur
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 000a6cae-5972-40d6-bd6c-a9b7d9649b3c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b1c48e42e55025aff0ce1a24a3ef45ddf8005eab
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61934543"
---
# <a name="entity-references-are-preserved"></a>Varlık Başvuruları Korunur
Varlık başvurusu genişletilmiş, ancak korunur, XML belge nesne modeli (DOM) derlemeleri bir **XmlEntityReference** bir varlık başvurusu karşılaştığında düğümü.  
  
 Aşağıdaki XML kullanarak  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 DOM derlemeleri bir **XmlEntityReference** karşılaştığında bu düğüm `&publisher;` başvuru. **XmlEntityReference** varlık bildiriminde içeriğinden kopyalanan alt düğümleri içerir. Yukarıdaki kod örneğinde metni varlık bildirimde, bu nedenle içeren bir **XmlText** düğüm varlık referans düğümün alt düğümü olarak oluşturulur.  
  
 ![Ağaç yapısı Korunan varlık başvuruları için](../../../../docs/standard/data/xml/media/xmlentityref-notexpanded-nodes.gif "xmlentityref_notexpanded_nodes")  
Korunur varlık başvuruları için ağaç yapısı  
  
 Alt düğümleri **XmlEntityReference** tüm alt kopyalarını oluşturulan düğümlerdir **XmlEntity** varlık bildirimi karşılaştığında düğümü.  
  
> [!NOTE]
>  Öğesinden kopyalanan düğümleri **XmlEntity** olmayan her zaman tam kopya varlık referans düğümün altında kez yerleştirilir. Varlık referans düğümün kapsamda bulunan ad olabilir ve bu alt düğümlerin son yapılandırma etkiler.  
  
 Varsayılan olarak, genel varlıklar ister `&abc;` korunur ve **XmlEntityReference** düğümleri her zaman oluşturulur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
