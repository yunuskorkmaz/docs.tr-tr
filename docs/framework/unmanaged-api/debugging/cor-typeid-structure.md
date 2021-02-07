---
description: 'Daha fazla bilgi edinin: COR_TYPEID yapısı'
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
ms.openlocfilehash: fe246d544697275ffc4ea3ab6ed21c0f33863881
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99712221"
---
# <a name="cor_typeid-structure"></a>COR_TYPEID Yapısı

Bir tür tanımlayıcısı içerir.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef struct COR_TYPEID{  
    UINT64 token1;  
    UINT64 token2;  
} COR_TYPEID;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Description|  
|------------|-----------------|  
|`token1`|İlk belirteç.|  
|`token2`|İkinci belirteç.|  
  
## <a name="remarks"></a>Açıklamalar  

 `COR_TYPEID`Yapı, atık toplanacak nesneler hakkında bilgi sağlayan bir dizi hata ayıklama yöntemi tarafından döndürülür. Daha sonra, bu öğe hakkında ek bilgiler sağlayan diğer hata ayıklama yöntemlerine bir bağımsız değişken olarak geçirilebilir. Örneğin, bir [ICorDebugHeapEnum](icordebugheapenum-interface.md) nesnesini numaralandırarak, yönetilen yığında tek tek nesneleri temsil eden bağımsız [cor_heapobject](cor-heapobject-structure.md) nesneleri alabilirsiniz. Ardından, `COR_TYPEID` `COR_HEAPOBJECT.type` nesne hakkında tür bilgisi sağlayan ICorDebugType nesnesini almak için alanından değeri [ICorDebugProcess5:: GetTypeForTypeID](icordebugprocess5-gettypefortypeid-method.md) metoduna geçirebilirsiniz.  
  
 Bir `COR_TYPEID` nesnenin donuk olması amaçlanmıştır. Bireysel alanlarına erişilmemelidir veya bunların kullanılması gerekir. Tek kullanımı, yöntem çağrısında bir parametre olarak verilen ve daha sonra `out` ek bilgi sağlamak için diğer yöntemlere geçirilebilecek bir tanımlayıcı olarak verilmiştir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Yapıları](debugging-structures.md)
- [Hata Ayıklama](index.md)
