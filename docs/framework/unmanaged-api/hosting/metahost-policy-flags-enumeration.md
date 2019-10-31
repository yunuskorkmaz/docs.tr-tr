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
ms.openlocfilehash: a028d2a8116de4df79f662ee8b2768e6e070428a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141391"
---
# <a name="metahost_policy_flags-enumeration"></a>METAHOST_POLICY_FLAGS Numaralandırması
Çoğu çalışma zamanı ana bilgisayarı için ortak olan bağlama ilkeleri sağlar. Bu numaralandırma [ICLRMetaHostPolicy:: GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) yöntemi tarafından kullanılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
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
|`METAHOST_POLICY_HIGHCOMPAT`|Geçerli işleme yüklenmiş ortak dil çalışma zamanını (CLR) düşünmez olan yüksek uyumluluk ilkesini tanımlar. Bunun yerine, yalnızca yüklü CLRs 'leri ve bileşen tercihlerini, derleme dosyasının kendisinden türetildikleri gibi, derlenen yerleşik sürümü veya yapılandırma dosyası olarak değerlendirir.|  
|`METAHOST_POLICY_APPLY_UPGRADE_POLICY`|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\içeriğine göre tam eşleşme bulunamadığında, sürüm bağlama sonucuna yükseltme ilkesi uygular. Netframework\ilkeupgrades. Bu, [RUNTIME_INFO_UPGRADE_VERSION](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md)ile aynı etkiye sahiptir.|  
|`METAHOST_POLICY_EMULATE_EXE_LAUNCH`|Bağlama sonuçları, çağrıya verilen görüntü yeni bir işlemde başlatılmış gibi döndürülür. Şu anda `GetRequestedRuntime` yüklenebilir çalışma zamanları kümesini yoksayar ve yüklü çalışma zamanları kümesine göre bağlar. Bu bayrak, bir konağın başlatıldığında bir EXE 'nin hangi çalışma zamanına bağlanacağını belirlemesine izin verir.|  
|`METAHOST_POLICY_SHOW_ERROR_DIALOG`|`GetRequestedRuntime`, giriş parametreleriyle uyumlu bir çalışma zamanı bulamazsa bir hata iletişim kutusu görüntülenir. .NET Framework 4,5 ' den başlayarak bu hata iletişim kutusu, kullanıcının uygun özelliği etkinleştirmek isteyip istemediğinizi soran bir Windows özelliği iletişim kutusu biçimini alabilir.|  
|`METAHOST_POLICY_USE_PROCESS_IMAGE_PATH`|`GetRequestedRuntime`, bağlama işlemine ek girdi olarak işlem görüntüsünü (ve ilgili yapılandırma dosyalarını) kullanır. Varsayılan olarak `GetRequestedRuntime`, bağlanacak çalışma zamanı belirlenirken işlem görüntü yoluna (genellikle işlemi başlatmak için kullanılan EXE) geri dönmemektedir.|  
|`METAHOST_POLICY_ENSURE_SKU_SUPPORTED`|`GetRequestedRuntime`, yapılandırma dosyasında herhangi bir bilgi yoksa ilgili SKU 'nun yüklenip yüklenmediğini denetmelidir. Bu, yapılandırma dosyaları olmayan uygulamaların, .NET Framework varsayılan yüklemesinden daha küçük SKU 'Larda düzgün şekilde başarısız olmasına olanak sağlar. Varsayılan olarak, `GetRequestedRuntime` SKU özniteliği yapılandırma dosyası `<supportedRuntime />` öğesinde belirtilmediği takdirde uygun SKU 'nun yüklenip yüklenmediğini denetlemez.|  
|`METAHOST_POLICY_IGNORE_ERROR_MODE`|`GetRequestedRuntime`, SEM_FAILCRITICALERRORS ( [SetErrorMode](https://go.microsoft.com/fwlink/p/?LinkId=255242) işlevi çağırarak ayarlanır) öğesini yoksayıp hata iletişim kutusunu gösterir. Varsayılan olarak, SEM_FAILCRITICALERRORS hata iletişim kutusunu bastırır. Başka bir işlemden devralınan ve sessiz hata, senaryonuza istenmeyen bir durum olabilir.|  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** Metahost. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Barındırma Sabit Listeleri](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
- [GetRequestedRuntime Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)
