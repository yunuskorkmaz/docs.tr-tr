---
title: 1022 - StartBookmarkWorkItem
ms.date: 03/30/2017
ms.assetid: 4415fbdb-0329-4019-803f-aea66e75f3da
ms.openlocfilehash: 93d906b32b51effaa709da6763f535708cd6f821
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924728"
---
# <a name="1022---startbookmarkworkitem"></a>1022 - StartBookmarkWorkItem
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimlik|1022|  
|anahtar sözcükler|WFRuntime|  
|Düzey|Ayrıntılı|  
|Kanal|Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama|  
  
## <a name="description"></a>Açıklama  
 Bir BookmarkWorkItem yürütme başlanacağını gösterir.  
  
## <a name="message"></a>İleti  
 '%1', DisplayName etkinliği için bir BookmarkWorkItem yürütülmesi başlatılıyor: '%2', InstanceId: '%3'.  YerİşaretiAdı: %4, BookmarkScope: %5.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|Etkinlik|xs:string|Etkinlik türü adı.|  
|displayName|xs:string|Etkinliğin görünen adı.|  
|InstanceId|xs:string|Etkinlik örneği kimliği.|  
|YerİşaretiAdı|xs:string|Yer işaretinin adı.|  
|BookmarkScope|xs:string|Yer işareti kapsam.|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
