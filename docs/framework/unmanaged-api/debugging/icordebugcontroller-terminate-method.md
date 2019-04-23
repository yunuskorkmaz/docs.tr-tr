---
title: ICorDebugController::Terminate Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugController.Terminate
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Terminate
helpviewer_keywords:
- Terminate method, ICorDebugController interface [.NET Framework debugging]
- ICorDebugController::Terminate method [.NET Framework debugging]
ms.assetid: 4275af0c-b5a7-4e4c-97c9-7e41f36b2dd8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c4c8dd8795fc3699176490ea0bb9b2e999038afb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59124884"
---
# <a name="icordebugcontrollerterminate-method"></a>ICorDebugController::Terminate Yöntemi
Belirtilen çıkış kodu ile işlemi sonlandırır.  
  
> [!NOTE]
>  Bu yöntem Win32 için bir sarmalayıcı olan `TerminateProcess` işlevi. Bu nedenle, `Terminate` aynı çıkış kodunu kullanır biçimi Win32 `TerminateProcess` işlevi kullanır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT Terminate (  
    [in] UINT exitCode  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `exitCode`  
 [in] Çıkış kodu sayısal bir değer. Geçerli bir sayısal değerler Winbase.h içinde tanımlanır.  
  
## <a name="remarks"></a>Açıklamalar  
 İşlemin ne zaman durdurulursa `Terminate` olan adlı işlemi kullanarak devam [Icordebugcontroller::continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) yöntemi hata ayıklayıcı sonlandırma onayı alması [ Icordebugmanagedcallback::exitprocess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) veya [Icordebugmanagedcallback::exitappdomain](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitappdomain-method.md) geri çağırma.  
  
> [!NOTE]
>  Bu yöntem, bir uygulama etki alanına göre uygulanmadı. Diğer bir deyişle, bu anda uygulanmadı <xref:System.AppDomain> düzeyi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
