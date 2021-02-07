---
description: 'Daha fazla bilgi edinin: CorDebugExceptionFlags numaralandırması'
title: CorDebugExceptionFlags Numaralandırması
ms.date: 03/30/2017
api_name:
- CorDebugExceptionFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugExceptionFlags
helpviewer_keywords:
- CorDebugExceptionFlags enumeration [.NET Framework debugging]
ms.assetid: b22687a8-e9cf-4e65-a1b0-f92a81bc524e
topic_type:
- apiref
ms.openlocfilehash: c0036c2674f3202623da1a8fdeea14165a2a6e62
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747055"
---
# <a name="cordebugexceptionflags-enumeration"></a>CorDebugExceptionFlags Numaralandırması

Bir özel durum hakkında ek bilgi sağlar.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef enum CorDebugExceptionFlags {  
    DEBUG_EXCEPTION_NONE = 0,  
    DEBUG_EXCEPTION_CAN_BE_INTERCEPTED = 0x0001  
} CorDebugExceptionFlags;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Description|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_NONE`|Özel durum yok.|  
|`DEBUG_EXCEPTION_CAN_BE_INTERCEPTED`|Özel durum, yakabir tablodur.<br /><br /> Özel durumun zamanlaması yine de hata ayıklayıcı tarafından ele ılamıyor olabilir. Örneğin, geçerli geri aramanın altında veya bir tam zamanında (JıT) eki tarafından sonuçlanmış özel durum olayı yoksa, özel durum yakalanamaz.|  
  
## <a name="remarks"></a>Açıklamalar  

 Yeni değerler sonraki sürümlerde bu numaralandırmaya eklenebilir, bu nedenle beklenmeyen değerler için kullanılan kodu hazırlamanız gerekir `CorDebugExceptionFlags` .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Numaralandırmaları](debugging-enumerations.md)
