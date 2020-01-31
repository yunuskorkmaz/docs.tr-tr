---
title: ICorDebugManagedCallback::ExitProcess Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.ExitProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::ExitProcess
helpviewer_keywords:
- ExitProcess method, ICorDebugManagedCallback interface [.NET Framework debugging]
- ICorDebugManagedCallback::ExitProcess method [.NET Framework debugging]
ms.assetid: 63a7d47a-0d54-4e29-9767-9f09feaa38b7
topic_type:
- apiref
ms.openlocfilehash: 4380b8a3803e164aab7318821a9dbde32ecc3a0b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76781750"
---
# <a name="icordebugmanagedcallbackexitprocess-method"></a>ICorDebugManagedCallback::ExitProcess Yöntemi
Hata ayıklayıcıya bir işlemin çıkış olduğunu bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT ExitProcess (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pProcess`  
 'ndaki İşlemi temsil eden ICorDebugProcess nesnesine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 `ExitProcess` olayından devam edemezsiniz. Bu olay, işlem durdurulmuş olarak göründüğü sırada diğer olaylara zaman uyumsuz olarak harekete çıkabilir. Bu durum, genellikle bazı harici bir zorlamalı nedeniyle işlem durdurulduğunda sonlandırıldığında meydana gelir.  
  
 Ortak dil çalışma zamanı (CLR) zaten yönetilen bir geri çağırma gönderiyor ise bu olay, geri çağırma geri dönene kadar gecikecek.  
  
 `ExitProcess` olay, kapatılırken çağrılmanın garanti edilmesi gereken tek çıkış/kaldırma olayıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugManagedCallback Arabirimi](icordebugmanagedcallback-interface.md)
