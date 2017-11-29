---
title: 1030 - StartFaultWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e1601fb9-0bc6-4dbe-816f-f24914063d34
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b25dbd5ced96b8e9ca3ef51e4de841a6238d2cbc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="1030---startfaultworkitem"></a>1030 - StartFaultWorkItem
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimlik|1030|  
|Anahtar Sözcükler|WFRuntime|  
|Düzey|Ayrıntılı|  
|Kanal|Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama|  
  
## <a name="description"></a>Açıklama  
 Bir FaultWorkItem yürütme başlanacağını gösterir.  
  
## <a name="message"></a>İleti  
 '%1', DisplayName etkinliğinin FaultWorkItem yürütülmesi başlatılıyor: '%2', örnek kimliği: '%3'.  Özel durum '%4', DisplayName etkinliğinden yayılır: '%5', örnek kimliği: '%6'.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|FaultActivity|xs: String|Hataya etkinlik türü adı.|  
|FaultActivityDisplayName|xs: String|Hataya etkinlik görünen adı.|  
|FaultActivityInstanceId|xs: String|Hataya etkinlik örnek kimliği.|  
|ExceptionActivity|xs: String|Özel durum oluşturdu etkinlik türü adı.|  
|ExceptionActivityDisplayName|xs: String|Özel durum oluşturdu etkinliğin görünen adı.|  
|ExceptionActivityInstanceId|xs: String|Özel durum oluşturdu etkinlik örnek kimliği.|  
|Özel Durum|xs: String|Özel durum için özel durum ayrıntıları|  
|AppDomain|xs: String|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
