---
title: 1020 - CreateBookmark
ms.date: 03/30/2017
ms.assetid: 4bee948d-816f-4803-85cc-3883b5e23d10
ms.openlocfilehash: 2a382a2f12f4800cd70286a553af253e2af64c9b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924754"
---
# <a name="1020---createbookmark"></a>1020 - CreateBookmark
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimlik|1020|  
|anahtar sözcükler|WFRuntime|  
|Düzey|Ayrıntılı|  
|Kanal|Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama|  
  
## <a name="description"></a>Açıklama  
 Bir etkinlik için bir yer işareti oluşturulduktan gösterir.  
  
## <a name="message"></a>İleti  
 '%1', DisplayName etkinliği için yer imi oluşturuldu: '%2', InstanceId: '%3'.  YerİşaretiAdı: %4, BookmarkScope: %5.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|Etkinlik|xs:string|Etkinlik türü adı.|  
|displayName|xs:string|Etkinliğin görünen adı.|  
|InstanceId|xs:string|Etkinlik örneği kimliği.|  
|YerİşaretiAdı|xs:string|Yer işaretinin adı.|  
|BookmarkScope|xs:string|Yer işareti kapsam.|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
