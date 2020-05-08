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
ms.openlocfilehash: e901c65824ee8d6949c79c7778944148c0d9eb28
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976063"
---
# <a name="icordebugeval2rudeabort-method"></a>ICorDebugEval2::RudeAbort Yöntemi
Şu anda gerçekleştirdiği hesaplamayı `ICorDebugEval2` iptal eder.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT RudeAbort ();  
```  
  
## <a name="remarks"></a>Açıklamalar  
 `RudeAbort`, değerlendirici 'in tuttuğu herhangi bir kilidi serbest bırakmadığından, hata ayıklama oturumunu güvenli olmayan bir durumda bırakır. Bu yöntemi çok dikkatli bir şekilde çağırın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
