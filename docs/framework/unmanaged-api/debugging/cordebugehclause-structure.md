---
title: CorDebugEHClause Yapısı
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- CorDebugEHClause
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 0e350a1b-6997-46d0-bfc5-962a5011ef43
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: be5d580c28a15a58cad6c5a2231d3a87e25c0e7a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54495351"
---
# <a name="cordebugehclause-structure"></a>CorDebugEHClause Yapısı
[.NET Framework 4.5.2 ve sonraki sürümlerinde desteklenen]  
  
 Bir özel durum işleme (EH) yan tümcesinde belirtilen ara dil (IL) kod parçasını temsil eder.  
  
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
|`Flags`|Özel durum bilgilerini EH yan tümcesindeki açıklayan bir bit alanı. Daha fazla bilgi için Açıklamalar bölümüne bakın.|  
|`TryOffset`|Bayt cinsinden uzaklığı, `try` yöntem gövdesini başından itibaren blok.|  
|`TryLength`|Bayt cinsinden uzunluğu, `try` blok.|  
|`HandlerOffset`|Bu işleyici konumunu `try` blok.|  
|`HandlerLength`|İşleyici kodu bayt cinsinden boyutu.|  
|`ClassToken`|Bir özel durum türüne göre işleyicisi için meta veri belirteci.|  
|`FilterOffset`|Bir filtre tabanlı özel durum işleyicisi yöntem gövdesini başından itibaren bayt cinsinden uzaklığı.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir dizi `CoreDebugEHClause` tarafından döndürülen değerler [GetEHClauses](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-getehclauses-method.md) yöntemi.  
  
 EH yan tümcesi bilgi CLI belirtimine göre tanımlanır. Daha fazla bilgi için [standart ECMA-355: Ortak dil altyapısı (CLI), 6 Edition](https://www.ecma-international.org/publications/standards/Ecma-335.htm).  
  
 `flags` Alan aşağıdaki bayraklar içerebilir. CorDebug.idl veya CorDebug.h tanımlandıkları değil olduğunu unutmayın.  
  
|Bayrağı|Değer|Açıklama|  
|----------|-----------|-----------------|  
|`COR_ILEXCEPTION_CLAUSE_EXCEPTION`|0x00000000|Türü belirtilmiş özel durum yan tümcesi.|  
|`COR_ILEXCEPTION_CLAUSE_FILTER`|0x00000001|Bir özel durum filtresi ve işleyici yan tümcesi.|  
|`COR_ILEXCEPTION_CLAUSE_FINALLY`|0x00000002|A `finally` yan tümcesi.|  
|`COR_ILEXCEPTION_CLAUSE_FAULT`|0x00000004|Bir fault tümcesinin (bir `finally` yalnızca bir özel durum oluştuğunda çağrılır yan tümcesi).|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [GetEHClauses Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-getehclauses-method.md)
- [Hata Ayıklama Yapıları](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
