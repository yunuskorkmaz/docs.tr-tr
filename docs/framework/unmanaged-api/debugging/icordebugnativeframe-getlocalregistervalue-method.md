---
title: ICorDebugNativeFrame::GetLocalRegisterValue Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetLocalRegisterValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetLocalRegisterValue
helpviewer_keywords:
- GetLocalRegisterValue method [.NET Framework debugging]
- ICorDebugNativeFrame::GetLocalRegisterValue method [.NET Framework debugging]
ms.assetid: 5ccb74f3-f891-430c-b70a-e370624edde2
topic_type:
- apiref
ms.openlocfilehash: 132e0868426670ba61d8ee12ba7007be1a8a52de
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139400"
---
# <a name="icordebugnativeframegetlocalregistervalue-method"></a>ICorDebugNativeFrame::GetLocalRegisterValue Yöntemi
Bu yerel çerçeve için belirtilen kasada depolanan bir bağımsız değişkenin veya yerel değişkenin değerini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetLocalRegisterValue (  
    [in]  CorDebugRegister   reg,  
    [in]  ULONG              cbSigBlob,  
    [in]  PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `reg`  
 'ndaki Değeri içeren kaydı belirten "CorDebugRegister" numaralandırmasının değeri.  
  
 `cbSigBlob`  
 'ndaki `pvSigBlob` parametresi tarafından başvurulan ikili meta veri imzasının boyutunu belirten bir tamsayı.  
  
 `pvSigBlob`  
 'ndaki Değerin türünün ikili meta veri imzasına işaret eden bir `PCCOR_SIGNATURE` değeri.  
  
 `ppValue`  
 dışı Belirtilen kasada depolanan alınan değeri temsil eden bir "ICorDebugValue" nesnesinin adresine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetLocalRegisterValue` yöntemi yerel bir çerçevede veya bir tam zamanında (JıT) derlenmiş çerçevede kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
