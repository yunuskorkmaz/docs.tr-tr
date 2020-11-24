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
ms.openlocfilehash: 460aeeca9d62ce91a11a24d774c8e681ed4f00ca
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679812"
---
# <a name="icordebugcontrollerterminate-method"></a>ICorDebugController::Terminate Yöntemi

Belirtilen çıkış koduyla işlemi sonlandırır.  
  
> [!NOTE]
> Bu yöntem, Win32 işlevi için bir sarmalayıcıdır `TerminateProcess` . Bu nedenle, `Terminate` çıkış kodunu Win32 `TerminateProcess` işlevinin kullandığı şekilde kullanır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT Terminate (  
    [in] UINT exitCode  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `exitCode`  
 'ndaki Çıkış kodu olan sayısal bir değer. Geçerli sayısal değerler Winbase. h içinde tanımlanır.  
  
## <a name="remarks"></a>Açıklamalar  

 İşlem `Terminate` çağrıldığında, hata ayıklayıcının [ICorDebugManagedCallback:: ExitProcess](icordebugmanagedcallback-exitprocess-method.md) veya [ICorDebugManagedCallback:: exetppdomain](icordebugmanagedcallback-exitappdomain-method.md) geri çağırması aracılığıyla sonlandırma onayını alabilmesi için [ICorDebugController:: Continue](icordebugcontroller-continue-method.md) yöntemi kullanılarak işlem devam edilmelidir.  
  
> [!NOTE]
> Bu yöntem bir uygulama etki alanı tarafından uygulanmıyor. Diğer bir deyişle, <xref:System.AppDomain> düzeyinde uygulanmaz.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
