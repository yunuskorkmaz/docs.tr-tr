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
ms.openlocfilehash: a45061b6a3105565fdbb36173731b3c3dfe5aa4f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137291"
---
# <a name="icordebugnativeframegetlocaldoubleregistervalue-method"></a>ICorDebugNativeFrame::GetLocalDoubleRegisterValue Yöntemi
Bu yerel çerçeve için belirtilen iki kasada depolanan bir bağımsız değişkenin veya yerel değişkenin değerini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
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
 'ndaki Değerin yüksek sözcüğünü içeren kaydı belirten "CorDebugRegister" numaralandırmasının değeri.  
  
 `lowWordReg`  
 'ndaki Değerin düşük sözcüğünü içeren kaydı belirten `CorDebugRegister` numaralandırması değeri.  
  
 `cbSigBlob`  
 'ndaki `pvSigBlob` parametresi tarafından başvurulan ikili meta veri imzasının boyutunu belirten bir tamsayı.  
  
 `pvSigBlob`  
 'ndaki Değerin türünün ikili meta veri imzasına işaret eden bir `PCCOR_SIGNATURE` değeri.  
  
 `ppValue`  
 dışı Belirtilen kayıtlarda depolanan alınan değeri temsil eden bir "ICorDebugValue" nesnesinin adresine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetLocalDoubleRegisterValue` yöntemi yerel bir çerçevede veya bir tam zamanında (JıT) derlenmiş çerçevede kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
