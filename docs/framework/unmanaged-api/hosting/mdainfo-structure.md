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
ms.openlocfilehash: 517e0ae7fb5d5151f94f82d9146ebbf40bad2ef9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503867"
---
# <a name="mdainfo-structure"></a>MDAInfo Yapısı
`Event_MDAFired`Yönetilen hata ayıklama Yardımcısı (MDA) oluşturulmasını tetikleyen olayla ilgili ayrıntıları sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef struct _MDAInfo {  
    LPCWSTR  lpMDACaption;  
    LPCWSTR  lpMDAMessage  
} MDAInfo;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Description|  
|------------|-----------------|  
|`lpMDACaption`|Geçerli MDA 'ın başlığı. Başlık, olayı tetikleyen hata türünü açıklar `Event_MDAFired` .|  
|`lpMDAMessage`|Geçerli MDA tarafından sunulan çıkış iletisi.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yönetilen hata ayıklama yardımcıları (MDAs), çalışma zamanı yürütme altyapısında geçersiz koşulları tanımlama veya altyapının durumu hakkında ek bilgi dökümü gibi görevleri gerçekleştirmek için ortak dil çalışma zamanı (CLR) ile birlikte çalışan hata ayıklama yardımlarıdır. MDAs, tuzak zor olan olaylar hakkında XML iletileri oluşturur. Yönetilen ve yönetilmeyen kod arasındaki geçişlerde hata ayıklama için özellikle faydalıdır.  
  
 Çalışma zamanı, bir MDA öğesinin oluşturulmasını tetikleyen bir olay harekete geçirildiğinde aşağıdaki adımları gerçekleştirir:  
  
- Ana bilgisayar bir olay hakkında bildirim almak için [ICLROnEventManager:: RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md) öğesini çağırarak bir [IActionOnCLREvent](iactiononclrevent-interface.md) örneği kaydettirmemişse `Event_MDAFired` , çalışma zamanı varsayılan, barındırılmamış davranışıyla devam eder.  
  
- Konakta bu olay için bir işleyici kaydedilmişse, çalışma zamanı bir hata ayıklayıcının işleme bağlı olup olmadığını denetler. Eğer ise, çalışma zamanı hata ayıklayıcıya kesilir. Hata ayıklayıcı devam ederse, ana bilgisayara çağrı yapılır. Herhangi bir hata ayıklayıcı ekli değilse, çalışma zamanı bir `IActionOnCLREvent::OnEvent` örneğe bir işaretçi çağırır ve bir işaretçiyi `MDAInfo` parametre olarak geçirir `data` .  
  
 Ana bilgisayar Mdaları etkinleştirmeyi seçebilir ve bir MDA etkinleştirildiğinde bildirim alabilir. Bu, ana bilgisayara varsayılan davranışı geçersiz kılmak ve olayı oluşturan yönetilen iş parçacığını durdurmak için, işlem durumunu bozmasını engellemek için bir fırsat sağlar. MDAs kullanma hakkında daha fazla bilgi için bkz. [yönetilen hata ayıklama yardımcıları Ile hataları tanılama](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. IDL  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Barındırma Yapıları](hosting-structures.md)
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
