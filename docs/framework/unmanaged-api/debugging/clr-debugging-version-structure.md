---
title: CLR_DEBUGGING_VERSION Yapısı
ms.date: 03/30/2017
api_name:
- CLR_DEBUGGING_VERSION
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CLR_DEBUGGING_VERSION
helpviewer_keywords:
- CLR_DEBUGGING_VERSION structure [.NET Framework debugging]
ms.assetid: 4d821186-3ddf-405a-ac44-d79438a9f7f3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 87f938a7119abe4a88da65bd779a5f4a02499516
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61996352"
---
# <a name="clrdebuggingversion-structure"></a>CLR_DEBUGGING_VERSION Yapısı
Ürün sürümü, hata ayıklama amacıyla ortak dil çalışma zamanı (CLR) tanımlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef struct _CLR_DEBUGGING_VERSION  
{  
    WORD wStructVersion;
    WORD wMajor;
    WORD wMinor;
    WORD wBuild;
    WORD wRevision;
} CLR_DEBUGGING_VERSION;
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
 `CLR_DEBUGGING_VERSION` Yapısıdır cor_versıon yapısı ile aynı ancak, `CLR_DEBUGGING_VERSION` yapısı bir ek yapı sürümü alanı sağlar (`wStructVersion`). Şu anda, bu alan, sıfır olarak ayarlanmalıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Yapıları](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
