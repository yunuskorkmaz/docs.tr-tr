---
title: "ICorDebugEval2::NewParameterizedObject Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugEval2.NewParameterizedObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::NewParameterizedObject
helpviewer_keywords:
- NewParameterizedObject method [.NET Framework debugging]
- ICorDebugEval2::NewParameterizedObject method [.NET Framework debugging]
ms.assetid: 3d705463-e640-4249-8036-4e8206d03cfe
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 39b69a82f25ab6df5f2bd2f6dc70caf1bf13a0f9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugeval2newparameterizedobject-method"></a>ICorDebugEval2::NewParameterizedObject Yöntemi
Yeni bir parametreli türü nesnesi oluşturur ve nesnenin oluşturucusu yöntemini çağırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT NewParameterizedObject (  
    [in] ICorDebugFunction     *pConstructor,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[],  
    [in] ULONG32               nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pConstructor`  
 [in] Bir işaretçi ICorDebugFunction nesneye Oluşturucusu örneğinin oluşturulması için nesnesinin temsil eder.  
  
 `nTypeArgs`  
 [in] Tür bağımsız değişkenleri sayıda geçirildi.  
  
 `ppTypeArgs`  
 [in] Her biri noktalarını oluşturulmasını nesne için bir tür bağımsız değişkeni temsil eden bir Icordebugtype nesnesi için bir dizi işaretçisi.  
  
 `nArgs`  
 [in] Oluşturucuya geçirilen bağımsız değişken sayısı.  
  
 `ppArgs`  
 [in] Oluşturucuya geçirilen bağımsız değişken değeri temsil eden Icordebugvalue nesne işaret her biri bir dizi işaretçisi.  
  
## <a name="remarks"></a>Açıklamalar  
 Nesnenin oluşturucusu sürebilir <xref:System.Type> parametreleri.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
