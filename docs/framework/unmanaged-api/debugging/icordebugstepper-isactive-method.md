---
title: "ICorDebugStepper::IsActive Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStepper.IsActive
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStepper::IsActive
helpviewer_keywords:
- IsActive method, ICorDebugStepper interface [.NET Framework debugging]
- ICorDebugStepper::IsActive method [.NET Framework debugging]
ms.assetid: 8b35e7a9-b40e-40a9-8d8e-b82e823fc575
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dd919852d3e7c187dff7fc4304d0a1b42f5294e0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugstepperisactive-method"></a>ICorDebugStepper::IsActive Yöntemi
Bu ICorDebugStepper bir adım şu anda yürütülmekte olup olmadığını belirten bir değer alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT IsActive (  
    [out] BOOL   *pbActive  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pbActive`  
 [out] Döndürür `true` Adımlayıcı şu anda bir adım; yürütüyor, aksi takdirde döndürür `false`.  
  
## <a name="remarks"></a>Açıklamalar  
 Hata ayıklayıcı alıncaya kadar herhangi bir adım eylem etkin kaldığı bir [Icordebugmanagedcallback::stepcomplete](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md) çağrısı, hangi otomatik olarak Adımlayıcı devre dışı bırakır. Adımlayıcı de erken çağırarak devre dışı bırakılabilir [ICorDebugStepper::Deactivate](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-deactivate-method.md) önce geri arama koşulu ulaştı.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
