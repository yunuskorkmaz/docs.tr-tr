---
title: ICorProfilerInfo::GetILFunctionBodyAllocator Metodu
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0ae8b209ad03594cb77029193b0e9dec773a6e02
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54603332"
---
# <a name="icorprofilerinfogetilfunctionbodyallocator-method"></a>ICorProfilerInfo::GetILFunctionBodyAllocator Metodu
Bir yöntem gövdesi bir yöntemin Microsoft Ara dil (MSIL) kodu değiştirme için kullanılacak bellek ayırmak için sağlayan bir arabirimi alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetILFunctionBodyAllocator(  
    [in]  ModuleID      moduleId,  
    [out] IMethodMalloc **ppMalloc);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `moduleId`  
 [in] Yöntem bulunduğu modül kimliği.  
  
 `ppMalloc`  
 [out] Bir işaretçi bir [Imethodmalloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md) arabirimi bellek ayırmak için bir yöntem sağlar.  
  
## <a name="remarks"></a>Açıklamalar  
 MSIL kodunun bir yöntem gövdesinde bir göreli sanal adres (RVA) göre 4 GB içinde modül izlediğini anlamına gelir yüklenen modül olarak yer almalıdır. Bir yöntem gövdesi takas etmek bir araç kolaylaştırmak için `GetILFunctionBodyAllocator` yöntemi sağlar, bellek bu aralıkta ayrılır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ICorProfilerInfo Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
