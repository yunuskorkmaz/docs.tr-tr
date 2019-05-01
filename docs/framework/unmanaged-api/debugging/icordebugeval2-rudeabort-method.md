---
title: ICorDebugEval2::RudeAbort Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.RudeAbort
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::RudeAbort
helpviewer_keywords:
- ICorDebugEval2::RudeAbort method [.NET Framework debugging]
- RudeAbort method, ICorDebugEval2 interface [.NET Framework debugging]
ms.assetid: 02468edf-d32b-4cb3-aaa8-3dd2abfc8b25
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0aabff090634f1ecdeec5636336ad1fb77b8b81c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988929"
---
# <a name="icordebugeval2rudeabort-method"></a>ICorDebugEval2::RudeAbort Yöntemi
Hesaplama durdurur bu `ICorDebugEval2` şu anda gerçekleştiriyor.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT RudeAbort ();  
```  
  
## <a name="remarks"></a>Açıklamalar  
 `RudeAbort` güvenli olmayan bir durumda hata ayıklama oturumu bırakır, böylece değerlendirme tutan kilitleri serbest bırakmaz. İşlemini çok dikkatli bu yöntemi çağırın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
