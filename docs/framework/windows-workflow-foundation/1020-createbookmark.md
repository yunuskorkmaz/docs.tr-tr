---
title: 1020 - CreateBookmark
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4bee948d-816f-4803-85cc-3883b5e23d10
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d0584c6eeaf0e08e92ad94e01e1fca765616440f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="1020---createbookmark"></a>1020 - CreateBookmark
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimlik|1020|  
|Anahtar Sözcükler|WFRuntime|  
|Düzey|Ayrıntılı|  
|Kanal|Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama|  
  
## <a name="description"></a>Açıklama  
 Yer işareti bir etkinlik için oluşturulan gösterir.  
  
## <a name="message"></a>İleti  
 '%1', DisplayName etkinliği için bir yer işareti oluşturuldu: '%2', örnek kimliği: '%3'.  YerİşaretiAdı: %4, BookmarkScope: %5.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|Etkinlik|xs: String|Etkinlik türü adı.|  
|Görünen adı|xs: String|Etkinliğin görünen adı.|  
|örnek kimliği|xs: String|Etkinlik örnek kimliği.|  
|YerİşaretiAdı|xs: String|Yer işaretinin adı.|  
|BookmarkScope|xs: String|Yer işareti kapsamı.|  
|AppDomain|xs: String|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
