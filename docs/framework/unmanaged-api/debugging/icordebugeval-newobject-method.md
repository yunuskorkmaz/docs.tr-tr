---
title: "ICorDebugEval::NewObject Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval.NewObject
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval::NewObject
helpviewer_keywords:
- NewObject method [.NET Framework debugging]
- ICorDebugEval::NewObject method [.NET Framework debugging]
ms.assetid: ce3025e8-defa-4c5e-8298-f49d71fa5736
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 98c885e7ffd4b35bcc3af34757509910c78c0c90
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugevalnewobject-method"></a>ICorDebugEval::NewObject Yöntemi
Yeni bir nesne örneği ayırır ve belirtilen Oluşturucusu yöntemini çağırır.  
  
 Bu yöntem .NET Framework 2.0 sürümünde kullanımdan kalkmıştır. Kullanım [Icordebugeval2::newparameterizedobject](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md) yerine.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT NewObject (  
    [in] ICorDebugFunction  *pConstructor,  
    [in] ULONG32            nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pConstructor`  
 [in] Çağrılacak Oluşturucusu.  
  
 `nArgs`  
 [in] Boyutunu `ppArgs` dizi.  
  
 `ppArgs`  
 [in] Her biri bir bağımsız değişken oluşturucuya geçirilen temsil eden bir Icordebugvalue nesneler dizisi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** 1.1, 1.0  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [NewParameterizedObject Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md)
