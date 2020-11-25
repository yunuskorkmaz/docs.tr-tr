---
title: ICorProfilerInfo::GetHandleFromThread Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetHandleFromThread
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetHandleFromThread
helpviewer_keywords:
- GetHandleFromThread method [.NET Framework profiling]
- ICorProfilerInfo::GetHandleFromThread method [.NET Framework profiling]
ms.assetid: 36cdc9f5-7579-4cd2-aa36-fc05c741584c
topic_type:
- apiref
ms.openlocfilehash: 632a9070eab227bc48ce76c51ea08f98060d680d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722551"
---
# <a name="icorprofilerinfogethandlefromthread-method"></a>ICorProfilerInfo::GetHandleFromThread Yöntemi

Bir iş parçacığının KIMLIĞINI bir Win32 iş parçacığı tanıtıcısına eşler.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetHandleFromThread(  
    [in]  ThreadID threadId,  
    [out] HANDLE  *phThread);  
```  
  
## <a name="parameters"></a>Parametreler  

 `threadId`  
 'ndaki Eşleştirilecek iş parçacığı KIMLIĞI.  
  
 `phThread`  
 dışı Win32 iş parçacığı tanıtıcısına yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  

 Profil oluşturucunun kullanılmadan `DuplicateHandle` önce tanıtıcıda Win32 işlevini çağırması gerekir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](icorprofilerinfo-interface.md)
