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
ms.openlocfilehash: 37659262695b63a6dd6390c62c4bb7e04fdadca4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179303"
---
# <a name="cor_heapinfo-structure"></a>COR_HEAPINFO Yapısı
Çöp toplama yığını hakkında, sayısala uygun olup olmadığı da dahil olmak üzere genel bilgiler sağlar.  
  
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
|`areGCStructuresValid`|`true`çöp toplama yapıları geçerliyse ve yığın numaralandırılabilirse; aksi `false`takdirde, .|  
|`pointerSize`|Hedef mimarideki işaretçilerin baytboyutu.|  
|`numHeaps`|İşlemdeki mantıksal çöp toplama yığınlarının sayısı.|  
|`concurrent`|`TRUE`eşzamanlı (arka plan) çöp toplama etkinse; aksi `FALSE`takdirde, .|  
|`gcType`|Çöp toplayıcısının bir iş istasyonunda mı yoksa sunucuda mı çalıştığını gösteren [CorDebugGCType](cordebuggctype-enumeration.md) numaralandırmasının bir üyesi.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yapının `COR_HEAPINFO` bir örneği [ICorDebugProcess5::GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) yöntemini arayarak döndürülür.  
  
 Nesneleri çöp toplama yığınına kaydettirmeden önce, yığının `areGCStructuresValid` sayısal durumuna geldiğinden emin olmak için her zaman alanı denetlemeniz gerekir. Daha fazla bilgi için [ICorDebugProcess5::GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) yöntemine bakın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üstbilgi:** CorDebug.idl, CorDebug.h  
  
 **Kütüphane:** CorGuids.lib  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Yapıları](debugging-structures.md)
- [Hata ayıklama](index.md)
