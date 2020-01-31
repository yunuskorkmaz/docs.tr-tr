---
title: ICorProfilerInfo::GetInprocInspectionIThisThread Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetInprocInspectionIThisThread
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetInprocInspectionIThisThread
helpviewer_keywords:
- ICorProfilerInfo::GetInprocInspectionIThisThread method [.NET Framework profiling]
- GetInprocInspectionIThisThread method [.NET Framework profiling]
ms.assetid: badddccd-f85c-416e-9f0f-419eab2c9d42
topic_type:
- apiref
ms.openlocfilehash: 0ab383f0968061667b3580a2058687eecda99dde
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76870048"
---
# <a name="icorprofilerinfogetinprocinspectionithisthread-method"></a>ICorProfilerInfo::GetInprocInspectionIThisThread Yöntemi
ICorDebugThread arabirimi için sorgulanabilen bir nesne alır. Bu yöntem .NET Framework sürüm 2,0 ' de kullanılmıyor.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetInprocInspectionIThisThread(  
    [out] IUnknown **ppicd);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ppicd`  
 `ICorDebugThread` arabirimi için sorgulanabilen [Çıkış](/cpp/atl/iunknown) nesnesi.  
  
## <a name="remarks"></a>Açıklamalar  
 Ortak dil çalışma zamanı (CLR) hata ayıklama Hizmetleri, .NET Framework sürüm 1,0 ' de sınırlı sayıda işlem hata ayıklamayı destekliyordu. İşlem içi hata ayıklama, hata ayıklama API 'sinin İnceleme kısımlarını kullanmak için bir profil oluşturucu etkinleştirdi. Müşteri geri bildirimlerinden kaynaklanan işlem içi hata ayıklama, 2,0 sürümündeki .NET Framework kaldırılmıştır ve profil oluşturma API 'SI ile birlikte daha fazla bir işlev kümesiyle değiştirilmiştir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümü:** 1,0  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](icorprofilerinfo-interface.md)
