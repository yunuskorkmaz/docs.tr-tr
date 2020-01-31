---
title: ICoreClrDebugTarget Arabirimi
ms.date: 03/30/2017
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
ms.openlocfilehash: 190671b4f690f8c2cad43cf446a1196985ec5a42
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790748"
---
# <a name="icoreclrdebugtarget-interface"></a>ICoreClrDebugTarget Arabirimi
Başvuru sayılarını denetleyen, işlem numaralandırmakta olan ve uzak bir Macintosh Silverlight hedefine bağlı bir hata ayıklayıcı ile ilişkili belleği serbest alan yöntemler sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
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
|[ICoreClrDebugTarget::EnumProcesses Yöntemi](icoreclrdebugtarget-enumprocesses-method.md)|Uzak bir bilgisayarda çalışan işlemi numaralandırır.|  
|[ICoreClrDebugTarget::EnumRuntimes Yöntemi](icoreclrdebugtarget-enumruntimes-method.md)|Uzak bilgisayardaki belirtilen işlemdeki ortak dil çalışma zamanlarını (CLRs) numaralandırır.|  
|[ICoreClrDebugTarget::FreeMemory Yöntemi](icoreclrdebugtarget-freememory-method.md)|Bu sınıftaki sabit listesi yöntemleriyle ayrılan belleği serbest bırakır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Şu anda bu işlev yalnızca uzak bir Macintosh bilgisayarda çalışan Silverlight tabanlı bir uygulama hedefinde hata ayıklama için desteklenir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CoreClrRemoteDebuggingInterfaces. h  
  
 **Kitaplık:** mscordbi_macx86. dll  
  
 **.NET Framework sürümleri:** 3,5 SP1  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugRemoteTarget Arabirimi](icordebugremotetarget-interface.md)
- [ICorDebug Arabirimi](icordebug-interface.md)

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
