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
ms.openlocfilehash: fb8cfb2d1c5902ecd0d5858ef21ba48b65b12506
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125329"
---
# <a name="icordebugcontrollerterminate-method"></a>ICorDebugController::Terminate Yöntemi
Belirtilen çıkış koduyla işlemi sonlandırır.  
  
> [!NOTE]
> Bu yöntem, Win32 `TerminateProcess` işlevi için bir sarmalayıcıdır. Bu nedenle `Terminate`, Win32 `TerminateProcess` işlevi tarafından kullanılan aynı şekilde çıkış kodunu kullanır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT Terminate (  
    [in] UINT exitCode  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `exitCode`  
 'ndaki Çıkış kodu olan sayısal bir değer. Geçerli sayısal değerler Winbase. h içinde tanımlanır.  
  
## <a name="remarks"></a>Açıklamalar  
 `Terminate` çağrıldığında işlem durdurulmuşsa, hata ayıklayıcının ICorDebugManagedCallback aracılığıyla sonlandırmanın onayını alabilmesi için [ICorDebugController:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) yöntemi kullanılarak devam edilmelidir [:: ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) veya [ICorDebugManagedCallback:: Exbir ppdomain](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitappdomain-method.md) geri çağırma.  
  
> [!NOTE]
> Bu yöntem bir uygulama etki alanı tarafından uygulanmıyor. Diğer bir deyişle, <xref:System.AppDomain> düzeyinde uygulanmaz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
