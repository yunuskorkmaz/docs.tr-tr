---
description: 'Daha fazla bilgi edinin: ICorDebugProcess5:: EnumerateHandles yöntemi'
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
ms.openlocfilehash: 62ca1390ceec634e6651dc013345688fe5892bcd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99649916"
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
 'ndaki Koleksiyona eklenecek tanıtıcıların türünü belirten [CorGCReferenceType](corgcreferencetype-enumeration.md) değerlerinin bit düzeyinde birleşimi.  
  
 `ppENum`  
 dışı Çöp toplanabilecek nesneler için bir Numaralandırıcı olan [ıcorıtcggcreferenceenum](icordebuggcreferenceenum-interface.md) adresine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  

 `EnumerateHandles` , tanıtıcı tablosunun incelemesini destekleyen bir yardımcı işlevdir. [ICorDebugProcess5:: EnumerateGCReferences](icordebugprocess5-enumerategcreferences-method.md) yöntemine benzer, ancak tüm nesneler ile bir [ıcorıtcggcreferenceenum](icordebuggcreferenceenum-interface.md) koleksiyonu yerleştirmek yerine yalnızca tanıtıcı tablosundan tanıtıcılara sahip nesneleri içerir.  
  
 `types`Parametresi, koleksiyona dahil edilecek tanıtıcı türlerini belirtir. `types`[CorGCReferenceType](corgcreferencetype-enumeration.md) numaralandırması için aşağıdaki üç üyenin herhangi biri olabilir:  
  
- `CorHandleStrongOnly` (yalnızca güçlü başvurulara yönelik tanıtıcılardır).  
  
- `CorHandleWeakOnly` (yalnızca zayıf başvurulara yönelik tanıtıcılardır).  
  
- `CorHandleAll` (tüm tutamaçlar).  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Yapıları](debugging-structures.md)
- [Hata Ayıklama](index.md)
