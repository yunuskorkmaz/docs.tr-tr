---
title: METAHOST_POLICY_FLAGS Numaralandırması
ms.date: 03/30/2017
api_name:
- METAHOST_POLICY_FLAGS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- METAHOST_POLICY_FLAGS
helpviewer_keywords:
- METAHOST_POLICY_FLAGS enumeration [.NET Framework hosting]
ms.assetid: 3bb4b526-0118-42e2-ba59-c95648528ce9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 31ff93b6935c2237a5935c4b40cc30b4129edcd0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59230609"
---
# <a name="metahostpolicyflags-enumeration"></a>METAHOST_POLICY_FLAGS Numaralandırması
Çoğu çalışma zamanı konaklar için ortak olan bağlama ilkeleri sağlar. Bu sabit listesi tarafından kullanılan [Iclrmetahostpolicy::getrequestedruntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) yöntemi.  
  
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
|`METAHOST_POLICY_HIGHCOMPAT`|Geçerli işlem içine yüklenmiş tüm ortak dil çalışma zamanının (CLR) göz önünde bulundurmaz yüksek uyumluluk İlkesi tanımlar. Bunun yerine, bunu yalnızca yüklü CLRs ve bileşen tercihleri derleme dosyası, bildirilen yerleşik karşı sürümü veya yapılandırma dosyasını türetildiği haliyle olarak kabul eder.|  
|`METAHOST_POLICY_APPLY_UPGRADE_POLICY`|Tam bir eşleşme, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft içeriklerine dayanan bulunmadığında, sürüm bağlama sonucu yükseltme İlkesi uygular\\. NETFramework\Policy\Upgrades. Bu aynı etkiye sahiptir [RUNTIME_INFO_UPGRADE_VERSION](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md).|  
|`METAHOST_POLICY_EMULATE_EXE_LAUNCH`|Yeni bir işleme çağrısına sağlanan görüntü Gezginden gibi bağlama sonuçlar döndürülür. Şu anda `GetRequestedRuntime` yüklenebilir çalışma zamanları kümesini yoksayar ve çalışma zamanı kümesini karşı bağlar. Bu bayrak başlatıldığında bir EXE bağlanacağı hangi çalışma zamanı belirlemek bir konak sağlar.|  
|`METAHOST_POLICY_SHOW_ERROR_DIALOG`|Bir hata iletişim kutusu görüntülenir `GetRequestedRuntime` giriş parametreleri ile uyumlu olan bir çalışma zamanı bulamıyor. İle başlayarak [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], bu hata iletişim kutusunda kullanıcı uygun özelliğini etkinleştirmek isteyip istemediğinizi soran bir Windows özelliği iletişim kutusu biçiminde.|  
|`METAHOST_POLICY_USE_PROCESS_IMAGE_PATH`|`GetRequestedRuntime` işlem görüntü (ve karşılık gelen herhangi bir yapılandırma dosyası) bağlama işlemi için ek giriş olarak kullanır. Varsayılan olarak, `GetRequestedRuntime` geri işlem görüntü yolu (genellikle işlemi başlatmak için kullanılan EXE) düşmüyorsa bağlamak için çalışma zamanı belirlerken.|  
|`METAHOST_POLICY_ENSURE_SKU_SUPPORTED`|`GetRequestedRuntime` yapılandırma dosyasında hiçbir bilgi kullanılabilir olduğunda ve uygun SKU yüklü olup olmadığını denetlemelisiniz. Bu, varsayılan yükleme .NET Framework'ün daha küçük SKU'ları üzerinde düzgün bir şekilde başarısız için yapılandırma dosyalarını olmayan uygulamalar sağlar. Varsayılan olarak, `GetRequestedRuntime` SKU öznitelik yapılandırma dosyasında belirtilmediği sürece ve uygun SKU yüklü olup olmadığını denetlemez `<supportedRuntime />` öğesi.|  
|`METAHOST_POLICY_ENSURE_SKU_SUPPORTED`|`GetRequestedRuntime` yapılandırma dosyasında hiçbir bilgi kullanılabilir olduğunda ve uygun SKU yüklü olup olmadığını denetlemelisiniz. Bu, varsayılan yükleme .NET Framework'ün daha küçük SKU'ları üzerinde düzgün bir şekilde başarısız için yapılandırma dosyalarını olmayan uygulamalar sağlar. Varsayılan olarak, `GetRequestedRuntime` SKU öznitelik yapılandırma dosyasında belirtilmediği sürece ve uygun SKU yüklü olup olmadığını denetlemez `<supportedRuntime />` öğesi.|  
|`METAHOST_POLICY_IGNORE_ERROR_MODE`|`GetRequestedRuntime` SEM_FAILCRITICALERRORS sayılmalıdır (çağırarak Hosted [SetErrorMode](https://go.microsoft.com/fwlink/p/?LinkId=255242) işlevi) ve hata iletişim kutusunu görüntüleyin. Varsayılan olarak, hata iletişim kutusu SEM_FAILCRITICALERRORS bastırır. Başka bir işlemden devralınmış ve sessiz hata senaryonuzda istenmeyen olabilir.|  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** Metahost.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Barındırma Sabit Listeleri](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
- [GetRequestedRuntime Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)
