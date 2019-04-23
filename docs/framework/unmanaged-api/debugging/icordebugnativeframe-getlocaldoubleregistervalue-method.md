---
title: ICorDebugNativeFrame::GetLocalDoubleRegisterValue Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetLocalDoubleRegisterValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetLocalDoubleRegisterValue
helpviewer_keywords:
- ICorDebugNativeFrame::GetLocalDoubleRegisterValue method [.NET Framework debugging]
- GetLocalDoubleRegisterValue method [.NET Framework debugging]
ms.assetid: 1f838215-ac8a-434f-8ce6-03021d3098d9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 13e1e3369c4e7a185c2167facc8514b5cfc85a85
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59115875"
---
# <a name="icordebugnativeframegetlocaldoubleregistervalue-method"></a>ICorDebugNativeFrame::GetLocalDoubleRegisterValue Yöntemi
Bir bağımsız değişken veya yerel bu çerçeve için iki belirtilen kaydeder depolanan yerel değişken değerini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetLocalDoubleRegisterValue (  
    [in] CorDebugRegister   highWordReg,  
    [in] CorDebugRegister   lowWordReg,  
    [in] ULONG              cbSigBlob,  
    [in] PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `highWordReg`  
 [in] "CorDebugRegister" numaralandırma değeri yüksek sözcüğünü içeren kayıt belirten bir değer.  
  
 `lowWordReg`  
 [in] Değerini `CorDebugRegister` değerinin düşük sözcüğünü içeren kayıt belirten sabit listesi.  
  
 `cbSigBlob`  
 [in] Tarafından başvurulan ikili meta veri imzası boyutunu belirten bir tamsayı `pvSigBlob` parametresi.  
  
 `pvSigBlob`  
 [in] A `PCCOR_SIGNATURE` değerin türü. ikili meta verileri imza işaret eden bir değer.  
  
 `ppValue`  
 [out] Belirtilen kayıtlara depolanan alınan değeri temsil eden bir "ICorDebugValue" nesnenin adresi için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetLocalDoubleRegisterValue` Yöntemi, bir yerel çerçeve veya bir tam zamanında (JIT) kullanılabilir-çerçeve derlenir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
