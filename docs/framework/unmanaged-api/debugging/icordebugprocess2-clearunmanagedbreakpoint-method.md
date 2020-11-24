---
title: ICorDebugProcess2::ClearUnmanagedBreakpoint Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.ClearUnmanagedBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::ClearUnmanagedBreakpoint
helpviewer_keywords:
- ClearUnmanagedBreakpoint method [.NET Framework debugging]
- ICorDebugProcess2::ClearUnmanagedBreakpoint method [.NET Framework debugging]
ms.assetid: 12ed0fff-7f0e-4d7a-bb70-b3376371f36c
topic_type:
- apiref
ms.openlocfilehash: a713fd006f1e9ad8fe7109651c2cda5025da3566
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673949"
---
# <a name="icordebugprocess2clearunmanagedbreakpoint-method"></a>ICorDebugProcess2::ClearUnmanagedBreakpoint Yöntemi

Belirtilen adresteki daha önce ayarlanan bir kesme noktasını kaldırır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT ClearUnmanagedBreakpoint (  
    [in] CORDB_ADDRESS   address  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `address`  
 'ndaki `CORDB_ADDRESS` Kesme noktasının ayarlandığı adresi belirten bir değer.  
  
## <a name="remarks"></a>Açıklamalar  

 Belirtilen kesme noktası daha önce [ICorDebugProcess2:: SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md)için daha önceki bir çağrı tarafından ayarlanmıştır.  
  
 `ClearUnmanagedBreakpoint`Yöntemi, hata ayıklamakta olan işlem çalışırken çağrılabilir.  
  
 `ClearUnmanagedBreakpoint`Hata ayıklayıcı yalnızca yönetilen modda eklenmişse veya belirtilen adreste hiçbir kesme noktası yoksa, yöntemi bir hata kodu döndürür.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
