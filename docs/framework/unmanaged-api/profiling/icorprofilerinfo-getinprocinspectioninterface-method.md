---
title: ICorProfilerInfo::GetInprocInspectionInterface Metodu
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetInprocInspectionInterface
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetInprocInspectionInterface
helpviewer_keywords:
- GetInprocInspectionInterface method [.NET Framework profiling]
- ICorProfilerInfo::GetInprocInspectionInterface method [.NET Framework profiling]
ms.assetid: 22a92d1d-8849-4af6-8304-ecc53dd1d289
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0c4e2a094f018b4f77423b6dbfe990925632edf9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54683865"
---
# <a name="icorprofilerinfogetinprocinspectioninterface-method"></a>ICorProfilerInfo::GetInprocInspectionInterface Metodu
Sorgulanabilir bir nesne için bir "ICorDebugProcess" arabirimi alır. Bu yöntem .NET Framework 2.0 sürümünde artık kullanılmıyor.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetInprocInspectionInterface(  
    [out] IUnknown **ppicd);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppicd`  
 [Çıkış](/cpp/atl/iunknown) için sorgulanan nesne bir `ICorDebugProcess` arabirimi.  
  
## <a name="remarks"></a>Açıklamalar  
 .NET Framework sürüm 1.0 debugging işlemdeki sınırlı hata ayıklama API'si ortak dil çalışma zamanı (CLR) desteklenir. İşlem içi hata ayıklama, hata ayıklama API incelemesi bölümlerini kullanmak bir profil oluşturucu etkin. Müşteri geri bildirim sonucunda, işlemdeki hata ayıklama algıladı .NET Framework sürüm 2. 0'dan kaldırılmadığı ve profil oluşturma API'ayarlarına uygun olarak daha fazla işlevselliği kümesiyle değiştirildi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümü:** 1.0  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ICorProfilerInfo Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
