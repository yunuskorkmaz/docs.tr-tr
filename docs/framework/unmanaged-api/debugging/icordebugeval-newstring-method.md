---
title: ICorDebugEval::NewString Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugEval.NewString
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::NewString
helpviewer_keywords:
- NewString method [.NET Framework debugging]
- ICorDebugEval::NewString method [.NET Framework debugging]
ms.assetid: 29e7a14b-d50e-4852-bfda-011b76c0c9ee
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: db609bdee7975b6c067271f99529e2cf2240f720
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61989033"
---
# <a name="icordebugevalnewstring-method"></a>ICorDebugEval::NewString Yöntemi
Yeni bir dize örneği belirtilen içeriğiyle ayırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT NewString (  
    [in] LPCWSTR   string  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `string`  
 [in] İçeriği dize işaretçisi.  
  
## <a name="remarks"></a>Açıklamalar  
 Dize, her zaman iş parçacığı gerçekleştirmektedir uygulama etki alanında oluşturulur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
