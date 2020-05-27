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
ms.openlocfilehash: bb40ed65a2e34f1bf293e4c4c842d7db63d2eaa5
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008449"
---
# <a name="metahost_policy_flags-enumeration"></a>METAHOST_POLICY_FLAGS Numaralandırması
Çoğu çalışma zamanı ana bilgisayarı için ortak olan bağlama ilkeleri sağlar. Bu numaralandırma [ICLRMetaHostPolicy:: GetRequestedRuntime](iclrmetahostpolicy-getrequestedruntime-method.md) yöntemi tarafından kullanılır.  
  
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
|`METAHOST_POLICY_APPLY_UPGRADE_POLICY`|, HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft içeriğine göre tam eşleşme bulunamadığında sürüm bağlama sonucuna yükseltme ilkesi uygular \\ . Netframework\ilkeupgrades. Bu, [RUNTIME_INFO_UPGRADE_VERSION](runtime-info-flags-enumeration.md)ile aynı etkiye sahiptir.|  
|`METAHOST_POLICY_EMULATE_EXE_LAUNCH`|Bağlama sonuçları, çağrıya verilen görüntü yeni bir işlemde başlatılmış gibi döndürülür. Şu anda, `GetRequestedRuntime` yüklenebilir çalışma zamanları kümesini yoksayar ve yüklü çalışma zamanları kümesine göre bağlar. Bu bayrak, bir konağın başlatıldığında bir EXE 'nin hangi çalışma zamanına bağlanacağını belirlemesine izin verir.|  
|`METAHOST_POLICY_SHOW_ERROR_DIALOG`|`GetRequestedRuntime`Giriş parametreleriyle uyumlu bir çalışma zamanı bulamazsa bir hata iletişim kutusu görüntülenir. .NET Framework 4,5 ' den başlayarak bu hata iletişim kutusu, kullanıcının uygun özelliği etkinleştirmek isteyip istemediğinizi soran bir Windows özelliği iletişim kutusu biçimini alabilir.|  
|`METAHOST_POLICY_USE_PROCESS_IMAGE_PATH`|`GetRequestedRuntime`bağlama işlemine ek girdi olarak işlem görüntüsünü (ve ilgili yapılandırma dosyalarını) kullanır. Varsayılan olarak, `GetRequestedRuntime` bağlanacak çalışma zamanı belirlenirken işlem görüntü yoluna (genellikle işlemi başlatmak için kullanılan exe) geri dönmez.|  
|`METAHOST_POLICY_ENSURE_SKU_SUPPORTED`|`GetRequestedRuntime`yapılandırma dosyasında hiçbir bilgi yoksa ilgili SKU 'nun yüklenip yüklenmediğini kontrol etmelidir. Bu, yapılandırma dosyaları olmayan uygulamaların, .NET Framework varsayılan yüklemesinden daha küçük SKU 'Larda düzgün şekilde başarısız olmasına olanak sağlar. Varsayılan olarak, `GetRequestedRuntime` yapılandırma dosyası ÖĞESINDE SKU özniteliği belirtilmediği takdirde uygun SKU 'nun yüklenip yüklenmediğini denetlemez `<supportedRuntime />` .|  
|`METAHOST_POLICY_IGNORE_ERROR_MODE`|`GetRequestedRuntime`SEM_FAILCRITICALERRORS göz ardı etmelidir ( [SetErrorMode](/windows/win32/api/errhandlingapi/nf-errhandlingapi-seterrormode) işlevi çağırarak ayarlanır) ve hata iletişim kutusunu gösterir. Varsayılan olarak, SEM_FAILCRITICALERRORS hata iletişim kutusunu bastırır. Başka bir işlemden devralınan ve sessiz hata, senaryonuza istenmeyen bir durum olabilir.|  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Metahost. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Barındırma Sabit Listeleri](hosting-enumerations.md)
- [GetRequestedRuntime Yöntemi](iclrmetahostpolicy-getrequestedruntime-method.md)
