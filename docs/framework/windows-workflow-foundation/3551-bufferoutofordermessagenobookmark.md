---
title: 3551 - BufferOutOfOrderMessageNoBookmark
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7930d6c4-c843-4a83-933a-cecd71b80d1e
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9a380def22c270a3fafe118a426609a93862c447
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="3551---bufferoutofordermessagenobookmark"></a>3551 - BufferOutOfOrderMessageNoBookmark
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimlik|3551|  
|Anahtar Sözcükler|WFServices|  
|Düzey|Bilgiler|  
|Kanal|Microsoft Windows uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Açıklama  
 Yer işareti sürdürme başarısız oldu gösterir. Arabellekli alma işlemi hizmet örneği belirli bu işlemi hazır olduğunda yeniden denenecek.  
  
## <a name="message"></a>İleti  
 Hizmet örneği '%1' işlemi '%2', şu anda gerçekleştirilemiyor. Hizmet örneği belirli bu işlemi için hazır olduğunda, başka bir deneme yapılır.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|OperationName|xs: String|İşlemin adı.|  
|Serviceınstanceıd|xs: String|Hizmet örneği kimliği.|  
|AppDomain|xs: String|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
