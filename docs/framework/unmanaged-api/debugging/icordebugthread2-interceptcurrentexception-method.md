---
title: ICorDebugThread2::InterceptCurrentException Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugThread2.InterceptCurrentException
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::InterceptCurrentException
helpviewer_keywords:
- InterceptCurrentException method [.NET Framework debugging]
- ICorDebugThread2::InterceptCurrentException method [.NET Framework debugging]
ms.assetid: 536d2357-1b97-49e0-a10c-c860aed74e6e
topic_type:
- apiref
ms.openlocfilehash: 96e3a90bcb7700915bfd3618d7bae40c0ff64a75
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678603"
---
# <a name="icordebugthread2interceptcurrentexception-method"></a>ICorDebugThread2::InterceptCurrentException Yöntemi

Bir hata ayıklayıcının bu iş parçacığında geçerli özel durumu kesmesini sağlar.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT InterceptCurrentException (  
    [in] ICorDebugFrame  *pFrame  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pFrame`  
 'ndaki Etkin yığın çerçevesini temsil eden bir ICorDebugFrame işaretçisi.  
  
## <a name="remarks"></a>Açıklamalar  

 `InterceptCurrentException`Yöntem bir özel durum geri çağırması ([ICorDebugManagedCallback:: Exception](icordebugmanagedcallback-exception-method.md) veya [ICorDebugManagedCallback2:: Exception](icordebugmanagedcallback2-exception-method.md)) Ile ilişkili [ICorDebugController:: Continue](icordebugcontroller-continue-method.md)öğesine yapılan çağrı arasında çağrılabilir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
