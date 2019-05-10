---
title: MDAInfo Yapısı
ms.date: 03/30/2017
api_name:
- MDAInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- MDAInfo
helpviewer_keywords:
- MDAInfo structure [.NET Framework hosting]
ms.assetid: fb8c14f7-d461-43d1-8b47-adb6723b9b93
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: faa6af54714f7f0b7ac91c7836673c163195d5f6
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64656465"
---
# <a name="mdainfo-structure"></a>MDAInfo Yapısı
Hakkında ayrıntılar sağlar `Event_MDAFired` olayı yönetilen hata ayıklama Yardımcısı (MDA) oluşturulmasını tetikler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef struct _MDAInfo {  
    LPCWSTR  lpMDACaption;  
    LPCWSTR  lpMDAMessage  
} MDAInfo;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`lpMDACaption`|Geçerli MDA'ın başlığı. Başlık tetiklenen hata türünü açıklar `Event_MDAFired` olay.|  
|`lpMDAMessage`|Geçerli bir MDA tarafından sağlanan çıkış iletisi.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yönetilen hata ayıklama Yardımcıları (MDAs) çalışma zamanı yürütme altyapısı, ortak dil çalışma zamanı (CLR) geçersiz koşulları belirleme gibi görevleri gerçekleştirmek için birlikte çalışan yardımlarda hata veya durumu hakkında ek bilgi dökümü alma altyapısı. Mda'leri, aksi takdirde tuzak zor olan olaylar hakkında XML iletileri oluşturur. Bunlar, yönetilen ve yönetilmeyen kod arasındaki geçişleri hata ayıklama için özellikle yararlı olur.  
  
 Bir MDA oluşturulmasını tetikleyen bir olay harekete çalışma zamanı, aşağıdaki adımları gerçekleştirir:  
  
- Konak kayıtlı değil, bir [Iactiononclrevent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) çağırarak örneği [Iclroneventmanager::registeractiononevent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) haberdar için bir `Event_MDAFired` çalışma zamanı olayı geçer ile kendi Varsayılan, barındırılan olmayan davranış.  
  
- Bu olay işleyicisi ana bilgisayarı kaydedildiyse, çalışma zamanı hata ayıklayıcı işleme ekli olup olmadığını denetler. Bu durumda, çalışma zamanı hata ayıklayıcıya keser. Hata ayıklayıcının devam ettiğinde, ana bilgisayar çağırır. Hata ayıklayıcı bağlıysa, çalışma zamanı çağırır `IActionOnCLREvent::OnEvent` ve işaretçi bir `MDAInfo` örneği `data` parametresi.  
  
 Mda'leri etkinleştirme ve bir MDA etkinleştirildiğinde bildirim almak için konağı seçebilirsiniz. Bu konak varsayılan davranışı geçersiz kılabilir ve işlem durumu bozan gelen önlemek için olayı tetikleyen yönetilen iş parçacığını durdurmak için bir fırsat sağlar. Mda'leri kullanma hakkında daha fazla bilgi için bkz. [yönetilen hata ayıklama Yardımcıları ile hataları tanılama](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.idl  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Barındırma Yapıları](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
