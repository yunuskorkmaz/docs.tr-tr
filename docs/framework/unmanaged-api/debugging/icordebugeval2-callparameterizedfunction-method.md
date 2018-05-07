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
ms.openlocfilehash: 77d9ec0cf1cbca63382e7f29de85c2f9566dc2bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugeval2callparameterizedfunction-method"></a>ICorDebugEval2::CallParameterizedFunction Yöntemi
Oluşturucusu geçen bir sınıf içinde yuvalanmış belirtilen ICorDebugFunction çağrısı ayarlar <xref:System.Type> parametreleri veya can kendisini alın <xref:System.Type> parametreleri.  
  
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
  
#### <a name="parameters"></a>Parametreler  
 `pFunction`  
 [in] Bir işaretçi bir `ICorDebugFunction` çağrılacak işlev temsil eden nesne.  
  
 `nTypeArgs`  
 [in] İşlev alır bağımsız değişken sayısı.  
  
 `ppTypeArgs`  
 [in] Her biri bir işlev bağımsız değişkeni temsil eden bir Icordebugtype bir nesneye işaret etmiyor dizisi işaretçisi.  
  
 `nArgs`  
 [in] Değerlerin sayısını işlevinde geçirildi.  
  
 `ppArgs`  
 [in] İşaretçileri, her biri bir değeri temsil eden bir Icordebugvalue bir nesneye işaret etmiyor dizisi işlevi bağımsız değişken geçirildi.  
  
## <a name="remarks"></a>Açıklamalar  
 `CallParameterizedFunction` benzer [Icordebugeval::CallFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-callfunction-method.md) işlev türü parametrelere sahip bir sınıf içinde olabilir ancak bu, kendisini tür parametreleri ya da her ikisini de alabilir. Tür bağımsız değişkenleri sınıfı ve ardından işlevi için önce verilmelidir.  
  
 İşlev farklı uygulama etki alanında ise, bir geçiş meydana gelir. Ancak, tüm türü ve değeri bağımsız değişkenleri hedef uygulama etki alanında olmalıdır.  
  
 İşlev değerlendirmesi yalnızca sınırlı senaryolarda gerçekleştirilebilir. Varsa `CallParameterizedFunction` veya `ICorDebugEval::CallFunction` başarısız olduğunda, döndürülen HRESULT hata olası en genel nedeni gösterilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
