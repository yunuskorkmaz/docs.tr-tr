---
title: ICorDebugILFrame::SetIP Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.SetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::SetIP
helpviewer_keywords:
- SetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::SetIP method [.NET Framework debugging]
ms.assetid: 23f38dc1-85e4-4263-9235-2d05bbb6a833
topic_type:
- apiref
ms.openlocfilehash: 325b2a009e77d87e95bdb02803dd3c4675c26ddc
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213432"
---
# <a name="icordebugilframesetip-method"></a>ICorDebugILFrame::SetIP Yöntemi
Yönerge işaretçisini, Microsoft ara dili (MSIL) kodunda belirtilen konum konumunu ayarlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT SetIP (  
    [in] ULONG32 nOffset  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `nOffset`  
 MSIL kodunda konum konumu.  
  
## <a name="remarks"></a>Açıklamalar  
 `SetIP`Geçerli iş parçacığının tüm çerçevelerini ve zincirlerini hemen geçersiz kılmak için çağrılar. Hata ayıklayıcı, öğesine yapılan çağrıdan sonra çerçeve bilgisine ihtiyaç duyuyorsa `SetIP` , yeni bir yığın izlemesi gerçekleştirmesi gerekir.  
  
 [ICorDebug](icordebug-interface.md) , yığın çerçevesini geçerli bir durumda tutmaya çalışacak. Ancak, çerçeve geçerli bir durumdaysa bile başlatılmamış yerel değişkenler gibi sorunlar olabilir. Çağıran, çalışan programın tutarlılığına ilişkin emin olmanın sorumluluğundadır.  
  
 64 bit platformlarda, yönerge işaretçisi bir `catch` veya bloğunun dışına taşınamaz `finally` . `SetIP`Bu tür bir taşımayı 64 bitlik bir platformda yapmak için çağrılırsa, hata belirten BIR hresult döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
