---
title: "ICorDebugEval2::NewParameterizedObjectNoConstructor Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval2.NewParameterizedObjectNoConstructor
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval2::NewParameterizedObjectNoConstructor
helpviewer_keywords:
- NewParameterizedObjectNoConstructor method [.NET Framework debugging]
- ICorDebugEval2::NewParameterizedObjectNoConstructor method [.NET Framework debugging]
ms.assetid: f15b5b78-94f4-4eb9-b3b3-a621272f357c
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 27e4693b39f9ce27ac18eb2fa542b5a0196f21cb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugeval2newparameterizedobjectnoconstructor-method"></a>ICorDebugEval2::NewParameterizedObjectNoConstructor Yöntemi
Belirtilen sınıfının yeni bir parametreli türü nesne Oluşturucusu yöntemini çağırmak çalışırken olmadan başlatır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT NewParameterizedObjectNoConstructor (  
    [in] ICorDebugClass        *pClass,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[]  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pClass`  
 [in] Bir işaretçi Icordebugclass nesneye örneğinin oluşturulması için nesnenin sınıfını temsil eder.  
  
 `nTypeArgs`  
 [in] Tür bağımsız değişkenleri sayıda geçirildi.  
  
 `ppTypeArgs`  
 [in] Her biri noktalarını oluşturulmasını nesne için bir tür bağımsız değişkeni temsil eden bir Icordebugtype nesnesi için bir dizi işaretçisi.  
  
## <a name="remarks"></a>Açıklamalar  
 `NewParameterizedObjectNoConstructor` Yöntemi yanlış sayıda tür bağımsız değişkeni, başarısız olur veya tür bağımsız değişkeni yanlış tür geçirildi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
