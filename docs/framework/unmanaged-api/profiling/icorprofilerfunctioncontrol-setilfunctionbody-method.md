---
title: ICorProfilerFunctionControl::SetILFunctionBody Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionControl.SetILFunctionBody
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionControl::SetILFunctionBody
helpviewer_keywords:
- ICorProfilerFunctionControl::SetILFunctionBody method [.NET Framework profiling]
- SetILFunctionBody method, ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: 2c33f0f7-75b2-4c19-b2c7-c94b54997576
topic_type:
- apiref
ms.openlocfilehash: f6e2cfe47bdd212e39549544b06bf5b11033a956
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74429889"
---
# <a name="icorprofilerfunctioncontrolsetilfunctionbody-method"></a>ICorProfilerFunctionControl::SetILFunctionBody Yöntemi
Ortak Ara Dili (CIL) yönteminin gövdesinin yerini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT SetILFunctionBody(  
    [in]  ULONG   cbNewILMethodHeader,  
    [in, size_is(cbNewILMethodHeader)] LPCBYTE pbNewILMethodHeader);  
```  
  
## <a name="parameters"></a>Parametreler  
 `cbNewILMethodHeader`  
 [in] Üstbilgi ve gövdeden sonra gelen yapılar da dahil olmak üzere yeni CIL'in toplam boyutu.  
  
 `pbNewILMethodHeader`  
 [in] Yeni CIL üstbilgisi için bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem aşağıdaki özel HRESULT'ları döndürür.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Değişiklik başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 [ICorProfilerInfo:: SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) yönteminden farklı olarak `SetILFunctionBody` yöntemi, yenı CIL gövdesi için gereken belleği yönetir. Bu, profil oluşturucu tarafından sunulan CıL gövdesinin [IMethodMalloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md) arabirimi kullanılarak veya belirli bir Aralık içinde ayrılarak ayrılması gerekmediği anlamına gelir. Herhangi bir yığında ayrılabilir. Profil Oluşturucu, `SetILFunctionBody` döndüğünde, CıL gövdesi için kullanılan belleği serbest bırakabilirsiniz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerFunctionControl Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md)
