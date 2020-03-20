---
title: ICorDebugProcess5::EnumerateGCReferences Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.EnumerateGCReferences
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnumerateGCReferences
helpviewer_keywords:
- EnumerateGCReferences method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateGCReferences method [.NET Framework debugging]
ms.assetid: 86c397c3-81d8-463e-a248-3cbe06c44d9d
topic_type:
- apiref
ms.openlocfilehash: a97c14d83f99c847bb8569a33e175ab6eb5bccd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178617"
---
# <a name="icordebugprocess5enumerategcreferences-method"></a>ICorDebugProcess5::EnumerateGCReferences Yöntemi
Bir işlemde çöp olarak toplanacak olan tüm nesneler için bir sayısallaştırıcı alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT EnumerateGCReferences(  
    [in] Bool enumerateWeakReferences,
    [out] ICorDebugGCReferenceEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `enumerateWeakReferences`  
 [içinde] Zayıf başvuruların da numaralandırılıp numaralandırılmayacağını gösteren bir Boolean değeri. `enumerateWeakReferences` Ise, `true` `ppEnum` sayısallaştırıcı hem güçlü başvurular hem de zayıf referanslar içerir. `enumerateWeakReferences` Ise, `false`sayısallaştırıcı yalnızca güçlü başvurular içerir.  
  
 `ppEnum`  
 [çıkış] Nesnelerin çöp olarak toplanması için bir sayıyalı olan [bir ICorDebugGCReferenceEnum](icordebuggcreferenceenum-interface.md) adresine işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, bir işlemde yönetilen herhangi bir nesne için tam köklenme zincirini belirlemek için bir yol sağlar ve bir nesnenin neden hala hayatta olduğunu belirlemek için kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** CorDebug.idl, CorDebug.h  
  
 **Kütüphane:** CorGuids.lib  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugProcess5 Arabirimi](icordebugprocess5-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
