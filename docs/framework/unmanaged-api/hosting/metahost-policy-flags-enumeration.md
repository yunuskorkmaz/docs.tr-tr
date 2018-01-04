---
title: "METAHOST_POLICY_FLAGS Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: METAHOST_POLICY_FLAGS
api_location: mscoree.dll
api_type: COM
f1_keywords: METAHOST_POLICY_FLAGS
helpviewer_keywords: METAHOST_POLICY_FLAGS enumeration [.NET Framework hosting]
ms.assetid: 3bb4b526-0118-42e2-ba59-c95648528ce9
topic_type: apiref
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 80abed08cc7659d4218dce445be81481bb5a665b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="metahostpolicyflags-enumeration"></a>METAHOST_POLICY_FLAGS Numaralandırması
Çoğu çalışma zamanı konaklar için ortak olan bağlama ilkeleri sağlar. Bu numaralandırma tarafından kullanılan [Iclrmetahostpolicy::getrequestedruntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) yöntemi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef enum {  
    METAHOST_POLICY_HIGHCOMPAT              = 0x00,  
    METAHOST_POLICY_APPLY_UPGRADE_POLICY    = 0x08,  
    METAHOST_POLICY_EMULATE_EXE_LAUNCH      = 0x10,  
    METAHOST_POLICY_SHOW_ERROR_DIALOG       = 0x20,  
    METAHOST_POLICY_USE_PROCESS_IMAGE_PATH  = 0x40,  
    METAHOST_POLICY_ENSURE_SKU_SUPPORTED    = 0x80,  
    METAHOST_POLICY_IGNORE_ERROR_MODE       = 0x1000  
  
} METAHOST_POLICY_FLAGS;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`METAHOST_POLICY_HIGHCOMPAT`|Geçerli işlemine yüklenen tüm ortak dil çalışma zamanı (CLR) dikkate almaz yüksek uyumluluk İlkesi tanımlar. Bunun yerine, onu yalnızca yüklü CLRs ve bileşen Tercihler derleme dosyası, bildirilen yerleşik karşı sürümü veya yapılandırma dosyasını türetilmiş olarak göz önünde bulundurur.|  
|`METAHOST_POLICY_APPLY_UPGRADE_POLICY`|Tam bir eşleşme, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft içeriğine göre bulunmadığında, yükseltme ilkesi sürüm bağlama sonucu geçerlidir\\. NETFramework\Policy\Upgrades. Bu aynı etkiye sahip [RUNTIME_INFO_UPGRADE_VERSION](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md).|  
|`METAHOST_POLICY_EMULATE_EXE_LAUNCH`|Bağlama sonuçları çağrısına sağlanan görüntüsünü yeni bir işlemde başlatılan olarak döndürülür. Şu anda `GetRequestedRuntime` yüklenebilir çalışma zamanları kümesi yoksayar ve yüklü çalışma zamanları kümesi karşı bağlar. Bu bayrak başlatıldığında bir EXE bağlanacağı hangi çalışma zamanı belirlemek bir konak sağlar.|  
|`METAHOST_POLICY_SHOW_ERROR_DIALOG`|Bir hata iletişim kutusu görüntülenir `GetRequestedRuntime` giriş parametreleri ile uyumlu bir çalışma zamanı bulamıyor. İle başlayarak [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], bu hata iletişim kutusunda kullanıcı uygun özelliğini etkinleştirmek isteyip istemediğinizi soran bir Windows özelliği iletişim kutusu biçiminde.|  
|`METAHOST_POLICY_USE_PROCESS_IMAGE_PATH`|`GetRequestedRuntime`işlem görüntü (ve karşılık gelen hiçbir yapılandırma dosyası) bağlama işlemi ek giriş olarak kullanır. Varsayılan olarak, `GetRequestedRuntime` işlem görüntü yolu (genellikle, işlemi başlatmak için kullanılan EXE) için geri dönüş değil bağlamak için çalışma zamanı belirlerken.|  
|`METAHOST_POLICY_ENSURE_SKU_SUPPORTED`|`GetRequestedRuntime`hiçbir bilgi yapılandırma dosyasında kullanılabilir olduğunda uygun SKU yüklü olup olmadığını denetleyin gerekir. Bu yapılandırma dosyalarını .NET Framework'ün varsayılan yükleme değerinden daha küçük SKU üzerinde düzgün biçimde başarısız olmayan uygulamaları sağlar. Varsayılan olarak, `GetRequestedRuntime` SKU özniteliği yapılandırma dosyasında belirtilmediği sürece uygun SKU yüklü olup olmadığını denetlemez `<supportedRuntime />` öğesi.|  
|`METAHOST_POLICY_ENSURE_SKU_SUPPORTED`|`GetRequestedRuntime`hiçbir bilgi yapılandırma dosyasında kullanılabilir olduğunda uygun SKU yüklü olup olmadığını denetleyin gerekir. Bu yapılandırma dosyalarını .NET Framework'ün varsayılan yükleme değerinden daha küçük SKU üzerinde düzgün biçimde başarısız olmayan uygulamaları sağlar. Varsayılan olarak, `GetRequestedRuntime` SKU özniteliği yapılandırma dosyasında belirtilmediği sürece uygun SKU yüklü olup olmadığını denetlemez `<supportedRuntime />` öğesi.|  
|`METAHOST_POLICY_IGNORE_ERROR_MODE`|`GetRequestedRuntime`SEM_FAILCRITICALERRORS yok saymanız gerekir (çağırarak ayarlanmış [SetErrorMode](http://go.microsoft.com/fwlink/p/?LinkId=255242) işlevi) ve hata iletişim kutusu gösterir. Varsayılan olarak, hata iletişim kutusu SEM_FAILCRITICALERRORS gizler. Başka bir işlemden devralınmış ve sessiz hatası senaryonuzda istenmeyen olabilir.|  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Metahost.h  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Barındırma Sabit Listeleri](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)  
 [GetRequestedRuntime Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)
