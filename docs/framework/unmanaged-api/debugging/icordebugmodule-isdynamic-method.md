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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f8012d669cabc1bb589dcfe66bdf2e9b83dc5cb2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988041"
---
# <a name="icordebugmoduleisdynamic-method"></a>ICorDebugModule::IsDynamic Yöntemi
Bu modül dinamik olup olmadığını belirten bir değer alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT IsDynamic(  
    [out] BOOL *pDynamic  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pDynamic`  
 [out] `true` bu modül dinamik; Aksi takdirde ise `false`.  
  
## <a name="remarks"></a>Açıklamalar  
 Dinamik modül, yeni sınıflar ekleyebilirsiniz ve modül yüklendikten sonra mevcut sınıfları silin. [Icordebugmanagedcallback::loadclass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) ve [Icordebugmanagedcallback::unloadclass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) geri çağırmaları bildirmek hata ayıklayıcı bir sınıf, eklenmiş veya silinmiş.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
