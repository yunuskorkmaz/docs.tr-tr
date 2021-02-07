---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugEval2:: NewStringWithLength yöntemi'
title: ICorDebugEval2::NewStringWithLength Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.NewStringWithLength
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::NewStringWithLength
helpviewer_keywords:
- NewStringWithLength method [.NET Framework debugging]
- ICorDebugEval2::NewStringWithLength method [.NET Framework debugging]
ms.assetid: d5f54a34-6335-4708-b407-a756ec70fab4
topic_type:
- apiref
ms.openlocfilehash: 23864dabefcb4fc12f73c66bc2d19a6cca1aacf0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693531"
---
# <a name="icordebugeval2newstringwithlength-method"></a>ICorDebugEval2::NewStringWithLength Yöntemi

Belirtilen bir uzunluğa sahip, belirtilen içeriğe sahip bir dize oluşturur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT NewStringWithLength (  
    [in] LPCWSTR               string,  
    [in] UINT                  uiLength  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `string`  
 'ndaki Dize değerine yönelik bir işaretçi.  
  
 `uiLength`  
 'ndaki Dizenin uzunluğu.  
  
## <a name="remarks"></a>Açıklamalar  

 Dizenin sondaki NULL karakterinin yönetilen dizede olması bekleniyorsa, `NewStringWithLength` yöntemi çağıranın dize uzunluğunun sondaki null karakteri içerdiğinden emin olması gerekir.  
  
 Dize her zaman iş parçacığının yürütüldüğü uygulama etki alanında oluşturulur.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
