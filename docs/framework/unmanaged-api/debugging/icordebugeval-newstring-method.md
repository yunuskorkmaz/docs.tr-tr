---
description: 'Şu konuda daha fazla bilgi edinin: ıcorıbgeval:: NewString Yöntemi'
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
ms.openlocfilehash: 21eb49900d84cb1ad1f68a701998a4a778c3ef17
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693852"
---
# <a name="icordebugevalnewstring-method"></a>ICorDebugEval::NewString Yöntemi

Belirtilen içeriğe sahip yeni bir dize örneği ayırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT NewString (  
    [in] LPCWSTR   string  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `string`  
 'ndaki Dize için içerik işaretçisi.  
  
## <a name="remarks"></a>Açıklamalar  

 Dize her zaman iş parçacığının yürütüldüğü uygulama etki alanında oluşturulur.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
