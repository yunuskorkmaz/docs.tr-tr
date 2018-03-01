---
title: ICorDebugILCode2::GetLocalVarSigToken Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 47004375194438b1ef0aaf61144ba6f16278545b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilcode2getlocalvarsigtoken-method"></a>ICorDebugILCode2::GetLocalVarSigToken Metodu
[.NET Framework 4.5.2 ve sonraki sürümlerinde desteklenen]  
  
 Meta veriler bu örneği tarafından temsil edilen işlevi için yerel değişken İmza belirteci alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetLocalVarSigToken(  
   [out] mdSignature *pmdSig  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pmdSig`  
 [out] Bir işaretçi `mdSignature` bu işlev için yerel değişken imza için belirteç veya `mdSignatureNil` olup olmadığını hiç imza (diğer bir deyişle, işlev yerel değişkenlerin yoksa).  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorDebugILCode2 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-interface.md)  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
