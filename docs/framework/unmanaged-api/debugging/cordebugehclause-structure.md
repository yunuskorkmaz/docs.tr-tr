---
title: "CorDebugEHClause Yapısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: CorDebugEHClause
api_location: mscordbi.dll
api_type: COM
ms.assetid: 0e350a1b-6997-46d0-bfc5-962a5011ef43
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 97428837d78c246915381b51fb5005a68518b7bc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugehclause-structure"></a>CorDebugEHClause Yapısı
[.NET Framework 4.5.2 ve sonraki sürümlerinde desteklenen]  
  
 Bir özel durum işleme için belirli bir ara dile (IL) kod (EH) yan tümcesinin temsil eder.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
typedef struct _CorDebugEHClause {  
   ULONG32 Flags;  
   ULONG32 TryOffset;  
   ULONG32 TryLength;  
   ULONG32 HandlerOffset;  
   ULONG32 HandlerLength;  
   ULONG32 ClassToken;  
   ULONG32 FilterOffset;  
} CorDebugEHClause;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`Flags`|Özel durum bilgilerini EH yan tümcesinde açıklar bir bit alanı. Daha fazla bilgi için Açıklamalar bölümüne bakın.|  
|`TryOffset`|Bayt cinsinden uzaklık, `try` blok yöntem gövdesi başlangıcı.|  
|`TryLength`|Bayt cinsinden uzunluğu, `try` bloğu.|  
|`HandlerOffset`|Bu işleyici konumunu `try` bloğu.|  
|`HandlerLength`|İşleyici kod bayt cinsinden boyutu.|  
|`ClassToken`|Meta veri simgesi türü dayalı bir özel durum işleyicisi.|  
|`FilterOffset`|Bir filtre dayalı bir özel durum işleyicisi yöntem gövdesi başından bayt uzaklığı.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir dizi `CoreDebugEHClause` değerleri tarafından döndürülen [GetEHClauses](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-getehclauses-method.md) yöntemi.  
  
 EH yan tümcesi bilgi CLI belirtimine göre tanımlanır. Daha fazla bilgi için bkz: [standart ECMA-355: ortak dil altyapısı (CLI), 6 Edition](http://www.ecma-international.org/publications/standards/Ecma-335.htm).  
  
 `flags` Alan aşağıdaki bayraklar içerebilir. Bunlar CorDebug.idl veya CorDebug.h tanımlanmayan olduğunu unutmayın.  
  
|Bayrağı|Değer|Açıklama|  
|----------|-----------|-----------------|  
|`COR_ILEXCEPTION_CLAUSE_EXCEPTION`|0x00000000|Türü belirtilmiş özel durum yan tümcesi.|  
|`COR_ILEXCEPTION_CLAUSE_FILTER`|0x00000001|Bir özel durum filtresi ve işleyici yan tümcesi.|  
|`COR_ILEXCEPTION_CLAUSE_FINALLY`|0x00000002|A `finally` yan tümcesi.|  
|`COR_ILEXCEPTION_CLAUSE_FAULT`|0x00000004|Bir arıza yan tümcesi (bir `finally` yalnızca bir özel durum oluştuğunda çağrılır yan tümcesi).|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [GetEHClauses Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-getehclauses-method.md)  
 [Hata Ayıklama Yapıları](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
