---
title: StackOverflowInfo Yapısı
ms.date: 03/30/2017
api_name:
- StackOverflowInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StackOverflowInfo
helpviewer_keywords:
- StackOverflowInfo structure [.NET Framework hosting]
ms.assetid: 519389f2-0217-436c-99d4-93a76ebce5b5
topic_type:
- apiref
ms.openlocfilehash: a8a57cfcaf36949d4d10c6ec267a5f55a2aee5eb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729934"
---
# <a name="stackoverflowinfo-structure"></a>StackOverflowInfo Yapısı

Oluşan taşma türünü ve taşma nedeniyle oluşan özel durum hakkında bilgi depolar.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef struct _StackOverflowInfo {  
    StackOverflowType   soType;  
    EXCEPTION_POINTERS  *pExceptionInfo;  
} StackOverflowInfo;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`soType`|Taşma türünü belirten [StackOverflowType](stackoverflowtype-enumeration.md) numaralandırması değeri.|  
|`pExceptionInfo`|Bir özel durumun `EXCEPTION_POINTERS` makineye bağlı bir açıklamasına sahip bir özel durum kaydı ve özel durum sırasında işlemci bağlamının makineye bağlı açıklamasıyla bir bağlam kaydı Içeren Win32 nesnesine yönelik bir işaretçi.|  
  
## <a name="remarks"></a>Açıklamalar  

 `StackOverflowInfo`Olaylar Için [IActionOnCLREvent:: OnEvent](iactiononclrevent-onevent-method.md) yöntemine bir nesne geçirilir `Event_StackOverflow` .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. IDL  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Barındırma Yapıları](hosting-structures.md)
