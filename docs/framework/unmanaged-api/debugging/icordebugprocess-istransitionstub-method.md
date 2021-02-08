---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugProcess:: ısgeçişli Tionstub yöntemi'
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
ms.openlocfilehash: 0da8527538c2573b1ec0d26f8711644fe8fcca2a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782019"
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
 'ndaki `CORDB_ADDRESS` Söz konusu adresi belirten bir değer.  
  
 `pbTransitionStub`  
 dışı `true` Belirtilen adres, yönetilen koda geçişe neden olacak bir saplama içindeyse bir Boole değeri işaretçisi; Aksi takdirde * `pbTransitionStub` olur `false` .  
  
## <a name="remarks"></a>Açıklamalar  

 `IsTransitionStub`Yöntemi, yönetilmeyen atlama kodu tarafından, yönetilen Stepper üzerinde atlama denetimini ne zaman döneceğine karar vermek için kullanılabilir.  
  
 Taşınabilir çalıştırılabilir (PE) dosyasındaki bilgilere bakarak da geçiş saplamalarını de kullanabilirsiniz.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
