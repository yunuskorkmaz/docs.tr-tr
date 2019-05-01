---
title: ICorDebugILFrame4::GetCodeEx Yöntemi
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILFrame4.GetLocalVariableEx
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: aeda0e42-29ee-4ca8-9f21-ac4641677a62
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6d61981d26d21ec1e5e24093817586ebf45b129e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988487"
---
# <a name="icordebugilframe4getcodeex-method"></a>ICorDebugILFrame4::GetCodeEx Yöntemi
[.NET Framework 4.5.2 ve sonraki sürümlerinde desteklenen]  
  
 Bu yığın çerçevesi yürütülmekte olan kod için bir işaretçi alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetCodeEx(  
   [in] ILCodeKind flags,   
   [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `flags`  
 [in] Bir [Ilcodekind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) numaralandırma üyesi, profil oluşturucunun ReJIT istek tarafından tanımlanan Ara dil (IL) çerçevede içerilip içerilmeyeceğini belirtir.  
  
 `ppCode`  
 [out] Bu yığın çerçevesi yürütme kodunu temsil eden bir "ICorDebugCode" nesnenin adresi için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem benzer [Icordebugframe::getcode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md) yöntemi dışında olan isteğe bağlı olarak kod profil oluşturucunun ReJIT istek tarafından tanımlanan erişir. İle bu yöntemin çağrılması bir `flags` değerini `ILCODE_ORIGINAL_IL` çağırmakla eşdeğerdir [GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md); yöntem işaretlenmiş ise, IL erişilemez. `ILCODE_REJIT_IL` hata ayıklayıcının profil oluşturucunun ReJIT istek tarafından tanımlanan IL erişim sağlar. IL izlenmiyor, `ppCode` olduğu **null**, ve yöntemi `S_OK`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugILFrame4 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [ReJIT: Nasıl yapılır Kılavuzu](https://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
