---
title: ICorDebugProcess::IsTransitionStub Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.IsTransitionStub
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::IsTransitionStub
helpviewer_keywords:
- ICorDebugProcess::IsTransitionStub method [.NET Framework debugging]
- IsTransitionStub method [.NET Framework debugging]
ms.assetid: f7653317-7e48-4163-be03-f50f1a4b0f70
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1ec29aa748c437199434fa1394e1a00c82154447
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67766875"
---
# <a name="icordebugprocessistransitionstub-method"></a>ICorDebugProcess::IsTransitionStub Yöntemi
Adres yönetilen koda geçiş neden olacak bir saplama içinde olup olmadığını belirten bir değer alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT IsTransitionStub(  
    [in]  CORDB_ADDRESS address,  
    [out] BOOL *pbTransitionStub);  
```  
  
## <a name="parameters"></a>Parametreler  
 `address`  
 [in] A `CORDB_ADDRESS` söz konusu adresini belirten bir değer.  
  
 `pbTransitionStub`  
 [out] Boolean bir değer için bir işaretçi `true` yönetilen kod; geçiş neden olacak bir saplama içinde belirtilen adresi ise, aksi takdirde *`pbTransitionStub` olduğu `false`.  
  
## <a name="remarks"></a>Açıklamalar  
 `IsTransitionStub` Yöntemi sürüm denetimi için yönetilen Adımlayıcı döndürmek ne zaman karar için yönetilmeyen bir atlama kodu tarafından kullanılabilir.  
  
 Kimlik geçişi saptamalar da taşınabilir yürütülebilir (PE) dosya bilgileri bakarak yapabilirsiniz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
