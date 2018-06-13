---
title: ICorDebugModule2::ResolveAssembly Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.ResolveAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::ResolveAssembly
helpviewer_keywords:
- ICorDebugModule2::ResolveAssembly method [.NET Framework debugging]
- ResolveAssembly method [.NET Framework debugging]
ms.assetid: ddf9085c-7161-44bd-9609-cd2732b9009f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 44a6596807b98e6c8b8624b5df18f78dbf8d0711
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417784"
---
# <a name="icordebugmodule2resolveassembly-method"></a>ICorDebugModule2::ResolveAssembly Yöntemi
Belirtilen meta veri simgesi tarafından başvurulan derleme çözümler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT ResolveAssembly (  
    [in]  mdToken             tkAssemblyRef,  
    [out] ICorDebugAssembly   **ppAssembly  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `tkAsemblyRef`  
 [in] Bir `mdToken` bütünleştirilmiş koduna başvuruyor değeri.  
  
 `ppAssembly`  
 [out] Bir işaretçi adresine Icordebugassembly nesnenin derleme temsil eder.  
  
## <a name="remarks"></a>Açıklamalar  
 Derleme zaten ne zaman yüklenmezse `ResolveAssembly` çağrılır, HRESULT CORDBG_E_CANNOT_RESOLVE_ASSEMBLY değeri döndürülür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
