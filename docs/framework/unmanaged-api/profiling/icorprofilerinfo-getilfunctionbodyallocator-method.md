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
ms.openlocfilehash: 967f38add9ae5996c6ac33388203b55161a84e39
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84498277"
---
# <a name="icorprofilerinfogetilfunctionbodyallocator-method"></a>ICorProfilerInfo::GetILFunctionBodyAllocator Yöntemi
Microsoft ara dili (MSIL) kodundaki bir yöntemin gövdesini değiştirmek için kullanılacak belleği ayırmak üzere bir yöntemi sağlayan bir arabirim alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
 MSIL kodundaki bir yöntem gövdesi, yüklenen modüle göre, bir göreli sanal adres (RVA) olarak yerleştirilmelidir, bu da modülün 4 GB dahilinde izlediği anlamına gelir. Bir aracın bir Yöntem gövdesinin ölçeğini daha kolay hale getirmek için `GetILFunctionBodyAllocator` yöntemi, belleğin bu Aralık içinde ayrılmasını sağlar.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](icorprofilerinfo-interface.md)
