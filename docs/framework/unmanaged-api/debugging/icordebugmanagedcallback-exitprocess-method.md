---
description: ': ICorDebugManagedCallback:: ExitProcess yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 3418931b8397edefcb801986275c35b28e00072d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790964"
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

 Bir olaydan devam edemezsiniz `ExitProcess` . Bu olay, işlem durdurulmuş olarak göründüğü sırada diğer olaylara zaman uyumsuz olarak harekete çıkabilir. Bu durum, genellikle bazı harici bir zorlamalı nedeniyle işlem durdurulduğunda sonlandırıldığında meydana gelir.  
  
 Ortak dil çalışma zamanı (CLR) zaten yönetilen bir geri çağırma gönderiyor ise bu olay, geri çağırma geri dönene kadar gecikecek.  
  
 `ExitProcess`Olay, kapatılırken çağrılmanın garanti edilmesi gereken tek çıkış/kaldırma olayıdır.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugManagedCallback Arabirimi](icordebugmanagedcallback-interface.md)
