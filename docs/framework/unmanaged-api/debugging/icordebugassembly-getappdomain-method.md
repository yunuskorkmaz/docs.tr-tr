---
description: ': ICorDebugAssembly:: GetAppDomain metodu hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: f67b2a211b080843e2bd7b8820a5bf54dae638e3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99712109"
---
# <a name="icordebugassemblygetappdomain-method"></a>ICorDebugAssembly::GetAppDomain Metodu

Bu örneği içeren uygulama etki alanına bir arabirim işaretçisi alır `ICorDebugAssembly` .  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetAppDomain (  
    [out] ICorDebugAppDomain  **ppAppDomain  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `ppAppDomain`  
 dışı Uygulama etki alanını temsil eden ICorDebugAppDomain arabiriminin adresine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  

 Bu derleme sistem bütünleştirilmiş kodu ise `GetAppDomain` null değerini döndürür.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
