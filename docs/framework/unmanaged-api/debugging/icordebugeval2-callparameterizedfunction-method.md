---
title: ICorDebugEval2::CallParameterizedFunction Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.CallParameterizedFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::CallParameterizedFunction
helpviewer_keywords:
- ICorDebugEval2::CallParameterizedFunction method [.NET Framework debugging]
- CallParameterizedFunction method [.NET Framework debugging]
ms.assetid: 72f54a45-dbe6-4bb4-8c99-e879a27368e5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cba4eb2b76d7057a5ed66a35342a79615cb8539f
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57487736"
---
# <a name="icordebugeval2callparameterizedfunction-method"></a>ICorDebugEval2::CallParameterizedFunction Yöntemi
Bir çağrı, Oluşturucusu götüren bir sınıf içinde iç içe belirtilen ICorDebugFunction ayarlar <xref:System.Type> parametreleri veya can'ın kendisi <xref:System.Type> parametreleri.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT CallParameterizedFunction (  
    [in] ICorDebugFunction     *pFunction,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[],  
    [in] ULONG32               nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pFunction`  
 [in] Bir işaretçi bir `ICorDebugFunction` çağrılacak işlev temsil eden nesne.  
  
 `nTypeArgs`  
 [in] Alan işlev bağımsız değişken sayısı.  
  
 `ppTypeArgs`  
 [in] Bir dizi işaretçileri, her biri bir işlev bağımsız değişkeni temsil eden bir Icordebugtype nesneye işaret eder.  
  
 `nArgs`  
 [in] Değerlerin sayısını işleve geçirildi.  
  
 `ppArgs`  
 [in] Her biri bir değeri temsil eden bir Icordebugvalue nesneye işaret eden bir işaretçiler dizisi, bir işlev bağımsız değişkeni geçirildi.  
  
## <a name="remarks"></a>Açıklamalar  
 `CallParameterizedFunction` benzer [Icordebugeval::CallFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-callfunction-method.md) işlevi tür parametreleri ile bir sınıf içinde olabilir dışında kendi tür parametreleri veya her ikisi de alabilir. Tür bağımsız değişkeni, ilk sınıf ve işlev için verilmelidir.  
  
 İşlev, farklı uygulama etki alanında ise, bir geçiş meydana gelir. Ancak, tüm türü ve değeri bağımsız değişkenleri hedef uygulama etki alanında olmalıdır.  
  
 İşlev değerlendirmesi yalnızca sınırlı sayıda senaryoda gerçekleştirilebilir. Varsa `CallParameterizedFunction` veya `ICorDebugEval::CallFunction` başarısız olursa, döndürülen HRESULT hata olası en genel nedenlerinden gösterecektir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
