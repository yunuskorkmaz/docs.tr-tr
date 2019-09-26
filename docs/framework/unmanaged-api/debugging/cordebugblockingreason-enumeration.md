---
title: CorDebugBlockingReason Numaralandırması
ms.date: 03/30/2017
api_name:
- CorDebugBlockingReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugBlockingReason
helpviewer_keywords:
- CorDebugBlockingReason enumeration [.NET Framework debugging]
ms.assetid: a6ac2531-ddfe-46fd-88fe-8b1eabe0b255
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 99fcf160b3e3b2b238520e3db5ba2e74b270380a
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274137"
---
# <a name="cordebugblockingreason-enumeration"></a>CorDebugBlockingReason Numaralandırması
Bir iş parçacığının belirli bir nesne üzerinde engellenip engellenme nedenlerini belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
Typedef enum CorDebugBlockingReason  
{  
   BLOCKING_NONE = 0  
   BLOCKING_MONITOR_CRITICAL_SECTION = 1  
   BLOCKING_MONITOR_EVENT = 2  
}  CorDebugBlockingReason;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`BLOCKING_NONE`|Yalnızca iç kullanım.|  
|`BLOCKING_MONITOR_CRITICAL_SECTION`|Bir iş parçacığı, bir nesne üzerindeki izleyici kilidi ile ilişkili kritik bölümü almaya çalışıyor. Genellikle, <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> veya <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> yöntemlerinden birini çağırdığınızda bu durum oluşur.|  
|`BLOCKING_MONITOR_EVENT`|Bir iş parçacığı bir nesne için izleyici kilidi ile ilişkili olayı bekliyor. Genellikle, bu <xref:System.Threading.Monitor?displayProperty=nameWithType> `Wait` yöntemlerden birini çağırdığınızda oluşur.|  
  
## <a name="remarks"></a>Açıklamalar  
 Veya üyesi bir [CorDebugBlockingObject](cordebugblockingobject-structure.md) yapısında kullanıldığında, yapının üyesi,girilmekteolannesneyitemsiledenbir"ICorDebugValue"arabirimineişareteder.`pBlockingObject` `BLOCKING_MONITOR_EVENT` `BLOCKING_MONITOR_CRITICAL_SECTION` Ayrıca, [ICorDebugHeapValue3](icordebugheapvalue3-interface.md) arabirimini uygulamak da garanti edilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi** CorDebug. IDL, CorDebug. h  
  
 **Kitaplığı** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Sabit Listeleri](debugging-enumerations.md)
- [Hata Ayıklama](index.md)
