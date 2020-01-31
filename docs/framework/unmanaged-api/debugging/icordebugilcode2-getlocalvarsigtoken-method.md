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
ms.openlocfilehash: 3759cfa330ac37d2ed62a0b8bb70b5e10cd9d12e
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782453"
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

- [ICorDebugILCode2 Arabirimi](icordebugilcode2-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
