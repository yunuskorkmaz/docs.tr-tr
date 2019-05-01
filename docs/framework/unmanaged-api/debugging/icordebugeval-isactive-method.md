---
title: ICorDebugEval::IsActive Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugEval.IsActive
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::IsActive
helpviewer_keywords:
- IsActive method, ICorDebugEval interface [.NET Framework debugging]
- ICorDebugEval::IsActive method [.NET Framework debugging]
ms.assetid: bf2bba24-d278-43bd-b1c5-35680e748d3e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0d992ea86b3221af222bb01f1985fe277cea5a2c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61989008"
---
# <a name="icordebugevalisactive-method"></a>ICorDebugEval::IsActive Yöntemi
Bu Icordebugeval nesne yürütülmekte olmadığını belirten bir değer alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT IsActive (  
    [out] BOOL              *pbActive  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pbActive`  
 [out] Bu değerlendirme etkin olup olmadığını gösteren bir değer işaretçisi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
