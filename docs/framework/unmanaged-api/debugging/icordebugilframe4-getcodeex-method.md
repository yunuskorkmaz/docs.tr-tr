---
title: ICorDebugILFrame4::GetCodeEx Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: ICorDebugILFrame4.GetLocalVariableEx
api_location: mscordbi.dll
api_type: COM
ms.assetid: aeda0e42-29ee-4ca8-9f21-ac4641677a62
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: fc80882353bd7a9861f4db79b83493d1cef7bfee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugilframe4getcodeex-method"></a>ICorDebugILFrame4::GetCodeEx Metodu
[.NET Framework 4.5.2 ve sonraki sürümlerinde desteklenen]  
  
 Bir işaretçi Bu yığın çerçevesi yürütülen kodu alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetCodeEx(  
   [in] ILCodeKind flags,   
   [out] ICorDebugCode **ppCode  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `flags`  
 [in] Bir [Ilcodekind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) Profil Oluşturucu'nın ReJIT isteği tarafından tanımlanan Ara dile (IL) çerçevede dahil edilip edilmediğini belirten numaralandırma üyesi.  
  
 `ppCode`  
 [out] Bir işaretçi adresine "ICorDebugCode" nesnenin Bu yığın çerçevesi yürütüyor kodunu temsil eder.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem benzer [Icordebugframe::getcode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md) olan isteğe bağlı olarak kod Profil Oluşturucu'nın ReJIT isteği tarafından tanımlanan erişen dışında yöntemi. Bu yöntem çağırma bir `flags` değerini `ILCODE_ORIGINAL_IL` arama için eşdeğer bir gruba [GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md); yöntemi sürümlerde desteklenir, kendi IL erişilemeyecek. `ILCODE_REJIT_IL`Profil Oluşturucu'nın ReJIT isteği tarafından tanımlanan IL erişmek hata ayıklayıcı sağlar. IL izlenmemektedir, `ppCode` olan **null**, ve yöntemi `S_OK`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Icordebugılframe4 arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)  
 [Hata ayıklama arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [ReJIT: Nasıl yapılır Kılavuzu](http://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
