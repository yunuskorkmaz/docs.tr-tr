---
description: 'Daha fazla bilgi edinin: ICorDebugProcess5:: GetTypeFields yöntemi'
title: ICorDebugProcess5::GetTypeFields Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetTypeFields
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetTypeFields
helpviewer_keywords:
- GetTypeFields method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::GetTypeFields method [.NET Framework debugging]
ms.assetid: 6a0ad3ee-dacb-47e9-abae-4536bcc4804b
topic_type:
- apiref
ms.openlocfilehash: bdbb0be76400262d83876b9fc37cc4f00eb34e43
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99649825"
---
# <a name="icordebugprocess5gettypefields-method"></a>ICorDebugProcess5::GetTypeFields Metodu

Bir türe ait alanlar hakkında bilgi sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetTypeFields(  
    [in] COR_TYPEID id,  
    [in] ULONG32 celt,  
    [out] COR_FIELD fields[],
    [out] ULONG32 *pceltNeeded  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `id`  
 'ndaki Alan bilgilerinin alındığı türün tanımlayıcısı.  
  
 `celt`  
 'ndaki Alan bilgileri alınacak olan [COR_FIELD](cor-field-structure.md) nesne sayısı.  
  
 `fields`  
 dışı Türe ait alanlar hakkında bilgi sağlayan [COR_FIELD](cor-field-structure.md) nesneleri dizisi.  
  
 `pceltNeeded`  
 dışı İçinde bulunan [COR_FIELD](cor-field-structure.md) nesne sayısı için bir işaretçi `fields` .  
  
## <a name="remarks"></a>Açıklamalar  

 `celt`Alan bilgilerinin doldurmak için kullandığı alan sayısını belirten parametresi, `fields` alanın değerine karşılık gelmelidir `COR_TYPE_LAYOUT::numFields` .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugProcess5 Arabirimi](icordebugprocess5-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
