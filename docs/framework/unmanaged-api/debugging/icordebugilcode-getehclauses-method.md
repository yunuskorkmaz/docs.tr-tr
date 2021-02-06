---
description: 'Şu konuda daha fazla bilgi edinin: ıcordebugilcode:: Getehtümceleri yöntemi'
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
ms.openlocfilehash: e790f0f1f69a38d3a1be9e98eacfc5e37be0fd05
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99660667"
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
