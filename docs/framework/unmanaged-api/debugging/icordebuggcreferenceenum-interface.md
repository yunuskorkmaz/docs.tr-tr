---
description: 'Şu konuda daha fazla bilgi edinin: ıcorıtcggcreferenceenum arabirimi'
title: ICorDebugGCReferenceEnum Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugGCReferenceEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGCReferenceEnum
helpviewer_keywords:
- ICorDebugGCReferenceEnum interface [.NET Framework debugging]
ms.assetid: 5f3c91c9-c035-454f-96cc-011cab1ea06b
topic_type:
- apiref
ms.openlocfilehash: ad4a61cdc2b30fb4c8e2be500eae878327c6b449
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801299"
---
# <a name="icordebuggcreferenceenum-interface"></a>ICorDebugGCReferenceEnum Arabirimi

Çöp toplama işlemi yapılacak nesneler için bir numaralandırıcı sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Next Yöntemi](icordebuggcreferenceenum-next-method.md)|Atık olarak toplanabilecek nesneler hakkında bilgi içeren [cor_gc_reference](cor-gc-reference-structure.md) örneklerinin belirtilen sayısını alır.|  
  
## <a name="remarks"></a>Açıklamalar  

 `ICorDebugGCReferenceEnum`Arabirim "ıcorhata ayıklama Genum" arabirimini uygular.  
  
 `ICorDebugGCReferenceEnum` [ICorDebugProcess5:: EnumerateGCReferences](icordebugprocess5-enumerategcreferences-method.md) yöntemi çağırarak bir örnek [cor_gc_reference](cor-gc-reference-structure.md) örneklerle doldurulur. [Cor_gc_reference](cor-gc-reference-structure.md) nesneler [ıcorıtcggcreference:: Next](icordebuggcreferenceenum-next-method.md) yöntemi çağırarak Numaralandırılabilir.  
  
 Bu yöntem tarafından doldurulan koleksiyondaki [cor_gc_reference](cor-gc-reference-structure.md) nesneleri üç tür nesneyi temsil eder:  
  
- Tüm yönetilen yığınlardan nesneler. Bu, Yönetilen koddaki canlı başvuruları ve ortak dil çalışma zamanı tarafından oluşturulan nesneleri içerir.  
  
- Tanıtıcı tablodaki nesneler. Bu, bir modüldeki tanımlayıcı başvuruları ( `HNDTYPE_STRONG` ve `HNDTYPE_REFCOUNT` ) ve statik değişkenleri içerir.  
  
- Sonlandırıcı sırasından nesneler. Sonlandırıcı, Sonlandırıcı çalıştırılıncaya kadar kök nesneleri kuyruğa al.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
