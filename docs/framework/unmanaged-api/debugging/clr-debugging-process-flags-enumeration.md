---
title: CLR_DEBUGGING_PROCESS_FLAGS Numaralandırması
ms.date: 03/30/2017
api_name:
- CLR_DEBUGGING_PROCESS_FLAGS
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CLR_DEBUGGING_PROCESS_FLAG
helpviewer_keywords:
- CLR_DEBUGGING_PROCESS_FLAGS enumeration [.NET Framework debugging]
ms.assetid: 85b85fde-1f87-490b-ba8d-d604670959c3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 292f6953fad0d65b368642543af107c73ec42ab5
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274108"
---
# <a name="clr_debugging_process_flags-enumeration"></a>CLR_DEBUGGING_PROCESS_FLAGS Numaralandırması
[ICLRDebugging:: OpenVirtualProcess](iclrdebugging-openvirtualprocess-method.md) yöntemi tarafından kullanılan değerleri sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef enum CLR_DEBUGGING_PROCESS_FLAGS  
{  
   CLR_DEBUGGING_MANAGED_EVENT_PENDING = 1,  
   CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH = 2  
}  CLR_DEBUGGING_PROCESS_FLAGS;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`CLR_DEBUGGING_MANAGED_EVENT_PENDING`|Bu çalışma zamanının gönderileceği, ön olmayan bir yönetilen hata ayıklayıcı olayı vardır. Yakalama ve ön uç olmayan olaylar arasındaki ayrım için açıklamalar bölümüne bakın.|  
|`CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH`|Bekleyen yönetilen olay bir <xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> istek.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yakalama olayları işlem, uygulama etki alanı, derleme, modül ve hata ayıklayıcıyı bir işleme eklendikten sonra geçerli duruma getirecek olan iş parçacığı oluşturma bildirimlerini içerir. `CLR_DEBUGGING_MANAGED_EVENT_PENDING` Bayrak tarafından belirtilen yakalama olmayan olaylar, özel durumlar ve yönetilen hata ayıklama Yardımcısı (MDA) bildirimleri gibi diğer tüm hata ayıklayıcı olaylarını içerir.  
  
 `CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH` Bayrak, çalışma zamanının, iptal edilmiş bir yönetilen hata ayıklayıcı eklemek için bir Sonlandırıcı özel durumu ve isteği ayırt etmesini sağlar.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi** Metahost. IDL, Metahost. h  
  
 **Kitaplığı** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Sabit Listeleri](debugging-enumerations.md)
- [Hata Ayıklama](index.md)
