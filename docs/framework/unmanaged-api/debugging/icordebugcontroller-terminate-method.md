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
ms.openlocfilehash: ee1c30809567097e67b6b1e40f5534429d748abd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964363"
---
# <a name="icordebugcontrollerterminate-method"></a>ICorDebugController::Terminate Yöntemi
Belirtilen çıkış koduyla işlemi sonlandırır.  
  
> [!NOTE]
> Bu yöntem, Win32 `TerminateProcess` işlevi için bir sarmalayıcıdır. Bu nedenle `Terminate` , çıkış kodunu Win32 `TerminateProcess` işlevinin kullandığı şekilde kullanır.  
  
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
 İşlem `Terminate` çağrıldığında, işlem hata ayıklayıcının ICorDebugManagedCallback aracılığıyla sonlandırmanın onayını alabilmesi için [ICorDebugController:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) yöntemi kullanılarak devam edilmelidir [:: ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) veya [ICorDebugManagedCallback:: Exbir ppdomain](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitappdomain-method.md) geri çağırma.  
  
> [!NOTE]
> Bu yöntem bir uygulama etki alanı tarafından uygulanmıyor. Diğer bir deyişle, <xref:System.AppDomain> düzeyinde uygulanmaz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi** CorDebug. IDL, CorDebug. h  
  
 **Kitaplığı** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
