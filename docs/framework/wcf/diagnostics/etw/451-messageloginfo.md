---
title: 451 - MessageLogInfo
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 485b4b29-dc21-4a35-93f8-5f4726d6aa5a
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 515c95883b1c232f91363a65015c1f90800a7d12
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="451---messageloginfo"></a>451 - MessageLogInfo
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimlik|451|  
|Anahtar Sözcükler|Sorun giderme, WCFMessageLogging|  
|Düzey|Bilgiler|  
|Kanal|Microsoft Windows uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Açıklama  
 Bu olay iletisi günlük bilgileri gönderildiğinde yayınlanır.  
  
## <a name="message"></a>İleti  
 %1  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|Veri1|`xs:string`||  
|AppDomain|`xs:string`|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
