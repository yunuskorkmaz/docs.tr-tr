---
title: "ICorDebugILFrame::CanSetIP Yöntemi"
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
- ICorDebugILFrame.CanSetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::CanSetIP
helpviewer_keywords:
- CanSetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::CanSetIP method [.NET Framework debugging]
ms.assetid: 16caf02f-c71e-486c-90b0-f0e54357d8f0
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 22d0df9add0a4ce35b1a590d65e30a6756fec49c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframecansetip-method"></a>ICorDebugILFrame::CanSetIP Yöntemi
Yönerge işaretçisi Microsoft Ara dili (MSIL) kodunu belirtilen uzaklık konumda ayarlamak güvenli olup olmadığını belirten bir HRESULT alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT CanSetIP (  
    [in] ULONG32   nOffset  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `nOffset`  
 [in] Yönerge işaretçisi istenen ayarı.  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanım `CanSetIP` yöntemi çağırmadan önce [Icordebugılframe::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) yöntemi. Varsa `CanSetIP` herhangi HRESULT döndürür S_OK dışında hala çağırabilirsiniz `ICorDebugILFrame::SetIP`, ancak hata ayıklayıcı ayıklanacak kod güvenli ve doğru yürütülmesi devam edecek garantisi yoktur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug, h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
