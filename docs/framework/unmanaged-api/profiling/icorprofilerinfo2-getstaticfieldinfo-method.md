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
ms.openlocfilehash: e74bab058adda759db1fb549022608eedfef5d80
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432980"
---
# <a name="icorprofilerinfo2getstaticfieldinfo-method"></a>ICorProfilerInfo2::GetStaticFieldInfo Yöntemi
Belirtilen alan için geçerli olan statik türünü gösteren bir değer alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
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
 dışı Belirtilen alanın statik olup olmadığını belirten [COR_PRF_STATIC_TYPE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-static-type-enumeration.md) sabit değerinin bir işaretçisi ve bu durumda, alan için geçerli olan statik türü.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu bilgiler, statik alanın adresini almak için hangi işlevin çağrılacağını belirlemede kullanılabilir.  
  
 Profil Oluşturucu kodu, gerçekten bir adresi olduğundan emin olmak için statik bir alana ait meta verileri denetlemelidir. Statik sabit değerler (diğer bir deyişle, sabitler) yalnızca meta verilerde bulunur ve bir adrese sahip değildir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
