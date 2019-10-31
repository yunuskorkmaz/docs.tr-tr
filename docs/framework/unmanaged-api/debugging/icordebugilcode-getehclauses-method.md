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
ms.openlocfilehash: df9859f33b4146486a046253cf4705cd19c66adf
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131089"
---
# <a name="icordebugilcodegetehclauses-method"></a>ICorDebugILCode::GetEHClauses Metodu
[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]  
  
 Bu ara dil (IL) için tanımlanan özel durum işleme (EH) yan tümceleri listesine yönelik bir işaretçi döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetEHClauses(  
   [in] ULONG32 cClauses,  
   [out] ULONG32 * pcClauses,  
   [out, size_is(cClauses), length_is(*pcClauses)] CorDebugEHClause clauses[]);  
```  
  
## <a name="parameters"></a>Parametreler  
 `cClauses`  
 'ndaki `clauses` dizisinin depolama kapasitesi. Daha fazla bilgi için Açıklamalar bölümüne bakın.  
  
 `pcClauses`  
 dışı `clauses` dizisine hangi bilgilerin yazıldığı hakkında yan tümceler sayısı.  
  
 yan  
 dışı Bu Il için tanımlanan özel durum işleme yan tümceleri hakkında bilgi içeren bir [corhata ayıklama Gehclause](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md) nesneleri dizisi.  
  
## <a name="remarks"></a>Açıklamalar  
 `cClauses` 0 ise ve `pcClauses`**null**değilse, `pcClauses` kullanılabilir özel durum işleme yan tümceleri sayısına ayarlanır. Sıfır olmayan `cClauses`, `clauses` dizisinin depolama kapasitesini temsil eder. Yöntemi döndürüldüğünde, `clauses` en fazla `cClauses` öğesi içerir ve `pcClauses` aslında `clauses` dizisine yazılmış yan tümce sayısına ayarlanır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugILCode Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md)
- [CorDebugEHClause Yapısı](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md)
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
