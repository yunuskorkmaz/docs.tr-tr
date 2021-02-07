---
description: 'Hakkında daha fazla bilgi edinin: ICorDebugEval2:: RudeAbort Yöntemi'
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
ms.openlocfilehash: 2835fd635da007b5ee3f0e642b77f3954945f168
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693518"
---
# <a name="icordebugeval2rudeabort-method"></a>ICorDebugEval2::RudeAbort Yöntemi

`ICorDebugEval2`Şu anda gerçekleştirdiği hesaplamayı iptal eder.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT RudeAbort ();  
```  
  
## <a name="remarks"></a>Açıklamalar  

 `RudeAbort` , değerlendirici 'in tuttuğu herhangi bir kilidi serbest bırakmadığından, hata ayıklama oturumunu güvenli olmayan bir durumda bırakır. Bu yöntemi çok dikkatli bir şekilde çağırın.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
