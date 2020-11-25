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
ms.openlocfilehash: c36dec80b6885b0ee56670b94dbd0b155a9710b4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729713"
---
# <a name="icordebugeval2callparameterizedfunction-method"></a>ICorDebugEval2::CallParameterizedFunction Yöntemi

Belirtilen ICorDebugFunction öğesine bir çağrı kurar, bu, Oluşturucusu parametreleri alan bir sınıfın içinde iç içe eklenebilir <xref:System.Type> veya kendisi <xref:System.Type> parametre alabilir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
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
 'ndaki `ICorDebugFunction` Çağrılacak işlevi temsil eden nesneye yönelik bir işaretçi.  
  
 `nTypeArgs`  
 'ndaki İşlevin aldığı bağımsız değişken sayısı.  
  
 `ppTypeArgs`  
 'ndaki Her biri bir işlev bağımsız değişkenini temsil eden ICorDebugType nesnesine işaret eden bir işaretçiler dizisi.  
  
 `nArgs`  
 'ndaki İşleve geçirilen değer sayısı.  
  
 `ppArgs`  
 'ndaki Her biri bir işlev bağımsız değişkeninde geçirilen değeri temsil eden ICorDebugValue nesnesine işaret eden bir işaretçiler dizisi.  
  
## <a name="remarks"></a>Açıklamalar  

 `CallParameterizedFunction` , işlevin tür parametrelerine sahip bir sınıfın içinde olabileceği, kendi tür parametreleri veya her ikisini de içermesi dışında [ıcorınıtınkıonıval:: CallFunction](icordebugeval-callfunction-method.md) gibidir. Tür bağımsız değişkenleri önce sınıf için, sonra da işlev için verilmelidir.  
  
 İşlev farklı bir uygulama etki alanında ise, bir geçiş gerçekleşir. Ancak, tüm tür ve değer bağımsız değişkenleri hedef uygulama etki alanında olmalıdır.  
  
 İşlev değerlendirmesi yalnızca sınırlı senaryolarda gerçekleştirilebilir. `CallParameterizedFunction`Veya `ICorDebugEval::CallFunction` başarısız olursa, döndürülen HRESULT hatanın en genel olası nedenini gösterir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
