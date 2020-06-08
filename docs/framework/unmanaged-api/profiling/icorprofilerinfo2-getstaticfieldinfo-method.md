---
title: ICorProfilerInfo2::GetStaticFieldInfo Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetStaticFieldInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetStaticFieldInfo
helpviewer_keywords:
- ICorProfilerInfo2::GetStaticFieldInfo method [.NET Framework profiling]
- GetStaticFieldInfo method [.NET Framework profiling]
ms.assetid: fc663e76-e23f-49a8-bdd5-52cdf1a3b2b3
topic_type:
- apiref
ms.openlocfilehash: e1dd6addd9053ffb6cf2ce23408673d8fca17cb5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496847"
---
# <a name="icorprofilerinfo2getstaticfieldinfo-method"></a>ICorProfilerInfo2::GetStaticFieldInfo Yöntemi
Belirtilen alan için geçerli olan statik türünü gösteren bir değer alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetStaticFieldInfo (  
    [in] ClassID               classId,  
    [in] mdFieldDef            fieldToken,  
    [out] COR_PRF_STATIC_TYPE  *pFieldInfo);  
```  
  
## <a name="parameters"></a>Parametreler  
 `classId`  
 'ndaki Statik alanın tanımlandığı sınıfın KIMLIĞI.  
  
 `fieldToken`  
 'ndaki Statik alan için meta veri belirteci.  
  
 `pFieldInfo`  
 dışı Belirtilen alanın statik olup olmadığını belirten [COR_PRF_STATIC_TYPE](cor-prf-static-type-enumeration.md) sabit değerinin bir işaretçisi ve bu durumda, alan için geçerli olan statik türü.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu bilgiler, statik alanın adresini almak için hangi işlevin çağrılacağını belirlemede kullanılabilir.  
  
 Profil Oluşturucu kodu, gerçekten bir adresi olduğundan emin olmak için statik bir alana ait meta verileri denetlemelidir. Statik sabit değerler (diğer bir deyişle, sabitler) yalnızca meta verilerde bulunur ve bir adrese sahip değildir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 Arabirimi](icorprofilerinfo2-interface.md)
