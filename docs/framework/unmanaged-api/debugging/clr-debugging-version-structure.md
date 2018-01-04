---
title: "CLR_DEBUGGING_VERSION Yapısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CLR_DEBUGGING_VERSION
api_location: mscordbi.dll
api_type: COM
f1_keywords: CLR_DEBUGGING_VERSION
helpviewer_keywords: CLR_DEBUGGING_VERSION structure [.NET Framework debugging]
ms.assetid: 4d821186-3ddf-405a-ac44-d79438a9f7f3
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 092024f3f4e6fc1bc923ae2a299c5d9c21f1b1b8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="clrdebuggingversion-structure"></a>CLR_DEBUGGING_VERSION Yapısı
Hata ayıklama amacıyla ortak dil çalışma zamanı (CLR) ürün sürümü tanımlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Typedef struct _CLR_DEBUGGING_VERSION  
{  
WORD wStructVersion;  
WORD wMajor;   
WORD wMinor;  
WORD wBuild;  
WORD wRevision;  
}  CLR_DEBUGGING_VERSION;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`wStructVersion`|Yapı sürüm numarası|  
|`wMajor`|Ana sürüm numarası.|  
|`wMinor`|İkincil sürüm numarası.|  
|`wBuild`|Yapı numarası.|  
|`wRevision`|Düzeltme numarası.|  
  
## <a name="remarks"></a>Açıklamalar  
 `CLR_DEBUGGING_VERSION` Yapısı aynıdır cor_versıon yapısı ancak, `CLR_DEBUGGING_VERSION` yapısı bir ek yapı sürümü alanı sağlar (`wStructVersion`). Şu anda, bu alan sıfır olarak ayarlanması gerekir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklama Yapıları](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
