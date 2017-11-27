---
title: 1035 - RuntimeTransactionSet
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03b37de9-778c-4beb-b0e3-de73ece6088e
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c3fcd93dbc30b20f7822a54babde8277e32d8335
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="1035---runtimetransactionset"></a>1035 - RuntimeTransactionSet
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimlik|1035|  
|Anahtar Sözcükler|WFRuntime|  
|Düzey|Ayrıntılı|  
|Kanal|Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama|  
  
## <a name="description"></a>Açıklama  
 Etkinlik çalışma zamanı işlem ayarlanmış gösterir.  
  
## <a name="message"></a>İleti  
 Çalışma zamanı işlem '%1', DisplayName etkinliği tarafından ayarlandı: '%2', örnek kimliği: '%3'.  Etkinlik '%4', DisplayName yalıtılmış yürütme: '%5', örnek kimliği: '%6'.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|Etkinlik|xs: String|Etkinlik türü adı.|  
|Görünen adı|xs: String|Etkinliğin görünen adı.|  
|örnek kimliği|xs: String|Etkinlik örnek kimliği.|  
|IsolatedActivity|xs: String|İşlem için yalıtılmış etkinlik türü adı.|  
|IsolatedActivityDisplayName|xs: String|İşlem için yalıtılmış etkinliğin görünen adı.|  
|IsolatedActivityInstanceId|xs: String|İşlem için yalıtılmış etkinlik örnek kimliği.|  
|AppDomain|xs: String|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
