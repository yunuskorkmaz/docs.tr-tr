---
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
ms.openlocfilehash: 45de821dd52f7e153fc79ffde056ed959c654fce
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795969"
---
# <a name="cordebugexceptionflags-enumeration"></a>CorDebugExceptionFlags Numaralandırması
Bir özel durum hakkında ek bilgi sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef enum CorDebugExceptionFlags {  
    DEBUG_EXCEPTION_NONE = 0,  
    DEBUG_EXCEPTION_CAN_BE_INTERCEPTED = 0x0001  
} CorDebugExceptionFlags;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_NONE`|Özel durum yok.|  
|`DEBUG_EXCEPTION_CAN_BE_INTERCEPTED`|Özel durum, yakabir tablodur.<br /><br /> Özel durumun zamanlaması yine de hata ayıklayıcı tarafından ele ılamıyor olabilir. Örneğin, geçerli geri aramanın altında veya bir tam zamanında (JıT) eki tarafından sonuçlanmış özel durum olayı yoksa, özel durum yakalanamaz.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yeni değerler sonraki sürümlerde bu numaralandırmaya eklenebilir, bu nedenle beklenmeyen değerler için kullanılan `CorDebugExceptionFlags` kodu hazırlamanız gerekir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Numaralandırmaları](debugging-enumerations.md)
