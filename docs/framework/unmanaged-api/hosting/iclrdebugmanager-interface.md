---
title: ICLRDebugManager Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDebugManager
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRDebugManager
helpviewer_keywords: ICLRDebugManager interface [.NET Framework hosting]
ms.assetid: e835062c-c7d6-4945-8a44-2de7ebf3928e
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0e537b955524f2721868ddf5da9fccf68f9d4efd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="iclrdebugmanager-interface"></a>ICLRDebugManager Arabirimi
Bir dizi görevi bir tanımlayıcı ve kolay bir ad ile ilişkilendirmek konak izin vermek yöntemleri sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[BeginConnection yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)|Ana bilgisayar ve hata ayıklayıcısı görevleri bir tanımlayıcı ve kolay bir ad ile ilişkilendirmek için arasında yeni bir bağlantı kurar.|  
|[EndConnection yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)|Görevlerin bir listesi ve bir tanımlayıcı ve bir kolay ad arasındaki ilişkiyi kaldırır.|  
|[GetDacl yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-getdacl-method.md)|Bu yöntem uygulanmadı.|  
|[Isdebuggerattached yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-isdebuggerattached-method.md)|İşleme bir hata ayıklayıcısı ekli olup olmadığını belirten bir değer alır.|  
|[SetConnectionTasks yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)|Listesini ilişkilendirir [Iclrtask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) tanımlayıcı ve kolay bir ad ile örnekleri.|  
|[SetDacl yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setdacl-method.md)|Bu yöntem uygulanmadı.|  
|[SetSymbolReadingPolicy yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md)|Program veritabanı (PDB) dosyaları okumak için ilke ayarlar. İlke çağrı yığınları satır numaralarını ve dosyalarla ilgili bilgiler dahil edilip edilmeyeceğini belirler.|  
  
## <a name="remarks"></a>Açıklamalar  
 Senaryoları hata ayıklama, bir konak grubu görevleri programlama mantığındaki göre isteyebilirsiniz. Örneğin, bir gruplandırma işleminde çalışan her görev görmesini yerine Geliştirici API'leri, gerekli görevleri görmek bir geliştirici olanak tanır. `ICLRDebugManager`Bu tür bir gruplandırma uygulamak için ana sağlar.  
  
> [!IMPORTANT]
>  Üç `ICLRDebugManager` yöntemleri `BeginConnection`, `SetConnectionTasks` ve `EndConnection`, birbirine bağımlıdır. Beklendiği şekilde çalışması için verildikleri sırada çağrılmalıdır.  
  
 Gruplandırma ve tanımlayıcıları ve gruplandırma için konak atar kolay adlar ortak dil çalışma zamanı (CLR) için hiçbir anlamı yoktur. CLR boyunca bilgi için hata ayıklayıcı yalnızca geçirir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.h  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Barındırma arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
