---
description: 'Hakkında daha fazla bilgi edinin: CLR_DEBUGGING_PROCESS_FLAGS numaralandırması'
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
ms.openlocfilehash: 81510bde123ef9a8adefaec5b0708086dacbbf2d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772815"
---
# <a name="clr_debugging_process_flags-enumeration"></a>CLR_DEBUGGING_PROCESS_FLAGS Numaralandırması

[ICLRDebugging:: OpenVirtualProcess](iclrdebugging-openvirtualprocess-method.md) yöntemi tarafından kullanılan değerleri sağlar.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef enum CLR_DEBUGGING_PROCESS_FLAGS  
{  
   CLR_DEBUGGING_MANAGED_EVENT_PENDING = 1,  
   CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH = 2  
}  CLR_DEBUGGING_PROCESS_FLAGS;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Description|  
|------------|-----------------|  
|`CLR_DEBUGGING_MANAGED_EVENT_PENDING`|Bu çalışma zamanının gönderileceği, ön olmayan bir yönetilen hata ayıklayıcı olayı vardır. Yakalama ve ön uç olmayan olaylar arasındaki ayrım için açıklamalar bölümüne bakın.|  
|`CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH`|Bekleyen yönetilen olay bir <xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> istek.|  
  
## <a name="remarks"></a>Açıklamalar  

 Yakalama olayları işlem, uygulama etki alanı, derleme, modül ve hata ayıklayıcıyı bir işleme eklendikten sonra geçerli duruma getirecek olan iş parçacığı oluşturma bildirimlerini içerir. Bayrak tarafından belirtilen yakalama olmayan olaylar `CLR_DEBUGGING_MANAGED_EVENT_PENDING` , özel durumlar ve yönetilen hata ayıklama Yardımcısı (MDA) bildirimleri gibi diğer tüm hata ayıklayıcı olaylarını içerir.  
  
 `CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH`Bayrak, çalışma zamanının, iptal edilmiş bir yönetilen hata ayıklayıcı eklemek için bir Sonlandırıcı özel durumu ve isteği ayırt etmesini sağlar.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Metahost. IDL, Metahost. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Numaralandırmaları](debugging-enumerations.md)
- [Hata Ayıklama](index.md)
