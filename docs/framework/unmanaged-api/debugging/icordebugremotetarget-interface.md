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
ms.openlocfilehash: bab6b7f683b5563cf362366dfb007f83caeee12d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791932"
---
# <a name="icordebugremotetarget-interface"></a>ICorDebugRemoteTarget Arabirimi
Geliştiricilerin, ortak dil çalışma zamanı (CLR) ortamında Silverlight tabanlı uygulamalarda hata ayıklamalarına olanak tanıyan yöntemler sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
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
|[ICorDebugRemoteTarget::GetHostName Yöntemi](icordebugremotetarget-gethostname-method.md)|Uzak makinenin ana bilgisayar adını veya IP adresini döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  
 Karma mod (yani, yönetilen ve yerel kod) hata ayıklaması Windows 95, Windows 98 veya Windows ME 'de veya x86 olmayan platformlarda (IA-64 ve AMD64 gibi) desteklenmez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL  
  
 **Library:** : corguid. lib  
  
 **.NET Framework sürümleri:** 3,5 SP1  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugRemote Arabirimi](icordebugremote-interface.md)
- [ICorDebug Arabirimi](icordebug-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
