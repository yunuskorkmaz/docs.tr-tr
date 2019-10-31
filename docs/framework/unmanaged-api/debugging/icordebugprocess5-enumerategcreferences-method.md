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
ms.openlocfilehash: 84b5da043f9bd437ee9099135ba865c1ab23bb9d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129663"
---
# <a name="icordebugprocess5enumerategcreferences-method"></a>ICorDebugProcess5::EnumerateGCReferences Yöntemi
Bir işlemde çöp toplanabilecek tüm nesneler için bir Numaralandırıcı alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT EnumerateGCReferences(  
    [in] Bool enumerateWeakReferences,   
    [out] ICorDebugGCReferenceEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `enumerateWeakReferences`  
 'ndaki Zayıf başvuruların da oluşturulup oluşturulmayacağını gösteren bir Boolean değer. `enumerateWeakReferences` `true`, `ppEnum` Numaralandırıcı hem güçlü başvuruları hem de zayıf başvuruları içerir. `enumerateWeakReferences` `false`, Numaralandırıcı yalnızca güçlü başvurular içerir.  
  
 `ppEnum`  
 dışı Çöp toplanabilecek nesneler için bir Numaralandırıcı olan [ıcorıtcggcreferenceenum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) adresine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, bir işlemdeki yönetilen herhangi bir nesne için tam kök zinciri belirlemenin bir yolunu sağlar ve bir nesnenin neden hala etkin olduğunu tespit etmek için kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugProcess5 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
