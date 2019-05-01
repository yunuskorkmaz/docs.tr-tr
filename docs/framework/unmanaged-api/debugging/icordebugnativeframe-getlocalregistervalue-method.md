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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f53c8290271391e52176f8364b592ce6b46faf71
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61994637"
---
# <a name="icordebugnativeframegetlocalregistervalue-method"></a>ICorDebugNativeFrame::GetLocalRegisterValue Yöntemi
Bir bağımsız değişken veya yerel bu çerçeve için belirtilen kayıt defterinde depolanan yerel değişken değerini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetLocalRegisterValue (  
    [in]  CorDebugRegister   reg,  
    [in]  ULONG              cbSigBlob,  
    [in]  PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `reg`  
 [in] "CorDebugRegister" numaralandırma değerini içeren kayıt belirten bir değer.  
  
 `cbSigBlob`  
 [in] Tarafından başvurulan ikili meta veri imzası boyutunu belirten bir tamsayı `pvSigBlob` parametresi.  
  
 `pvSigBlob`  
 [in] A `PCCOR_SIGNATURE` değerin türü. ikili meta verileri imza işaret eden bir değer.  
  
 `ppValue`  
 [out] Belirtilen kayıt defterinde depolanan alınan değeri temsil eden bir "ICorDebugValue" nesnenin adresi için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetLocalRegisterValue` Yöntemi, bir yerel çerçeve veya bir tam zamanında (JIT) kullanılabilir-çerçeve derlenir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
