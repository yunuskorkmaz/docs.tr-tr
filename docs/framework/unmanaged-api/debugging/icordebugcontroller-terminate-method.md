---
title: "ICorDebugController::Terminate Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2e7647df7a67d8357e72f8f41b0b3f586675aaac
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcontrollerterminate-method"></a>ICorDebugController::Terminate Yöntemi
Belirtilen çıkış kodu ile işlemi sonlandırır.  
  
> [!NOTE]
>  Win32 için sarmalayıcı bu yöntemdir `TerminateProcess` işlevi. Bu nedenle, `Terminate` aynı çıkış kodunu kullanır biçimi Win32 `TerminateProcess` işlevini kullanır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT Terminate (  
    [in] UINT exitCode  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `exitCode`  
 [in] Çıkış kodu sayısal bir değer. Geçerli sayısal değerleri Winbase.h tanımlanır.  
  
## <a name="remarks"></a>Açıklamalar  
 İşlem zaman durdurulursa `Terminate` olduğu adlı işlemi kullanarak devam [Icordebugcontroller::continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) yöntemi hata ayıklayıcı sonlandırma onayı alması [ Icordebugmanagedcallback::exitprocess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) veya [Icordebugmanagedcallback::exitappdomain](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitappdomain-method.md) geri çağırma.  
  
> [!NOTE]
>  Bu yöntem, bir uygulama etki alanı tarafından uygulanmadı. Diğer bir deyişle, bu anda uygulanmadı <xref:System.AppDomain> düzeyi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 
