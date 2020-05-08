---
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
ms.openlocfilehash: a2b76cb59a95082e0cf9c0884b8277cca3c8fe8d
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976076"
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
