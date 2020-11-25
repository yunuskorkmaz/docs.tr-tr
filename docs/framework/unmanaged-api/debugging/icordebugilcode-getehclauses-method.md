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
ms.openlocfilehash: 38936a57944e9a0920c374f473c4cbe8e8d70abb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728673"
---
# <a name="icordebugilcodegetehclauses-method"></a>ICorDebugILCode::GetEHClauses Metodu

[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]  
  
 Bu ara dil (IL) için tanımlanan özel durum işleme (EH) yan tümceleri listesine yönelik bir işaretçi döndürür.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp
HRESULT GetEHClauses(  
   [in] ULONG32 cClauses,  
   [out] ULONG32 * pcClauses,  
   [out, size_is(cClauses), length_is(*pcClauses)] CorDebugEHClause clauses[]);  
```  
  
## <a name="parameters"></a>Parametreler  

 `cClauses`  
 'ndaki Dizinin depolama kapasitesi `clauses` . Daha fazla bilgi için Açıklamalar bölümüne bakın.  
  
 `pcClauses`  
 dışı Hangi bilgilerin diziye yazıldığı hakkında yan tümceler sayısı `clauses` .  
  
 yan  
 dışı Bu Il için tanımlanan özel durum işleme yan tümceleri hakkında bilgi içeren bir [corhata ayıklama Gehclause](cordebugehclause-structure.md) nesneleri dizisi.  
  
## <a name="remarks"></a>Açıklamalar  

 `cClauses`0 ise ve `pcClauses` **null** değilse, `pcClauses` kullanılabilir özel durum işleme yan tümceleri sayısına ayarlanır. `cClauses`Sıfır olmayan ise, dizinin depolama kapasitesini temsil eder `clauses` . Yöntemi döndürüldüğünde, `clauses` en fazla `cClauses` öğe içerir ve `pcClauses` gerçekten diziye yazılan yan tümce sayısına ayarlanır `clauses` .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugILCode Arabirimi](icordebugilcode-interface.md)
- [CorDebugEHClause Yapısı](cordebugehclause-structure.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
