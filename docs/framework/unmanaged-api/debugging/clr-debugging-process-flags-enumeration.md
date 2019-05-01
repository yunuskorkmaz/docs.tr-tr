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
ms.openlocfilehash: 8321e5aeba435ca5f1398a9cb827a93ae821d686
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61996365"
---
# <a name="clrdebuggingprocessflags-enumeration"></a>CLR_DEBUGGING_PROCESS_FLAGS Numaralandırması
Tarafından kullanılan değerleri sağlar [Iclrdebugging::openvirtualprocess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) yöntemi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef enum CLR_DEBUGGING_PROCESS_FLAGS  
{  
   CLR_DEBUGGING_MANAGED_EVENT_PENDING = 1,  
   CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH = 2  
}  CLR_DEBUGGING_PROCESS_FLAGS;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`CLR_DEBUGGING_MANAGED_EVENT_PENDING`|Bu çalışma zamanı göndermek için bir catch yukarı yönetilen hata ayıklayıcı olayında. Olayları yakalama ve catch yukarı arasındaki fark için Açıklamalar bölümüne bakın.|  
|`CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH`|Beklemede olan yönetilen olay bir <xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> istek.|  
  
## <a name="remarks"></a>Açıklamalar  
 Olayları yakalama işlemi, uygulama etki alanı, derleme, modül ve sonra bir işleme eklenmiş kadar geçerli durumu hata ayıklayıcı getiren iş parçacığı oluşturma bildirimleri içerir. Tarafından belirtilen olmayan catch yukarı olayları `CLR_DEBUGGING_MANAGED_EVENT_PENDING` bayrak, tüm diğer hata ayıklayıcı olayları, özel durumlar gibi içerir ve yönetilen hata ayıklama Yardımcısı (MDA) bildirimleri.  
  
 `CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH` Bayrağı isteği iptal edilebilir bir yönetilen hata ayıklayıcı ekleyin ve bir sonlandırma özel durumuyla arasında ayırt etmek çalışma zamanı sağlar.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** Metahost.idl, Metahost.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Sabit Listeleri](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
