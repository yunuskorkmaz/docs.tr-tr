---
title: ICorDebugManagedCallback2::FunctionRemapOpportunity Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.FunctionRemapOpportunity
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::FunctionRemapOpportunity
helpviewer_keywords:
- FunctionRemapOpportunity method [.NET Framework debugging]
- ICorDebugManagedCallback2::FunctionRemapOpportunity method [.NET Framework debugging]
ms.assetid: 0d6471bc-ad9b-4b1d-a307-c10443918863
topic_type:
- apiref
ms.openlocfilehash: d2fc59621cbb6752830c7a8392ce4e0c476ef9e7
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210065"
---
# <a name="icordebugmanagedcallback2functionremapopportunity-method"></a>ICorDebugManagedCallback2::FunctionRemapOpportunity Yöntemi
Kod yürütmenin, düzenlenmiş bir işlevin daha eski bir sürümündeki bir sıra noktasına ulaştığı hata ayıklayıcıya bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT FunctionRemapOpportunity (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFunction    *pOldFunction,  
    [in] ICorDebugFunction    *pNewFunction,  
    [in] ULONG32              oldILOffset  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pAppDomain`  
 'ndaki Düzenlenen işlevi içeren uygulama etki alanını temsil eden ICorDebugAppDomain nesnesine yönelik bir işaretçi.  
  
 `pThread`  
 'ndaki Yeniden eşleme kesme noktasının karşılaştığı iş parçacığını temsil eden ICorDebugThread nesnesine yönelik bir işaretçi.  
  
 `pOldFunction`  
 'ndaki İş parçacığında çalışmakta olan işlevin sürümünü temsil eden ICorDebugFunction nesnesine yönelik bir işaretçi.  
  
 `pNewFunction`  
 'ndaki İşlevin en son sürümünü temsil eden ICorDebugFunction nesnesine yönelik bir işaretçi.  
  
 `oldILOffset`  
 'ndaki İşlevin eski sürümündeki yönerge işaretçisinin Microsoft ara dili (MSIL) boşluğu.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu geri çağırma, [ICorDebugILFrame2:: RemapFunction](icordebugilframe2-remapfunction-method.md) metodunu çağırarak, yönerge işaretçisini belirtilen işlevin yeni sürümünde doğru yere yeniden eşlemek için bir fırsat sağlar. Hata ayıklayıcı `RemapFunction` [ICorDebugController:: Continue](icordebugcontroller-continue-method.md) metodunu çağırmadan önce çağrıdıysa, çalışma zamanı eski kodu yürütmeye devam eder ve `FunctionRemapOpportunity` sonraki dizi noktasında başka bir geri çağırma harekete geçmeyecektir.  
  
 Bu geri çağırma, hata ayıklayıcı S_OK dönene kadar verilen işlevin daha eski bir sürümünü yürüten her çerçeve için çağrılacaktır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugManagedCallback2 Arabirimi](icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback Arabirimi](icordebugmanagedcallback-interface.md)
