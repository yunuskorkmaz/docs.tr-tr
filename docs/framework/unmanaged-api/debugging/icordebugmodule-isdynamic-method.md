---
title: ICorDebugModule::IsDynamic Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugModule.IsDynamic
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::IsDynamic
helpviewer_keywords:
- IsDynamic method [.NET Framework debugging]
- ICorDebugModule::IsDynamic method [.NET Framework debugging]
ms.assetid: 5eefe716-5025-4a4c-970c-c823cdc7bb87
topic_type:
- apiref
ms.openlocfilehash: 45b1d0c0a3199227ab644ba8732198dd14b1cb4c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793004"
---
# <a name="icordebugmoduleisdynamic-method"></a>ICorDebugModule::IsDynamic Yöntemi
Bu modülün dinamik olup olmadığını gösteren bir değer alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT IsDynamic(  
    [out] BOOL *pDynamic  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pDynamic`  
 [out] Bu modül dinamik ise `true`; Aksi takdirde, `false`.  
  
## <a name="remarks"></a>Açıklamalar  
 Dinamik bir modül, modül yüklendikten sonra bile yeni sınıflar ekleyebilir ve var olan sınıfları silebilir. [ICorDebugManagedCallback:: LoadClass](icordebugmanagedcallback-loadclass-method.md) ve [ICorDebugManagedCallback:: UnloadClass](icordebugmanagedcallback-unloadclass-method.md) geri çağırmaları, bir sınıf eklendiğinde veya silindiğinde hata ayıklayıcıyı bilgilendirir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
