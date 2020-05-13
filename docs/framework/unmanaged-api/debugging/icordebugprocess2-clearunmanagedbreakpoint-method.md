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
ms.openlocfilehash: 2b228383c3b393fe43f60d39e59cca37af36233f
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212500"
---
# <a name="icordebugprocess2clearunmanagedbreakpoint-method"></a>ICorDebugProcess2::ClearUnmanagedBreakpoint Yöntemi
Belirtilen adresteki daha önce ayarlanan bir kesme noktasını kaldırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT ClearUnmanagedBreakpoint (  
    [in] CORDB_ADDRESS   address  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `address`  
 'ndaki `CORDB_ADDRESS`Kesme noktasının ayarlandığı adresi belirten bir değer.  
  
## <a name="remarks"></a>Açıklamalar  
 Belirtilen kesme noktası daha önce [ICorDebugProcess2:: SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md)için daha önceki bir çağrı tarafından ayarlanmıştır.  
  
 `ClearUnmanagedBreakpoint`Yöntemi, hata ayıklamakta olan işlem çalışırken çağrılabilir.  
  
 `ClearUnmanagedBreakpoint`Hata ayıklayıcı yalnızca yönetilen modda eklenmişse veya belirtilen adreste hiçbir kesme noktası yoksa, yöntemi bir hata kodu döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
