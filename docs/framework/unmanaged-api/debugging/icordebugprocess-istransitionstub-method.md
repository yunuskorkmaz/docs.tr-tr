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
ms.openlocfilehash: 852c77be0dc8ef91933bacbbd3d6b3f5a69ae8c8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139394"
---
# <a name="icordebugprocessistransitionstub-method"></a>ICorDebugProcess::IsTransitionStub Yöntemi
Bir adresin, yönetilen koda geçişe neden olacak bir saplama içinde olup olmadığını gösteren bir değer alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT IsTransitionStub(  
    [in]  CORDB_ADDRESS address,  
    [out] BOOL *pbTransitionStub);  
```  
  
## <a name="parameters"></a>Parametreler  
 `address`  
 'ndaki Söz konusu adresi belirten bir `CORDB_ADDRESS` değeri.  
  
 `pbTransitionStub`  
 dışı Belirtilen adres, yönetilen koda geçişe neden olacak bir saplama içindeyse, `true` Boole değeri işaretçisi; Aksi halde *`pbTransitionStub` `false`.  
  
## <a name="remarks"></a>Açıklamalar  
 `IsTransitionStub` yöntemi, yönetilmeyen atlama kodu tarafından, yönetilen Stepper üzerinde atlama denetimini ne zaman döneceğine karar vermek için kullanılabilir.  
  
 Taşınabilir çalıştırılabilir (PE) dosyasındaki bilgilere bakarak da geçiş saplamalarını de kullanabilirsiniz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
