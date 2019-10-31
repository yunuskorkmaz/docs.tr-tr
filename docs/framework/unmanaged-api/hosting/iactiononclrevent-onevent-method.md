---
title: IActionOnCLREvent::OnEvent Yöntemi
ms.date: 03/30/2017
api_name:
- IActionOnCLREvent.OnEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IActionOnCLREvent::OnEvent
helpviewer_keywords:
- OnEvent method [.NET Framework hosting]
- IActionOnCLREvent::OnEvent method [.NET Framework hosting]
ms.assetid: 0970f10c-4304-4c12-91c0-83e51455afb4
topic_type:
- apiref
ms.openlocfilehash: 98807717fc913052dae15f9f3cbd462d4f537ad4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126926"
---
# <a name="iactiononclreventonevent-method"></a>IActionOnCLREvent::OnEvent Yöntemi
[ICLROnEventManager:: RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) metoduna yapılan bir çağrı kullanılarak kaydedilmiş olaylarda geri çağırmaları gerçekleştirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT OnEvent (  
    [in] EClrEvent event,  
    [in] PVOID     data  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `event`  
 'ndaki Olay türünü gösteren [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) değerlerinden biri.  
  
 `data`  
 'ndaki `event`ayrıntılarını içeren bir nesne işaretçisi.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`OnEvent` başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAıL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAıL döndürürse, CLR artık işlem içinde kullanılamaz. Herhangi bir barındırma yöntemine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  
 `data` parametresi, belirtilmemiş türdeki bir nesnenin işaretçisidir. `event` parametresi `Event_DomainUnload`, `data` kaldırılan <xref:System.AppDomain> için sayısal tanıtıcıdır. Ana bilgisayar bu tanımlayıcıyı anahtar olarak kullanarak uygun eylemi gerçekleştirebilir.  
  
 `event` `Event_MDAFired`, `data` yönetilen hata ayıklama Yardımcısı 'Nın (MDA) ileti çıkışını içeren bir [Mdadınfo](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md) örneğine yönelik bir işaretçidir. Mdalar, geliştiricilerin hata ayıklamasına yardımcı olan ve tuzak zorluğu eden olaylar hakkında XML iletileri oluşturarak CLR 'nin bir özelliğidir. Bu tür iletiler, yönetilen ve yönetilmeyen kod arasındaki geçişlerde hata ayıklama için özellikle yararlı olabilir. Daha fazla bilgi için bkz. [yönetilen hata ayıklama yardımcıları Ile hataları tanılama](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [EClrEvent Sabit Listesi](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)
- [IActionOnCLREvent Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)
- [ICLRControl Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [ICLROnEventManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)
- [MDAInfo Yapısı](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md)
