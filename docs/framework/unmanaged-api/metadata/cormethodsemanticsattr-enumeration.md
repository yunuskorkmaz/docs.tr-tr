---
title: "CorMethodSemanticsAttr Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorMethodSemanticsAttr
api_location: mscoree.dll
api_type: COM
f1_keywords: CorMethodSemanticsAttr
helpviewer_keywords: CorMethodSemanticsAttr enumeration [.NET Framework metadata]
ms.assetid: ca2af325-eb9d-4a91-90e4-267e45b98611
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c6dca24aad06b1c07c86cb716f4be344c8458471
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="cormethodsemanticsattr-enumeration"></a>CorMethodSemanticsAttr Numaralandırması
Bir yöntem ve bir ilişkili özelliğin veya olay arasındaki ilişkiyi tanımlayan değerler içeriyor.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef enum CorMethodSemanticsAttr {  
  
    msSetter    =   0x0001,  
    msGetter    =   0x0002,  
    msOther     =   0x0004,  
    msAddOn     =   0x0008,  
    msRemoveOn  =   0x0010,  
    msFire      =   0x0020,  
  
} CorMethodSemanticsAttr;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`msSetter`|Yöntemi gerektiğini belirten bir `set` bir özellik için erişimcisi.|  
|`msGetter`|Yöntemi gerektiğini belirten bir `get` bir özellik için erişimcisi.|  
|`msOther`|Yöntemin bir özellik veya burada tanımlanan dışında bir olay için bir ilişki olduğunu belirtir.|  
|`msAddOn`|Yöntemi, bir olay işleyicisi yöntemlerini ekler belirtir.|  
|`msRemoveOn`|Yöntemi, bir olay işleyicisi yöntemlerini kaldırır belirtir.|  
|`msFire`|Yöntemin bir olay başlatır belirtir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorHdr.h  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Meta veri numaralandırmalar](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
