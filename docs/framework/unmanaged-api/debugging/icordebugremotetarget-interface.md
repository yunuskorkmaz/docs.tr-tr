---
title: ICorDebugRemoteTarget Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugRemoteTarget
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemoteTarget
helpviewer_keywords:
- ICorDebugRemoteTarget interface [.NET Framework debugging]
ms.assetid: bd9936a6-cc24-4869-8761-0988664464e6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ae31506d4ba34bf262f49bc2321c6cfcd30f1b60
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59197327"
---
# <a name="icordebugremotetarget-interface"></a>ICorDebugRemoteTarget Arabirimi
Geliştiricilerin ortak dil çalışma zamanı (CLR) ortamında Silverlight tabanlı uygulamaların hatalarını ayıklamalarına olanak tanıyan yöntemler sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
interface ICorDebugRemoteTarget  : IUnknown  
{  
    HRESULT GetHostName (  
        [in]  ULONG32                    cchHostName,  
        [out] ULONG32*                   pcchHostName,  
        [out, size_is(cchHostName),  
              length_is(*pcchHostName)]  
                  WCHAR szHostName[]  
        );  
};  
```  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[ICorDebugRemoteTarget::GetHostName Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-gethostname-method.md)|Ana bilgisayar adı veya uzak bir makinenin IP adresini döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  
 Karma mod (diğer bir deyişle, yönetilen ve yerel kod) hata ayıklaması, Windows 95, Windows 98 veya Windows ME veya x86 olmayan platformları (örn. IA-64 ve AMD64 gibi) üzerinde desteklenmiyor.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl  
  
 **Kitaplığı:** : CorGuids.lib  
  
 **.NET framework sürümleri:** 3.5 SP1  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugRemote Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)
- [ICorDebug Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
