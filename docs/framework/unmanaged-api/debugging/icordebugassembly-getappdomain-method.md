---
title: ICorDebugAssembly::GetAppDomain Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly.GetAppDomain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly::GetAppDomain
helpviewer_keywords:
- ICorDebugAssembly::GetAppDomain method [.NET Framework debugging]
- GetAppDomain method, ICorDebugAssembly interface [.NET Framework debugging]
ms.assetid: 14e18510-23ac-4cba-9f96-c86147a2df9d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4fced656168952c1064de213405147baf7856b2c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67737349"
---
# <a name="icordebugassemblygetappdomain-method"></a>ICorDebugAssembly::GetAppDomain Metodu
Bu içeren uygulama etki alanı için bir arabirim işaretçisi alır `ICorDebugAssembly` örneği.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetAppDomain (  
    [out] ICorDebugAppDomain  **ppAppDomain  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ppAppDomain`  
 [out] Uygulama etki alanını temsil eden bir Icordebugappdomain arabirimi adresi için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu derleme sistemi derleme ise `GetAppDomain` null döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
