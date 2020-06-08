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
ms.openlocfilehash: 653c8d1d3edd38e646b4e90c0e48dbe15bed102a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504270"
---
# <a name="iclrdebugmanager-interface"></a>ICLRDebugManager Arabirimi
Bir ana bilgisayarın bir dizi görevi bir tanımlayıcıyla ve kolay bir adla ilişkilendirilmesine imkan tanıyan yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Description|  
|------------|-----------------|  
|[BeginConnection Yöntemi](iclrdebugmanager-beginconnection-method.md)|Görevleri bir tanımlayıcı ve kolay bir ad ile ilişkilendirmek için ana bilgisayar ile hata ayıklayıcı arasında yeni bir bağlantı kurar.|  
|[EndConnection Yöntemi](iclrdebugmanager-endconnection-method.md)|Bir görev listesi ve tanımlayıcı ve kolay ad arasındaki ilişkiyi kaldırır.|  
|[GetDacl Yöntemi](iclrdebugmanager-getdacl-method.md)|Bu yöntem uygulanmadı.|  
|[IsDebuggerAttached Yöntemi](iclrdebugmanager-isdebuggerattached-method.md)|Bir hata ayıklayıcının işleme bağlı olup olmadığını gösteren bir değer alır.|  
|[SetConnectionTasks Yöntemi](iclrdebugmanager-setconnectiontasks-method.md)|[ICLRTask](iclrtask-interface.md) örneklerinin listesini bir tanımlayıcı ve kolay bir ad ile ilişkilendirir.|  
|[SetDacl Yöntemi](iclrdebugmanager-setdacl-method.md)|Bu yöntem uygulanmadı.|  
|[SetSymbolReadingPolicy Yöntemi](iclrdebugmanager-setsymbolreadingpolicy-method.md)|Program veritabanı (PDB) dosyalarını okuma ilkesini ayarlar. İlke, satır numaraları ve dosya hakkındaki bilgilerin çağrı yığınlarına dahil edilip edilmeyeceğini belirler.|  
  
## <a name="remarks"></a>Açıklamalar  
 Hata ayıklama senaryolarında, bir ana bilgisayar görevleri kendi programlama mantığına göre gruplamak isteyebilir. Örneğin, bir gruplandırma, bir geliştiricinin işlemde çalışan her görevi görmek yerine yalnızca geliştiricinin API 'Leri için gereken görevleri görmesine izin verir. `ICLRDebugManager`konağın bu tür gruplamayı uygulamasına izin verir.  
  
> [!IMPORTANT]
> Üç `ICLRDebugManager` Yöntem, `BeginConnection` `SetConnectionTasks` ve birbirlerine `EndConnection` bağlıdır. Beklenen şekilde çalışması için, bunların belirtilen sırada çağrılması gerekir.  
  
 Gruplandırma ve konağın gruplandırmaya atadığı tanımlayıcı ve kolay adlar, ortak dil çalışma zamanı (CLR) için bir anlamı yoktur. CLR, bilgileri yalnızca hata ayıklayıcıyla geçirir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Barındırma Arabirimleri](hosting-interfaces.md)
