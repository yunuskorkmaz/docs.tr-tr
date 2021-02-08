---
description: ': ICorProfilerFunctionControl:: SetILFunctionBody yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 470eefce5b211adcfd111951be9a004b3bd7d8fc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781616"
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
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|Değişiklik başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  

 [ICorProfilerInfo:: SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md) yönteminden farklı olarak, `SetILFunctionBody` yöntemi yeni CIL gövdesi için gereken belleği yönetir. Bu, profil oluşturucu tarafından sunulan CıL gövdesinin [IMethodMalloc](imethodmalloc-interface.md) arabirimi kullanılarak veya belirli bir Aralık içinde ayrılarak ayrılması gerekmediği anlamına gelir. Herhangi bir yığında ayrılabilir. Profil Oluşturucu, döndürüldüğünden CıL gövdesi için kullanılan belleği serbest bırakabilirsiniz `SetILFunctionBody` .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerFunctionControl Arabirimi](icorprofilerfunctioncontrol-interface.md)
