---
title: ICorDebugProcess5::EnumerateHandles Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.EnumerateHandles
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnumerateHandles
helpviewer_keywords:
- EnumerateHandles method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateHandles method [.NET Framework debugging]
ms.assetid: 7d7fa796-0dc6-4ee8-9d56-40166246d91d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 229717ba1d7f004dc1ed020eddb2929079aa9285
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67767579"
---
# <a name="icordebugprocess5enumeratehandles-method"></a>ICorDebugProcess5::EnumerateHandles Yöntemi
Numaralandırıcı nesnesi tanıtıcıları için bir işlem olarak alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT EnumerateHandles(     [in] CorGCReferenceType types,  
    [out] ICorDebugGCReferenceEnum **ppEnum);  
```  
  
## <a name="parameters"></a>Parametreler  
 `types`  
 [in] Bitsel bir birleşimi [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) koleksiyona dahil etmek tanıtıcıları türünü belirten değer.  
  
 `ppENum`  
 [out] Adresine bir işaretçi bir [Icordebuggcreferenceenum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) atık olarak toplanmış için diğer bir deyişle bir numaralandırıcı nesneler için.  
  
## <a name="remarks"></a>Açıklamalar  
 `EnumerateHandles` tanıtıcı tablosunu incelenmesi destekleyen bir yardımcı işlevdir. Benzer [Icordebugprocess5::enumerategcreferences](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md) hariç yöntemi doldurma yerine bir [Icordebuggcreferenceenum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) atık olarak toplanmış, alınacak tüm nesneler ile koleksiyon, işleyicisi tablosundan tanıtıcıları içeren nesneleri içerir.  
  
 `types` Parametresi koleksiyona dahil etmek tanıtıcı türlerine belirtir. `types` Aşağıdaki üç üyeleri olabilir [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) sabit listesi:  
  
- `CorHandleStrongOnly` (yalnızca tanımlayıcı başvuruları tanıtıcıları).  
  
- `CorHandleWeakOnly` (yalnızca zayıf başvurular tanıtıcıları).  
  
- `CorHandleAll` (tüm tutamaçlar).  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Yapıları](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
