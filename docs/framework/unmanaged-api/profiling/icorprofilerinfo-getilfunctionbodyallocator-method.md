---
title: ICorProfilerInfo::GetILFunctionBodyAllocator Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetILFunctionBodyAllocator
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetILFunctionBodyAllocator
helpviewer_keywords:
- GetILFunctionBodyAllocator method [.NET Framework profiling]
- ICorProfilerInfo::GetILFunctionBodyAllocator method [.NET Framework profiling]
ms.assetid: 5da1bf3d-dddf-4892-b266-578ee54d570b
topic_type:
- apiref
ms.openlocfilehash: 5fe472c4a0053ec9e37d7d61ffde5cf21d65dd2f
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76863524"
---
# <a name="icorprofilerinfogetilfunctionbodyallocator-method"></a>ICorProfilerInfo::GetILFunctionBodyAllocator Yöntemi
Microsoft ara dili (MSIL) kodundaki bir yöntemin gövdesini değiştirmek için kullanılacak belleği ayırmak üzere bir yöntemi sağlayan bir arabirim alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetILFunctionBodyAllocator(  
    [in]  ModuleID      moduleId,  
    [out] IMethodMalloc **ppMalloc);  
```  
  
## <a name="parameters"></a>Parametreler  
 `moduleId`  
 'ndaki Yöntemin bulunduğu modülün KIMLIĞI.  
  
 `ppMalloc`  
 dışı Belleği ayırmak için bir yöntem sağlayan bir [IMethodMalloc](imethodmalloc-interface.md) arabirimine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 MSIL kodundaki bir yöntem gövdesi, yüklenen modüle göre, bir göreli sanal adres (RVA) olarak yerleştirilmelidir, bu da modülün 4 GB dahilinde izlediği anlamına gelir. Bir aracın bir yöntemin gövdesini takas edilmesini kolaylaştırmak için `GetILFunctionBodyAllocator` yöntemi belleğin bu Aralık içinde ayrılmasını sağlar.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](icorprofilerinfo-interface.md)
