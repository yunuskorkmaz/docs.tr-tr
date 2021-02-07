---
description: 'Daha fazla bilgi edinin: CorDebugBlockingReason numaralandırması'
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
ms.openlocfilehash: c2d9c805549d046fe40ab5ea00f30e2fd0a680a3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747119"
---
# <a name="cordebugblockingreason-enumeration"></a>CorDebugBlockingReason Numaralandırması

Bir iş parçacığının belirli bir nesne üzerinde engellenip engellenme nedenlerini belirtir.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
Typedef enum CorDebugBlockingReason  
{  
   BLOCKING_NONE = 0  
   BLOCKING_MONITOR_CRITICAL_SECTION = 1  
   BLOCKING_MONITOR_EVENT = 2  
}  CorDebugBlockingReason;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Description|  
|------------|-----------------|  
|`BLOCKING_NONE`|Yalnızca iç kullanım.|  
|`BLOCKING_MONITOR_CRITICAL_SECTION`|Bir iş parçacığı, bir nesne üzerindeki izleyici kilidi ile ilişkili kritik bölümü almaya çalışıyor. Genellikle, veya yöntemlerinden birini çağırdığınızda bu durum oluşur <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> .|  
|`BLOCKING_MONITOR_EVENT`|Bir iş parçacığı bir nesne için izleyici kilidi ile ilişkili olayı bekliyor. Genellikle, bu yöntemlerden birini çağırdığınızda oluşur <xref:System.Threading.Monitor?displayProperty=nameWithType> `Wait` .|  
  
## <a name="remarks"></a>Açıklamalar  

 `BLOCKING_MONITOR_CRITICAL_SECTION`Veya `BLOCKING_MONITOR_EVENT` üyesi bir [CorDebugBlockingObject](cordebugblockingobject-structure.md) yapısında kullanıldığında, `pBlockingObject` yapının üyesi, girilmekte olan nesneyi temsil eden bir "ICorDebugValue" arabirimine işaret eder. Ayrıca, [ICorDebugHeapValue3](icordebugheapvalue3-interface.md) arabirimini uygulamak da garanti edilir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Numaralandırmaları](debugging-enumerations.md)
- [Hata Ayıklama](index.md)
