---
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
ms.openlocfilehash: 0045285a3da22f468c2426bb3b9c4ae7e3e1d7c7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132665"
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
 'ndaki Alan bilgileri alınacak olan [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) nesnelerinin sayısı.  
  
 `fields`  
 dışı Türe ait alanlar hakkında bilgi sağlayan bir [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) nesneleri dizisi.  
  
 `pceltNeeded`  
 dışı `fields`bulunan [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) nesnelerinin sayısına yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Alan bilgilerini yöntemin `fields`doldurmak için kullandığı alan sayısını belirten `celt` parametresi, `COR_TYPE_LAYOUT::numFields` alanının değerine karşılık gelmelidir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugProcess5 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
