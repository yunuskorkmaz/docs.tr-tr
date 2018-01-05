---
title: "MDAInfo Yapısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: MDAInfo
api_location: mscoree.dll
api_type: COM
f1_keywords: MDAInfo
helpviewer_keywords: MDAInfo structure [.NET Framework hosting]
ms.assetid: fb8c14f7-d461-43d1-8b47-adb6723b9b93
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 53a999028f2677599598caf55e62f10721f61fe3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="mdainfo-structure"></a>MDAInfo Yapısı
Hakkında ayrıntılar sağlar `Event_MDAFired` yönetilen hata ayıklama Yardımcısı (MDA) oluşturulmasını tetikleyen olayı.  
  
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
|`lpMDACaption`|Geçerli MDA başlığı. Başlık tetiklenen hatası türünü açıklar `Event_MDAFired` olay.|  
|`lpMDAMessage`|Geçerli mda'sı tarafından sağlanan çıkış ileti.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yönetilen hata ayıklama Yardımcıları (Mda'lar) çalışma zamanı yürütme altyapısı ortak dil çalışma zamanı (CLR) geçersiz koşulları tanımlama gibi görevleri gerçekleştirmek için birlikte çalışmak yardımları hata ayıklama veya durumuyla ilgili ek bilgi döküm alma altyapısı. Mda'lar, aksi takdirde tuzak zor olan olaylar hakkında XML iletileri oluşturur. Bunlar yönetilen ve yönetilmeyen kodu arasında geçişler hata ayıklama için özellikle yararlı olur.  
  
 Bir MDA oluşturulmasını tetikleyen bir olay başlatıldığında çalışma zamanı aşağıdaki adımları gerçekleştirir:  
  
-   Konak değil kaydedildiyse bir [Iactiononclrevent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) çağırarak örneği [Iclroneventmanager::registeractiononevent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) , bildirim almak için bir `Event_MDAFired` olay, çalışma zamanı geçer ile kendi Varsayılan, barındırılan dışı davranış.  
  
-   Bu olay işleyicisi konağı kaydedildiyse, çalışma zamanı işleme bir hata ayıklayıcısı ekli olup olmadığını denetler. İse, çalışma zamanı ayıklayıcıya keser. Hata ayıklayıcı devam ettiğinde, ana bilgisayar çağırır. Hiçbir hata ayıklayıcısı ekli, çalışma zamanı çağırır `IActionOnCLREvent::OnEvent` ve bir işaretçi geçirir bir `MDAInfo` örneği `data` parametresi.  
  
 Ana bilgisayar Mda'lar etkinleştirmek için ve bir MDA etkinleştirildiğinde uyarılmayı seçebilirsiniz. Bu konak varsayılan davranışı geçersiz kılma ve işlem durumunda bozulmasını önlemek için, olayı yönetilen iş parçacığı iptal etmek için bir fırsat sağlar. Mda'lar kullanma hakkında daha fazla bilgi için bkz: [yönetilen hata ayıklama Yardımcıları ile hataları tanılama](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.idl  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Barındırma Yapıları](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)  
 [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
