---
title: Icordebugfunction2 arabirimi1
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2
helpviewer_keywords:
- ICorDebugFunction2 interface [.NET Framework debugging]
ms.assetid: 2b936bef-9b75-48bf-859f-42e419c65f1c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 190e2323fb07dbca6e156d7a24397997e54b6da9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54540799"
---
# <a name="icordebugfunction2-interface1"></a>Icordebugfunction2 arabirimi1
Kullanıcı olmayan kod atlar, yalnızca kendi kodum adım adım hata ayıklama için destek sağlamak üzere ICorDebugFunction arabirimi mantıksal olarak genişletir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[EnumerateNativeCode Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-enumeratenativecode-method.md)|(Henüz uygulanmadı.) Bu Icordebugfunction2 nesne tarafından başvurulan işlevinde yerel kod deyimlerini içeren bir Icordebugcodeenum için bir arabirim işaretçisi alır.|  
|[GetJMCStatus Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-getjmcstatus-method.md)|Bu işlev, kullanıcı kodu işaretlenmiş olup olmadığını gösteren bir değer alır.|  
|[GetVersionNumber Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-getversionnumber-method.md)|Bu işlev Düzenle ve devam et sürümünü alır.|  
|[SetJMCStatus Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-setjmcstatus-method.md)|Bu işlev için sadece benim kodumu işaretler Adımlama.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
>  Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
