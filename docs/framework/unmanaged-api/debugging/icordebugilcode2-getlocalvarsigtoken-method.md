---
title: ICorDebugILCode2::GetLocalVarSigToken Metodu
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILCode2.GetLocalVarSigToken
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 17665b77-1342-4115-94fd-9f45b0ecfb0f
topic_type:
- apiref
ms.openlocfilehash: 243000a2399b4938a3ad7f732c64e2f79b664f51
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131053"
---
# <a name="icordebugilcode2getlocalvarsigtoken-method"></a>ICorDebugILCode2::GetLocalVarSigToken Metodu
[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]  
  
 Bu örnek tarafından temsil edilen işlev için yerel değişken imzasının meta veri belirtecini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetLocalVarSigToken(  
   [out] mdSignature *pmdSig  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pmdSig`  
 dışı Bu işlev için yerel değişken imzasının `mdSignature` belirtecine yönelik bir işaretçi veya imza yoksa (işlevin herhangi bir yerel değişken yoksa) `mdSignatureNil`.  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugILCode2 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-interface.md)
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
