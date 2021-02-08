---
description: 'Hakkında daha fazla bilgi edinin: ICorDebugStepper::D eactivate yöntemi'
title: ICorDebugStepper::Deactivate Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.Deactivate
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::Deactivate
helpviewer_keywords:
- Deactivate method [.NET Framework debugging]
- ICorDebugStepper::Deactivate method [.NET Framework debugging]
ms.assetid: 855f4199-b62d-40ce-998e-1eb4a1772142
topic_type:
- apiref
ms.openlocfilehash: 039c52f5bc237506dcc648ace70789c8eb7ef8c9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794669"
---
# <a name="icordebugstepperdeactivate-method"></a>ICorDebugStepper::Deactivate Yöntemi

Bu ICorDebugStepper, aldığı son adım komutunu iptal etmesine neden olur.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT Deactivate ();  
```  
  
## <a name="remarks"></a>Açıklamalar  

 Yeni bir Adımlama komutu, en son alınan adım komutu iptal edildikten sonra verilebilir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
