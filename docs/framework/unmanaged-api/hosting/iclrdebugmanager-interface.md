---
title: ICLRDebugManager Arabirimi
ms.date: 03/30/2017
api_name:
- ICLRDebugManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager
helpviewer_keywords:
- ICLRDebugManager interface [.NET Framework hosting]
ms.assetid: e835062c-c7d6-4945-8a44-2de7ebf3928e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 515eb0633c82c3e1386487d1866de79c9898c9cd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54654613"
---
# <a name="iclrdebugmanager-interface"></a>ICLRDebugManager Arabirimi
Bir görev kümesi bir tanımlayıcı ve kolay bir ad ile ilişkilendirmek konak izin vermek için yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[BeginConnection Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)|Konak ve hata ayıklayıcı görevleri bir tanımlayıcı ve kolay bir ad ile ilişkilendirmek için arasında yeni bir bağlantı kurar.|  
|[EndConnection Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)|Görevlerin bir listesi ve tanımlayıcı bir kolay ad arasındaki ilişkiyi kaldırır.|  
|[GetDacl Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-getdacl-method.md)|Bu yöntem uygulanmadı.|  
|[IsDebuggerAttached Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-isdebuggerattached-method.md)|Bir hata ayıklayıcı işleme ekli olup olmadığını gösteren bir değer alır.|  
|[SetConnectionTasks Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)|Listesini ilişkilendirir [Iclrtask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) örnekleriyle tanımlayıcı ve bir kolay ad.|  
|[SetDacl Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setdacl-method.md)|Bu yöntem uygulanmadı.|  
|[SetSymbolReadingPolicy Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md)|Program veritabanı (PDB) dosyaları okumak için ilkesini ayarlar. İlke satır numaraları ve dosyaları hakkında bilgi çağrı yığınlarıyla içerilip içerilmeyeceğini belirler.|  
  
## <a name="remarks"></a>Açıklamalar  
 Hata ayıklama senaryoları bir konak grubu görevleri programlama mantığını göre isteyebilirsiniz. Örneğin, bir gruplandırma bir geliştirici Geliştirici API'leri, işlemde çalışan her görev görmek yerine gerektirdiği görevleri görmek izin verir. `ICLRDebugManager` Bu tür bir gruplandırma uygulamak konak sağlar.  
  
> [!IMPORTANT]
>  Üç `ICLRDebugManager` yöntemleri `BeginConnection`, `SetConnectionTasks` ve `EndConnection`, birbirine bağlıdır. Verildikleri sırada beklendiği şekilde çalışması için çağrılmalıdır.  
  
 Gruplandırma ve tanımlayıcıları ve konak gruba atar. kolay adlar bir ortak dil çalışma zamanı (CLR) için hiçbir anlamı yoktur. CLR, yalnızca hata ayıklayıcıyı boyunca bilgileri geçirir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
