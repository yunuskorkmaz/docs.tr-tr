---
title: COR_TYPEID Yapısı
ms.date: 03/30/2017
api_name:
- COR_TYPEID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_TYPEID
helpviewer_keywords:
- COR_TYPEID structure [.NET Framework debugging]
ms.assetid: 1e172b14-ee22-4943-b3b8-3740e7bdcd2e
topic_type:
- apiref
ms.openlocfilehash: 4f6dbe8c17bd6a91078b87a87c1055fbf4977a88
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132305"
---
# <a name="cor_typeid-structure"></a>COR_TYPEID Yapısı
Bir tür tanımlayıcısı içerir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef struct COR_TYPEID{  
    UINT64 token1;  
    UINT64 token2;  
} COR_TYPEID;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`token1`|İlk belirteç.|  
|`token2`|İkinci belirteç.|  
  
## <a name="remarks"></a>Açıklamalar  
 `COR_TYPEID` yapısı, atık olarak toplanabilecek nesneler hakkında bilgi sağlayan bir dizi hata ayıklama yöntemi tarafından döndürülür. Daha sonra, bu öğe hakkında ek bilgiler sağlayan diğer hata ayıklama yöntemlerine bir bağımsız değişken olarak geçirilebilir. Örneğin, bir [ICorDebugHeapEnum](icordebugheapenum-interface.md) nesnesini numaralandırarak, yönetilen yığında tek tek nesneleri temsil eden tek tek [cor_heapobject](cor-heapobject-structure.md) nesnelerini alabilirsiniz. Ardından, nesne hakkında tür bilgisi sağlayan ICorDebugType nesnesini almak için `COR_HEAPOBJECT.type` alanından `COR_TYPEID` değerini [ICorDebugProcess5:: GetTypeForTypeID](icordebugprocess5-gettypefortypeid-method.md) metoduna geçirebilirsiniz.  
  
 `COR_TYPEID` nesnenin donuk olması amaçlanmıştır. Bireysel alanlarına erişilmemelidir veya bunların kullanılması gerekir. Tek kullanımı, yöntem çağrısında bir `out` parametresi olarak sağlanmış olan ve daha sonra ek bilgi sağlamak için diğer yöntemlere geçirilebilecek bir tanımlayıcı olarak kullanılır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Yapıları](debugging-structures.md)
- [Hata Ayıklama](index.md)
