---
title: COR_ACTIVE_FUNCTION Yapısı
ms.date: 03/30/2017
api_name:
- COR_ACTIVE_FUNCTION
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_ACTIVE_FUNCTION
helpviewer_keywords:
- COR_ACTIVE_FUNCTION structure [.NET Framework debugging]
ms.assetid: ed86185f-2152-459c-961f-10c06d62e83f
topic_type:
- apiref
ms.openlocfilehash: cbc272070e9eb6810b34ec1f3fdc9e944c624cd3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132378"
---
# <a name="cor_active_function-structure"></a>COR_ACTIVE_FUNCTION Yapısı
Şu anda bir iş parçacığının çerçevelerinde etkin olan işlevlerle ilgili bilgiler içerir. Bu yapı, [ICorDebugThread2:: GetActiveFunctions](icordebugthread2-getactivefunctions-method.md) yöntemi tarafından kullanılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef struct  _COR_ACTIVE_FUNCTION {  
    ICorDebugAppDomain   *pAppDomain;  
    ICorDebugModule      *pModule;  
    ICorDebugFunction2   *pFunction;  
    ULONG32              ilOffset;  
    ULONG32              flags;  
} COR_ACTIVE_FUNCTION;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`pAppDomain`|`ilOffset` alanının uygulama etki alanı sahibine yönelik işaretçi.|  
|`pModule`|`ilOffset` alanının modül sahibine yönelik işaretçi.|  
|`pFunction`|`ilOffset` alanının işlev sahibine yönelik işaretçi.|  
|`ilOffset`|Çerçevenin Microsoft ara dili (MSIL) kayması.|  
|`flags`|Gelecekteki genişletilebilirlik için ayrılmıştır.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Yapıları](debugging-structures.md)
- [Hata Ayıklama](index.md)
