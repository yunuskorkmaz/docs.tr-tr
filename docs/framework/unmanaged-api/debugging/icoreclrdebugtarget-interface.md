---
title: ICoreClrDebugTarget Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICoreClrDebugTarget
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- ICoreClrDebugTarget
helpviewer_keywords:
- remote debugging API [Silverlight]
- ICorClrDebugTarget interface
- Silverlight, remote debugging
ms.assetid: 7cfaee76-e284-4a66-a431-8e33f0f60038
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 62d43121efbc039b8fad0b78bed7ec4a655efabb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icoreclrdebugtarget-interface"></a>ICoreClrDebugTarget Arabirimi
Başvuru sayıları denetlemek, işlemleri numaralandıran ve bir uzak Macintosh Silverlight hedefe bağlı bir hata ayıklayıcısı ile ilişkili belleği serbest yöntemleri sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
class ICoreClrDebugTarget {  
      HRESULT EnumProcesses (  
          [out] DWORD*                    pcProcs,  
          [out] CoreClrDebugProcInfo**    ppProcs  
      );  
  
      HRESULT EnumRuntimes (  
      [in]  DWORD                      dwInternalProcessID,  
      [out] DWORD*                     pcRuntimes,  
      [out] CoreClrDebugRuntimeInfo**  ppRuntimes  
      );  
  
      void FreeMemory (  
      [in] void*      pMemory  
    );  
};  
```  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[ICoreClrDebugTarget::EnumProcesses Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumprocesses-method.md)|Bir uzak bilgisayarda çalışan işlemler numaralandırır.|  
|[ICoreClrDebugTarget::EnumRuntimes Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumruntimes-method.md)|Ortak dil çalışma zamanları (CLRs), uzak bir bilgisayarda belirtilen işlemde numaralandırır.|  
|[ICoreClrDebugTarget::FreeMemory Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md)|Bu sınıf numaralandırma yöntemleri tarafından ayrılan belleği serbest bırakır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Şu anda bu işlevsellik yalnızca bir uzak Macintosh bilgisayarda çalışan Silverlight tabanlı uygulamaya hedef hata ayıklama için desteklenir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CoreClrRemoteDebuggingInterfaces.h  
  
 **Kitaplığı:** mscordbi_macx86.dll  
  
 **.NET framework sürümleri:** 3.5 SP1  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorDebugRemoteTarget Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)  
 [ICorDebug Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
    
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
