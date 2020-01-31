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
ms.openlocfilehash: 81993f108ae9b59300b5d29402d7a423c3657757
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792442"
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
 dışı Çöp toplanabilecek nesneler için bir Numaralandırıcı olan [ıcorıtcggcreferenceenum](icordebuggcreferenceenum-interface.md) adresine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, bir işlemdeki yönetilen herhangi bir nesne için tam kök zinciri belirlemenin bir yolunu sağlar ve bir nesnenin neden hala etkin olduğunu tespit etmek için kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugProcess5 Arabirimi](icordebugprocess5-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
