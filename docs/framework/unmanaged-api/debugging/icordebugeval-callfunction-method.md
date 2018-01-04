---
title: "ICorDebugEval::CallFunction Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval.CallFunction
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval::CallFunction
helpviewer_keywords:
- ICorDebugEval::CallFunction method [.NET Framework debugging]
- CallFunction method [.NET Framework debugging]
ms.assetid: 7f470c5c-e1c0-4d8d-aad8-830f113ae751
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3c2d5582c9ac69692546e9a2310c4d0c9cdde83e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugevalcallfunction-method"></a>ICorDebugEval::CallFunction Yöntemi
Belirtilen işlev çağrısı ayarlar.  
  
 Bu yöntem .NET Framework 2.0 sürümünde kullanımdan kalkmıştır. Kullanım [Icordebugeval2::callparameterizedfunction](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md) yerine.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT CallFunction (  
    [in] ICorDebugFunction  *pFunction,  
    [in] ULONG32            nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pFunction`  
 [in] İşaretçi ICorDebugFunction nesneye çağrılacak işlev belirtir.  
  
 `nArgs`  
 [in] İşlevin bağımsız değişken sayısı.  
  
 `ppArgs`  
 [in] Her biri işleve iletilecek bağımsız değişken belirten Icordebugvalue nesneye işaret dizisi işaretçisi.  
  
## <a name="remarks"></a>Açıklamalar  
 İşlev sanal ise `CallFunction` sanal gönderme gerçekleştirir. İşlev farklı uygulama etki alanında ise, tüm bağımsız değişkenler de o uygulama etki alanında olduğu sürece bir geçiş meydana gelir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** WindowSee [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** 1.1, 1.0  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [CallParameterizedFunction Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md)
