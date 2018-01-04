---
title: ICLRDebugging Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDebugging
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDebugging
helpviewer_keywords: ICLRDebugging interface [.NET Framework debugging]
ms.assetid: 429d8fce-b1b1-49d7-895c-28c1c1aa2dbd
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 325f6adf8fe3a357f903f0cb047a2255ef80e264
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdebugging-interface"></a>ICLRDebugging Arabirimi
Hata ayıklama amacıyla modülleri yükleme ve kaldırma işlemlerini yapan yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[OpenVirtualProcess Yöntemi](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md)|Bir ortak dil çalışma zamanı (CLR) modülü işleminde yüklenen karşılık gelen "ICorDebugProcess" arabirimini alır.|  
|[CanUnloadNow Yöntemi](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-canunloadnow-method.md)|Tarafından sağlanan bir kitaplık olup olmadığını belirleyen bir [Iclrdebugginglibraryprovider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) arabirimi hala kullanımda veya kaldırılmış olabilir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir örneği elde edebilirsiniz `ICLRDebugging` kullanarak arabirimi [Clrcreateınstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) işlevi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
