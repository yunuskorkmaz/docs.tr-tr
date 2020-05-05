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
ms.openlocfilehash: a889d6ba00c4a0eb96a9923a7dbe52f3b93aaba5
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795967"
---
# <a name="cordebugehclause-structure"></a>CorDebugEHClause Yapısı
[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]  
  
 Belirli bir ara dil (IL) kodu parçası için bir özel durum işleme (EH) yan tümcesini temsil eder.  
  
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
|`Flags`|EH yan tümcesindeki özel durum bilgilerini açıklayan bir bit alanı. Daha fazla bilgi için, açıklamalar bölümüne bakın.|  
|`TryOffset`|Metot gövdesinin başlangıcından itibaren `try` bloğunun bayt cinsinden değeri.|  
|`TryLength`|`try` Bloğun bayt cinsinden uzunluğu.|  
|`HandlerOffset`|Bu `try` bloktaki işleyicinin konumu.|  
|`HandlerLength`|İşleyici kodunun bayt cinsinden boyutu.|  
|`ClassToken`|Tür tabanlı özel durum işleyicisi için meta veri belirteci.|  
|`FilterOffset`|Filtre tabanlı özel durum işleyicisi için Yöntem gövdesinin başından itibaren bayt cinsinden fark.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir dizi `CoreDebugEHClause` değer, [getehyan tümceleri](icordebugilcode-getehclauses-method.md) yöntemi tarafından döndürülür.  
  
 EH yan tümce bilgileri CLı belirtimi tarafından tanımlanır. Daha fazla bilgi için bkz. [standart ECMA-355: ortak dil altyapısı (CLI), 6 Edition](https://www.ecma-international.org/publications/standards/Ecma-335.htm).  
  
 `flags` Alanda aşağıdaki bayraklar bulunabilir. Bunların CorDebug. IDL veya CorDebug. h içinde tanımlanmadığını unutmayın.  
  
|Bayrak|Değer|Açıklama|  
|----------|-----------|-----------------|  
|`COR_ILEXCEPTION_CLAUSE_EXCEPTION`|0x00000000|Türü belirtilmiş bir özel durum yan tümcesi.|  
|`COR_ILEXCEPTION_CLAUSE_FILTER`|0x00000001|Özel durum filtresi ve işleyici yan tümcesi.|  
|`COR_ILEXCEPTION_CLAUSE_FINALLY`|0x00000002|`finally` Yan tümce.|  
|`COR_ILEXCEPTION_CLAUSE_FAULT`|0x00000004|Bir fault yan tümcesi ( `finally` yalnızca bir özel durum oluştuğunda çağrılan bir yan tümce).|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [GetEHClauses Yöntemi](icordebugilcode-getehclauses-method.md)
- [Hata Ayıklama Yapıları](debugging-structures.md)
