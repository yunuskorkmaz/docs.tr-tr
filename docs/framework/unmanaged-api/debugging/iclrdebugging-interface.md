---
title: ICLRDebugging Arabirimi
ms.date: 03/30/2017
api_name:
- ICLRDebugging
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebugging
helpviewer_keywords:
- ICLRDebugging interface [.NET Framework debugging]
ms.assetid: 429d8fce-b1b1-49d7-895c-28c1c1aa2dbd
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c6edee34c8560c989040475fee4a35c6bd2ddb3e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59155720"
---
# <a name="iclrdebugging-interface"></a>ICLRDebugging Arabirimi
Hata ayıklama amacıyla modülleri yükleme ve kaldırma işlemlerini yapan yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[OpenVirtualProcess Yöntemi](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md)|Bir ortak dil çalışma zamanı (CLR) modülüne işleme yüklendiğinde karşılık gelen "ICorDebugProcess" arabirimini alır.|  
|[CanUnloadNow Yöntemi](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-canunloadnow-method.md)|Tarafından sağlanan bir kitaplığı olup olmadığını belirleyen bir [Iclrdebugginglibraryprovider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) arabirimi hala kullanımda olduğu veya kaldırılmış olabilir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir örneği elde edebilirsiniz `ICLRDebugging` kullanarak arabirimi [Clrcreateınstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) işlevi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
