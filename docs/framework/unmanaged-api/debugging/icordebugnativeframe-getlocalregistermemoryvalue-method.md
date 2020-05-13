---
title: ICorDebugNativeFrame::GetLocalRegisterMemoryValue Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetLocalRegisterMemoryValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetLocalRegisterMemoryValue
helpviewer_keywords:
- ICorDebugNativeFrame::GetLocalRegisterMemoryValue method [.NET Framework debugging]
- GetLocalRegisterMemoryValue method [.NET Framework debugging]
ms.assetid: d350f69d-9aff-4f5a-8301-daea22dee2da
topic_type:
- apiref
ms.openlocfilehash: f16150ad7d9ecec4b4aceee5c9266e9a7859f1cb
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213302"
---
# <a name="icordebugnativeframegetlocalregistermemoryvalue-method"></a>ICorDebugNativeFrame::GetLocalRegisterMemoryValue Yöntemi
Bir bağımsız değişkenin veya yerel değişkenin değerini alır; bu, alt sözcük ve üst sözcük, bu yerel çerçeve için sırasıyla bellek konumunda ve belirtilen yazmaç üzerinde depolanır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetLocalRegisterMemoryValue (  
    [in] CorDebugRegister   highWordReg,  
    [in] CORDB_ADDRESS      lowWordAddress,  
    [in] ULONG              cbSigBlob,  
    [in] PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `highWordReg`  
 'ndaki Değerin yüksek sözcüğünü içeren kaydı belirten "CorDebugRegister" numaralandırmasının değeri.  
  
 `lowWordAddress`  
 'ndaki `CORDB_ADDRESS`Değerin düşük sözcüğünü içeren bellek konumunu belirten bir değer.  
  
 `cbSigBlob`  
 'ndaki Parametresi tarafından başvurulan ikili meta veri imzasının boyutunu belirten bir tamsayı `pvSigBlob` .  
  
 `pvSigBlob`  
 'ndaki `PCCOR_SIGNATURE`Değerin türünün ikili meta veri imzasına işaret eden bir değer.  
  
 `ppValue`  
 dışı Belirtilen yazmaç ve bellek konumunda depolanan alınan değeri temsil eden bir "ICorDebugValue" nesnesinin adresine yönelik bir işaretçi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
