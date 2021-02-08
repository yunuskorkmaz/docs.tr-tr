---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugILCode2:: GetLocalVarSigToken yöntemi'
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
ms.openlocfilehash: cdf2725274a132528123534ddd36ae95e265af44
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791432"
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
 dışı `mdSignature` Bu işlev için yerel değişken imzasının belirtecine yönelik bir işaretçi veya `mdSignatureNil` imza yoksa (işlev herhangi bir yerel değişken içermiyorsa).  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugILCode2 Arabirimi](icordebugilcode2-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
