---
title: ICorDebugProcess::GetHelperThreadID Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess.GetHelperThreadID
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess::GetHelperThreadID
helpviewer_keywords:
- GetHelperThreadID method [.NET Framework debugging]
- ICorDebugProcess::GetHelperThreadID method [.NET Framework debugging]
ms.assetid: 84e1e605-37c1-49a5-8e12-35db85654622
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 092e99cb1d5534cee56db08b5a2eedaaa2fc4724
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugprocessgethelperthreadid-method"></a>ICorDebugProcess::GetHelperThreadID Metodu
Hata Ayıklayıcı'nın iç yardımcı iş parçacığı işletim sistemi (OS) iş parçacığı kimliği alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetHelperThreadID (  
    [out] DWORD *pThreadID  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pThreadID`  
 [out] İşletim sistemi için bir işaretçi iş parçacığı Hata Ayıklayıcı'nın iç yardımcı iş parçacığı kimliği.  
  
## <a name="remarks"></a>Açıklamalar  
 Yönetilen ve yönetilmeyen hata ayıklama sırasında hata ayıklayıcı tarafından yerleştirilen bir kesme noktası değerse, iş parçacığı belirtilen kimliği ile çalışan kaldığından emin olmak için hata ayıklayıcı'nın sorumluluğundadır. Bir hata ayıklayıcısı da kullanıcının bu iş parçacığından Gizle isteyebilirsiniz. Hiçbir Yardımcısı iş parçacığı işleminde henüz varsa `GetHelperThreadID` yöntemi döndürür sıfır *`pThreadID`.  
  
 Zaman içinde değişebilir olduğundan Yardımcısı iş parçacığı, iş parçacığı kimliği önbelleğe alamıyor. İş parçacığı kimliği her durdurma olay yeniden sorgulaması gerekir.  
  
 Hata Ayıklayıcı'nın Yardımcısı iş parçacığı iş parçacığı kimliği üzerinde doğru her yönetilmeyen [Icordebugmanagedcallback::CreateThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md) olay, böylece kendi Yardımcısı iş parçacığı iş parçacığı Kimliğini belirlemek ve kullanıcıdan gizlemek bir hata ayıklayıcısı sağlar. Bir yardımcı iş parçacığı yönetilmeyen sırasında tanımlanan bir iş parçacığı `ICorDebugManagedCallback::CreateThread` olay asla yönetilen kullanıcı kodu çalışmaz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl. CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
