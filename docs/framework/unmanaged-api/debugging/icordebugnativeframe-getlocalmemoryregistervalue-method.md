---
title: ICorDebugNativeFrame::GetLocalMemoryRegisterValue Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetLocalMemoryRegisterValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetLocalMemoryRegisterValue
helpviewer_keywords:
- ICorDebugNativeFrame::GetLocalMemoryRegisterValue method [.NET Framework debugging]
- GetLocalMemoryRegisterValue method
ms.assetid: 33a19f6e-1029-4d53-af64-19591c6e58ee
topic_type:
- apiref
ms.openlocfilehash: 788ce2d47769caa72518e0357a0affdff5862699
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137278"
---
# <a name="icordebugnativeframegetlocalmemoryregistervalue-method"></a>ICorDebugNativeFrame::GetLocalMemoryRegisterValue Metodu
Bir bağımsız değişkenin veya yerel değişkenin değerini alır, bu yerel çerçeve için sırasıyla alt sözcük ve yüksek sözcük belirtilen yazmaç ve bellek konumunda depolanır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetLocalMemoryRegisterValue (  
    [in] CORDB_ADDRESS      highWordAddress,  
    [in] CorDebugRegister   lowWordRegister,  
    [in] ULONG              cbSigBlob,  
    [in] PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `highWordAddress`  
 'ndaki Değerin yüksek sözcüğünü içeren bellek konumunu belirten bir `CORDB_ADDRESS` değeri.  
  
 `lowWordRegister`  
 'ndaki Değerin düşük sözcüğünü içeren kaydı belirten "CorDebugRegister" numaralandırmasının değeri.  
  
 `cbSigBlob`  
 'ndaki `pvSigBlob` parametresi tarafından başvurulan ikili meta veri imzasının boyutunu belirten bir tamsayı.  
  
 `pvSigBlob`  
 'ndaki Değerin türünün ikili meta veri imzasına işaret eden bir `PCCOR_SIGNATURE` değeri.  
  
 `ppValue`  
 dışı Belirtilen yazmaç ve bellek konumunda depolanan alınan değeri temsil eden bir "ICorDebugValue" nesnesinin adresine yönelik bir işaretçi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
