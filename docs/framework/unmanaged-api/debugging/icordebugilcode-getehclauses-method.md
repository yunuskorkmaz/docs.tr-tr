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
ms.openlocfilehash: ac9a4e4b54b302afeae4ede1dd574c15ded3ff12
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788608"
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
 dışı Bu Il için tanımlanan özel durum işleme yan tümceleri hakkında bilgi içeren bir [corhata ayıklama Gehclause](cordebugehclause-structure.md) nesneleri dizisi.  
  
## <a name="remarks"></a>Açıklamalar  
 `cClauses` 0 ise ve `pcClauses`**null**değilse, `pcClauses` kullanılabilir özel durum işleme yan tümceleri sayısına ayarlanır. Sıfır olmayan `cClauses`, `clauses` dizisinin depolama kapasitesini temsil eder. Yöntemi döndürüldüğünde, `clauses` en fazla `cClauses` öğesi içerir ve `pcClauses` aslında `clauses` dizisine yazılmış yan tümce sayısına ayarlanır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugILCode Arabirimi](icordebugilcode-interface.md)
- [CorDebugEHClause Yapısı](cordebugehclause-structure.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
