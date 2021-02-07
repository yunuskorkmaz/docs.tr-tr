---
description: 'Daha fazla bilgi edinin: ICorDebugFunction2 Interface'
title: ICorDebugFunction2 Arabirimi
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
ms.openlocfilehash: e5297d46acb9b174537363fc185fa2d540d55a75
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692205"
---
# <a name="icordebugfunction2-interface"></a>ICorDebugFunction2 Arabirimi

Kullanıcı dışı kodu atlayan Yalnızca kendi kodum adım adım hata ayıklama desteği sağlamak için ICorDebugFunction arabirimini mantıksal olarak genişletir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[EnumerateNativeCode Yöntemi](icordebugfunction2-enumeratenativecode-method.md)|(Henüz uygulanmadı.) Bu ICorDebugFunction2 nesnesinin başvurduğu işlevdeki yerel kod deyimlerini içeren bir ICorDebugCodeEnum için bir arabirim işaretçisi alır.|  
|[GetJMCStatus Yöntemi](icordebugfunction2-getjmcstatus-method.md)|Bu işlevin Kullanıcı kodu olarak işaretlenip işaretlenmediğini gösteren bir değer alır.|  
|[GetVersionNumber Metodu](icordebugfunction2-getversionnumber-method.md)|Bu işlevin Düzenle ve devam et sürümünü alır.|  
|[SetJMCStatus Yöntemi](icordebugfunction2-setjmcstatus-method.md)|Bu işlevi Yalnızca kendi kodum Adımlama için işaretler.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
