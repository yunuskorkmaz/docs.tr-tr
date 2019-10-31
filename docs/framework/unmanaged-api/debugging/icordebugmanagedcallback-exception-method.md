---
title: ICorDebugManagedCallback::Exception Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.Exception
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::Exception
helpviewer_keywords:
- Exception method, ICorDebugManagedCallback interface [.NET Framework debugging]
- ICorDebugManagedCallback::Exception method [.NET Framework debugging]
ms.assetid: ab18a509-dff3-4930-b585-bd15e0414176
topic_type:
- apiref
ms.openlocfilehash: af2dab65629093401219f1016538b912bee4d067
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130819"
---
# <a name="icordebugmanagedcallbackexception-method"></a>ICorDebugManagedCallback::Exception Yöntemi
Hata ayıklayıcıya yönetilen koddan bir özel durum gerçekleştiğini bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT Exception (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] BOOL                unhandled  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pAppDomain`  
 'ndaki Özel durumun oluşturulduğu uygulama etki alanını temsil eden ICorDebugAppDomain nesnesine yönelik bir işaretçi.  
  
 `pThread`  
 'ndaki Özel durumun oluşturulduğu iş parçacığını temsil eden ICorDebugThread nesnesine yönelik bir işaretçi.  
  
 `unhandled`  
 'ndaki Bu değer `false`, özel durum henüz uygulama tarafından işlenmemiştir; Aksi takdirde, özel durum işlenmemiş olur ve işlemi sonlandırır.  
  
## <a name="remarks"></a>Açıklamalar  
 Belirli özel durum iş parçacığı nesnesinden alınabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugManagedCallback Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
