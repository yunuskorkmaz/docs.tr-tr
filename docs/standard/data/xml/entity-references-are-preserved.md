---
title: "Varlık başvuruları korunur"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 000a6cae-5972-40d6-bd6c-a9b7d9649b3c
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: f5a867d1301355f4c9a77654556229274f96d00c
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="entity-references-are-preserved"></a>Varlık başvuruları korunur
Varlık başvurusu genişletilmiş, ancak korunur, XML belge nesne modeli (DOM) derlemeler bir **XmlEntityReference** bir varlık başvurusunun karşılaştığında düğümü.  
  
 Aşağıdaki XML kullanarak  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 DOM derlemeler bir **XmlEntityReference** onu karşılaştığında düğümü `&publisher;` başvuru. **XmlEntityReference** varlık bildiriminin içeriği kopyalanan alt düğümleri içerir. Bu nedenle önceki kod örneğinde varlık bildiriminde metni içeren bir **XmlText** düğümü varlık referans düğümün alt düğümü olarak oluşturulur.  
  
 ![Ağaç yapısı Korunan varlık başvuruları için](../../../../docs/standard/data/xml/media/xmlentityref-notexpanded-nodes.gif "xmlentityref_notexpanded_nodes")  
Korunur varlık başvuruları için ağaç yapısı  
  
 Alt düğümleri **XmlEntityReference** düğümleri oluşturulan tüm alt kopyalarıdır **XmlEntity** varlık bildirimi karşılaştığında düğümü.  
  
> [!NOTE]
>  Kopyalanan düğümleri **XmlEntity** olmayan her zaman tam kopyaları kez varlık başvurusu düğümünde yerleştirilir. Varlık referans düğümün kapsamında bulunan ad alanları olabilir ve son yapılandırma alt düğümlerin etkiler.  
  
 Varsayılan olarak, genel varlıklar ister `&abc;` korunur ve **XmlEntityReference** her zaman oluşturulan düğümler.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
