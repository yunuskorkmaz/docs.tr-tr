---
title: ICorDebugILCode::GetEHClauses Metodu
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILCode.GetEHClauses
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: cf7a0e00-06ae-47a5-8037-598b26196802
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6e890629f307e3d3cff11dabdb2db90a5e88ece5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61995559"
---
# <a name="icordebugilcodegetehclauses-method"></a>ICorDebugILCode::GetEHClauses Metodu
[.NET Framework 4.5.2 ve sonraki sürümlerinde desteklenen]  
  
 Özel durum işleme bu Ara dil (IL) için tanımlanan (EH) yan tümceleri listesine bir işaretçi döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetEHClauses(  
   [in] ULONG32 cClauses,  
   [out] ULONG32 * pcClauses,  
   [out, size_is(cClauses), length_is(*pcClauses)] CorDebugEHClause clauses[]);  
```  
  
## <a name="parameters"></a>Parametreler  
 `cClauses`  
 [in] Depolama kapasitesini `clauses` dizisi. Daha fazla bilgi için Açıklamalar bölümüne bakın.  
  
 `pcClauses`  
 [out] Hangi bilgilerin yazıldığını için yan tümceler sayısını `clauses` dizisi.  
  
 Yan tümceleri  
 [out] Bir dizi [CorDebugEHClause](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md) özel durum işleme için bu IL tanımlanan yan tümceleri hakkında bilgi içeren nesne.  
  
## <a name="remarks"></a>Açıklamalar  
 Varsa `cClauses` 0'dır ve `pcClauses` olan olmayan**null**, `pcClauses` kullanılabilir özel durum yan tümceleri işleme sayısını ayarlayın. Varsa `cClauses` sıfır olan depolama kapasitesini temsil ettiği `clauses` dizisi. Yöntem döndürüldüğünde `clauses` en çok içeren `cClauses` öğeleri ve `pcClauses` gerçekte yazılan yan tümceleri sayısına ayarlayın `clauses` dizisi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugILCode Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md)
- [CorDebugEHClause Yapısı](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md)
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
