---
description: 'Daha fazla bilgi edinin: CorDebugExceptionObjectStackFrame yapısı'
title: CorDebugExceptionObjectStackFrame Yapısı
ms.date: 03/30/2017
api_name:
- CorDebugExceptionObjectStackFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugExceptionObjectStackFrame
helpviewer_keywords:
- CorDebugExceptionObjectStackFrame structure [.NET Framework debugging]
ms.assetid: 542cdd81-5ae7-4361-b0ef-1ae4775df258
topic_type:
- apiref
ms.openlocfilehash: abeb5a9f6385c494745a34c6f37d6fbc1376ad7b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662162"
---
# <a name="cordebugexceptionobjectstackframe-structure"></a>CorDebugExceptionObjectStackFrame Yapısı

Bir özel durum nesnesinden yığın çerçeve bilgilerini temsil eder.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef struct CorDebugExceptionObjectStackFrame {  
    ICorDebugModule* pModule;  
    CORDB_ADDRESS ip;  
    mdMethodDef methodDef;  
    BOOL isLastForeignExceptionFrame;  
} CorDebugExceptionObjectStackFrame;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Description|  
|------------|-----------------|  
|`pModule`|Geçerli çerçeve için ICorDebugModule nesnesine yönelik bir işaretçi.|  
|`ip`|Geçerli çerçeveye ait yönerge işaretçisinin (EıP/RIP) değeri.|  
|`methodDef`|Geçerli çerçeve için yöntem belirteci.|  
|`isLastForeignExceptionFrame`|Karenin bir yabancı özel durumun son karesi olup olmadığını gösteren bir değer.|  
  
## <a name="remarks"></a>Açıklamalar  

 Çağıran, artık kullanımda olmadığında ICorDebugModule nesnesine işaretçiyi serbest bırakmalıdır.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Yapıları](debugging-structures.md)
- [Hata Ayıklama](index.md)
