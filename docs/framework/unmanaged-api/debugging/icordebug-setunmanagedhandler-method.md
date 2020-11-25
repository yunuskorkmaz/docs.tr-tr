---
title: ICorDebug::SetUnmanagedHandler Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebug.SetUnmanagedHandler
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::SetUnmanagerHandler
helpviewer_keywords:
- SetUnmanagedHandler method [.NET Framework debugging]
- ICorDebug::SetUnmanagedHandler method [.NET Framework debugging]
ms.assetid: 6b546be4-f86d-4536-8cfc-1d08e5066eb6
topic_type:
- apiref
ms.openlocfilehash: 0bce14a6853c872d27057b9fffc32b54c59abf13
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723395"
---
# <a name="icordebugsetunmanagedhandler-method"></a>ICorDebug::SetUnmanagedHandler Yöntemi

Yönetilmeyen olaylar için olay işleyicisi nesnesini belirtir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT SetUnmanagedHandler (  
    [in] ICorDebugUnmanagedCallback  *pCallback  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pCallback`  
 'ndaki Yönetilmeyen olaylar için olay işleyicisini temsil eden [ICorDebugUnmanagedCallback](icordebugunmanagedcallback-interface.md) nesnesine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  

 Yönetilmeyen olaylar için olay işleyicisi nesnesi [ICorDebug](icordebug-initialize-method.md) :: Initialize ve ICorDebug: [: CreateProcess](icordebug-createprocess-method.md) veya [ICorDebug::D ebugactiveprocess](icordebug-debugactiveprocess-method.md)çağrılarına yapılan çağrıdan sonra ayarlanmalıdır. Ancak, eski amaçlar için, ilk yerel hata ayıklama olayı oluşturuluncaya kadar yönetilmeyen olaylar için olay işleyicisi nesnesini ayarlamanız gerekmez. Özellikle `ICorDebug::CreateProcess` CREATE_SUSPENDED bayrağını ayarlandıysa, ana iş parçacığı sürdürülene kadar yerel hata ayıklama olayları dağıtılamaz.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebug Arabirimi](icordebug-interface.md)
