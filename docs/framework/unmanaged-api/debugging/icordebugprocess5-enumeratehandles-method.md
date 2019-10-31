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
ms.openlocfilehash: e0e68dba1f4d9ac5fa618aa842b823dcc046e70e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129675"
---
# <a name="icordebugprocess5enumeratehandles-method"></a>ICorDebugProcess5::EnumerateHandles Yöntemi
İşlemdeki nesne tanıtıcıları için bir Numaralandırıcı alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT EnumerateHandles(     [in] CorGCReferenceType types,  
    [out] ICorDebugGCReferenceEnum **ppEnum);  
```  
  
## <a name="parameters"></a>Parametreler  
 `types`  
 'ndaki Koleksiyona eklenecek tanıtıcıların türünü belirten [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) değerlerinin bit düzeyinde birleşimi.  
  
 `ppENum`  
 dışı Çöp toplanabilecek nesneler için bir Numaralandırıcı olan [ıcorıtcggcreferenceenum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) adresine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 `EnumerateHandles`, tanıtıcı tablosunun incelemesini destekleyen bir yardımcı işlevdir. [ICorDebugProcess5:: EnumerateGCReferences](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md) yöntemine benzer, ancak tüm nesneler atık toplama olacak şekilde bir [ıcorıtcggcreferenceenum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) koleksiyonu doldurmaktansa, yalnızca tanıtıcılara sahip olan nesneleri içerir. tanıtıcı tablosu.  
  
 `types` parametresi, koleksiyona dahil edilecek tanıtıcı türlerini belirtir. `types`, [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) numaralandırması için aşağıdaki üç üyenin herhangi biri olabilir:  
  
- `CorHandleStrongOnly` (yalnızca güçlü başvurulara yönelik tanıtıcılardır).  
  
- `CorHandleWeakOnly` (yalnızca zayıf başvurulara yönelik tanıtıcılardır).  
  
- `CorHandleAll` (tüm tutamaçlar).  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Yapıları](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
