---
title: ICorDebugChain::GetCaller Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetCaller
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetCaller
helpviewer_keywords:
- ICorDebugChain::GetCaller method [.NET Framework debugging]
- GetCaller method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: d0b8ab4b-d7d2-4fa0-945f-3d2b87e7e991
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1a0b5d702e9718ce6ac537beae67fc190b152b9f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405149"
---
# <a name="icordebugchaingetcaller-method"></a>ICorDebugChain::GetCaller Metodu
Bu zincir adlı zinciri alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetCaller (  
    [out] ICorDebugChain      **ppChain  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppChain`  
 [out] Bir işaretçi adresine Icordebugchain nesnenin arama zinciri temsil eder.  
  
 (Bu zincir veya hata ayıklayıcı çağrı yığını başlatılmış durumda olacaktır gibi) bu zincirini kendiliğinden çağrıldı, `ppChain` null olur.  
  
## <a name="remarks"></a>Açıklamalar  
 Arama zinciri çağrı iş parçacıkları arasında sıralanmış farklı bir iş parçacığı üzerinde olabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
