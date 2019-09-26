---
title: COR_HEAPINFO Yapısı
ms.date: 03/30/2017
api_name:
- COR_HEAPINFO
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_HEAPINFO
helpviewer_keywords:
- COR_HEAPINFO structure [.NET Framework debugging]
ms.assetid: bfb2cd39-3e0b-4d51-ba0c-f009755c1456
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f7b340a73aa9eaebca9c0d78563ae298557039b8
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274187"
---
# <a name="cor_heapinfo-structure"></a>COR_HEAPINFO Yapısı
Çöp toplama yığını hakkında, numaralandırılabilir olup olmadığı dahil genel bilgiler sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef struct _COR_HEAPINFO {  
    BOOL areGCStructuresValid;   
    DWORD pointerSize;   
    DWORD numHeaps;  
    BOOL concurrent;   
    CorDebugGCType gcType;   
} COR_HEAPINFO;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`areGCStructuresValid`|`true`çöp toplama yapıları geçerliyse ve yığın Numaralandırılabilir. Aksi takdirde `false`,.|  
|`pointerSize`|Hedef mimarideki işaretçilerin bayt cinsinden boyutu.|  
|`numHeaps`|İşlemdeki mantıksal çöp toplama yığınlarını sayısı.|  
|`concurrent`|`TRUE`eş zamanlı (arka plan) çöp toplama etkinse; Aksi takdirde `FALSE`,.|  
|`gcType`|Çöp toplayıcısının bir iş istasyonunda veya sunucuda çalışıp çalışmadığını belirten, [Cordebugggctype](cordebuggctype-enumeration.md) numaralandırmasının bir üyesi.|  
  
## <a name="remarks"></a>Açıklamalar  
 `COR_HEAPINFO` [ICorDebugProcess5:: GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) yöntemi çağırarak yapının bir örneği döndürülür.  
  
 Çöp toplama yığınında nesneleri numaralandırmadan önce, yığının sıralanabilir bir durumda olduğundan emin `areGCStructuresValid` olmak için alanı her zaman denetlemeniz gerekir. Daha fazla bilgi için bkz. [ICorDebugProcess5:: GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) yöntemi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi** CorDebug. IDL, CorDebug. h  
  
 **Kitaplığı** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Yapıları](debugging-structures.md)
- [Hata Ayıklama](index.md)
