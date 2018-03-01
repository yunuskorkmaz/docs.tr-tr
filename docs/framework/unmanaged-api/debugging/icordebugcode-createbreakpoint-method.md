---
title: "ICorDebugCode::CreateBreakpoint Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugCode.CreateBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::CreateBreakpoint
helpviewer_keywords:
- ICorDebugCode::CreateBreakpoint method [.NET Framework debugging]
- CreateBreakpoint method, ICorDebugCode interface [.NET Framework debugging]
ms.assetid: 46842618-0fe4-480b-871c-82fba82d23d9
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 211435025fe06eff180244430138be9d42c5eb86
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcodecreatebreakpoint-method"></a>ICorDebugCode::CreateBreakpoint Yöntemi
Bu kod kesimi belirtilen uzaklığında bir kesme noktası oluşturur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT CreateBreakpoint (  
    [in] ULONG32     offset,  
    [out] ICorDebugFunctionBreakpoint **ppBreakpoint  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `offset`  
 [in] Uzaklığı kesme noktası oluşturmak.  
  
 `ppBreakpoint`  
 [out] Kesme noktası temsil eden bir "ICorDebugFunctionBreakpoint" nesnesinin adresi için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Kesme noktası etkinleştirilmeden önce işlem nesnesine eklenmelidir.  
  
 Bu kodu Microsoft Ara dili (MSIL) koddur ve bir tam zamanında (JIT) yoktur-kesme kodunun derlenmiş, yerel sürümünü JIT derlenmiş kod da uygulanır. (Aynı kodu daha sonra JIT derlenmiş ise geçerlidir.)  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 
