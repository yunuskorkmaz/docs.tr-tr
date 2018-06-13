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
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412584"
---
# <a name="icordebugeval2rudeabort-method"></a>ICorDebugEval2::RudeAbort Yöntemi
Hesaplama durdurur bu `ICorDebugEval2` şu anda gerçekleştiriyor.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT RudeAbort ();  
```  
  
## <a name="remarks"></a>Açıklamalar  
 `RudeAbort` hata ayıklama oturumu güvenli olmayan bir durumda bırakır şekilde değerlendirici tutan kilitleri bırakmaz. Bunu yaparken çok dikkatli bu yöntemi çağırın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
