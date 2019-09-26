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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5d76fa4b2352da18b5ef0e547ebc4e2e99d980b8
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71273989"
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
 `COR_TYPEID` Yapı, atık toplanacak nesneler hakkında bilgi sağlayan bir dizi hata ayıklama yöntemi tarafından döndürülür. Daha sonra, bu öğe hakkında ek bilgiler sağlayan diğer hata ayıklama yöntemlerine bir bağımsız değişken olarak geçirilebilir. Örneğin, bir [ICorDebugHeapEnum](icordebugheapenum-interface.md) nesnesini numaralandırarak, yönetilen yığında tek tek nesneleri temsil eden tek tek [cor_heapobject](cor-heapobject-structure.md) nesnelerini alabilirsiniz. Ardından, nesne hakkında tür `COR_TYPEID` bilgisi sağlayan ICorDebugType nesnesini almak için `COR_HEAPOBJECT.type` alanından değeri [ICorDebugProcess5:: GetTypeForTypeID](icordebugprocess5-gettypefortypeid-method.md) metoduna geçirebilirsiniz.  
  
 Bir `COR_TYPEID` nesnenin donuk olması amaçlanmıştır. Bireysel alanlarına erişilmemelidir veya bunların kullanılması gerekir. Tek kullanımı, yöntem çağrısında bir `out` parametre olarak verilen ve daha sonra ek bilgi sağlamak için diğer yöntemlere geçirilebilecek bir tanımlayıcı olarak verilmiştir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi** CorDebug. IDL, CorDebug. h  
  
 **Kitaplığı** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Yapıları](debugging-structures.md)
- [Hata Ayıklama](index.md)
