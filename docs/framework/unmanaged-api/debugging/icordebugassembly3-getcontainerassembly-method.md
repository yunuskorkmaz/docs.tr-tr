---
title: ICorDebugAssembly3::GetContainerAssembly Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: f5fddeb6-b82e-4ebb-b432-849ce8513c77
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f9a32520c2a67c0bc51a3f88e9822db49e4a3974
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugassembly3getcontainerassembly-method"></a>ICorDebugAssembly3::GetContainerAssembly Metodu
Bu kapsayıcı derleme döndürür `ICorDebugAssembly3` nesnesi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetContainerAssembly(  
    ICorDebugAssembly **ppAssembly  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppAssembly`  
 Kapsayıcı derleme temsil eden Icordebugassembly nesne adresini gösteren bir işaretçi veya **null** yöntem çağrısının başarısız olursa.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `S_OK`yöntem çağrısının başarılı olursa; Aksi takdirde, `S_FALSE`, ve `ppAssembly` olan **null**.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu derleme başkalarıyla tek kapsayıcı derleme içinde birleştirilmedi varsa, bu yöntem kapsayıcı derleme döndürür. Daha fazla bilgi ve terimler için bkz: [Icordebugprocess6::enablevirtualmodulesplitting](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-enablevirtualmodulesplitting-method.md) konu.  
  
> [!NOTE]
>  Bu yöntem yalnızca .NET yerel ile kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Icordebugassembly3 arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)  
 [Hata ayıklama arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
