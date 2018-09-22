---
title: ICorDebugILFrame4::GetCodeEx Metodu
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
ms.openlocfilehash: 24be4507e8ad6cde1e9c50582e352f0fc9b12ed3
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2018
ms.locfileid: "46575999"
---
# <a name="icordebugilframe4getcodeex-method"></a>ICorDebugILFrame4::GetCodeEx Metodu
[.NET Framework 4.5.2 ve sonraki sürümlerinde desteklenen]  
  
 Bu yığın çerçevesi yürütülmekte olan kod için bir işaretçi alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetCodeEx(  
   [in] ILCodeKind flags,   
   [out] ICorDebugCode **ppCode  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `flags`  
 [in] Bir [Ilcodekind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) numaralandırma üyesi, profil oluşturucunun ReJIT istek tarafından tanımlanan Ara dil (IL) çerçevede içerilip içerilmeyeceğini belirtir.  
  
 `ppCode`  
 [out] Bu yığın çerçevesi yürütme kodunu temsil eden bir "ICorDebugCode" nesnenin adresi için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem benzer [Icordebugframe::getcode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md) yöntemi dışında olan isteğe bağlı olarak kod profil oluşturucunun ReJIT istek tarafından tanımlanan erişir. İle bu yöntemin çağrılması bir `flags` değerini `ILCODE_ORIGINAL_IL` çağırmakla eşdeğerdir [GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md); yöntem işaretlenmiş ise, IL erişilemez. `ILCODE_REJIT_IL` hata ayıklayıcının profil oluşturucunun ReJIT istek tarafından tanımlanan IL erişim sağlar. IL izlenmiyor, `ppCode` olduğu **null**, ve yöntemi `S_OK`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorDebugILFrame4 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [ReJIT: Nasıl yapılır Kılavuzu](https://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
