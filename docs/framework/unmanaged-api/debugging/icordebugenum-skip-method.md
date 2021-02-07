---
description: 'Şu konuda daha fazla bilgi edinin: ıcorı, Genum:: Skip yöntemi'
title: ICorDebugEnum::Skip Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugEnum.Skip
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEnum::Skip
helpviewer_keywords:
- ICorDebugEnum::Skip method [.NET Framework debugging]
- Skip method, ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: e925d88a-67a5-4f76-88b8-09cedeed0232
topic_type:
- apiref
ms.openlocfilehash: f72e400b3c2c911f609aca19f1b7d6a3a4e785cc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99694363"
---
# <a name="icordebugenumskip-method"></a>ICorDebugEnum::Skip Yöntemi

İmleci belirtilen öğe sayısına göre numaralandırmada ileri doğru kaydırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT Skip (  
    [in] ULONG celt  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `celt`  
 'ndaki İmlecin ileri taşımasını sağlayan öğe sayısı.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugEnum Arabirimi](icordebugenum-interface1.md)
