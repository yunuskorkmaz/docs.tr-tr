---
title: ICorDebugRemote Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugRemote
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemote
helpviewer_keywords:
- ICorDebugRemote interface [.NET Framework debugging]
ms.assetid: 53d073c6-fa02-40d2-82e1-b9452bb6abaa
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ab8ed5c4fa3dc0ed77c1948aa6c1b940ecc25c14
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421457"
---
# <a name="icordebugremote-interface"></a>ICorDebugRemote Arabirimi
Yönetilen bir hata ayıklayıcıyı uzak hedef işleminde başlatma veya ekleme özelliği sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
interface ICorDebugRemote : IUnknown  
{  
    HRESULT CreateProcessEx  
      (  
      [in] ICorDebugRemoteTarget *     pRemoteTarget,  
      [in] LPCWSTR                     lpApplicationName,  
      [in] LPWSTR                      lpCommandLine,  
      [in] LPSECURITY_ATTRIBUTES       lpProcessAttributes,  
      [in] LPSECURITY_ATTRIBUTES       lpThreadAttributes,  
      [in] BOOL                        bInheritHandles,  
      [in] DWORD                       dwCreationFlags,  
      [in] PVOID                       lpEnvironment,  
      [in] LPCWSTR                     lpCurrentDirectory,  
      [in] LPSTARTUPINFOW              lpStartupInfo,  
      [in] LPPROCESS_INFORMATION       lpProcessInformation,  
      [in] CorDebugCreateProcessFlags  debuggingFlags,  
      [out] ICorDebugProcess **        ppProcess  
      );  
  
    HRESULT DebugActiveProcessEx  
      (  
      [in] ICorDebugRemoteTarget *   pRemoteTarget,  
      [in] DWORD                     dwProcessId,  
      [in] BOOL                      fWin32Attach,  
      [out] ICorDebugProcess **      ppProcess  
      );  
};  
```  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[ICorDebugRemote::CreateProcessEx Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-createprocessex-method.md)|Yönetilen hata ayıklama için bir işlemi uzak makinede oluşturur.|  
|[ICorDebugRemote::DebugActiveProcessEx Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-debugactiveprocessex-method.md)|Hata ayıklayıcı altında uzaktaki bir makinede bir işlem başlatır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Şu anda bu işlevsellik yalnızca bir uzak Macintosh makine üzerinde çalışan Silverlight tabanlı uygulamaya hedef hata ayıklama için desteklenir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** 4.5, 4, 3.5 SP1  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorDebugRemoteTarget Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)  
 [ICorDebug Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
    
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
