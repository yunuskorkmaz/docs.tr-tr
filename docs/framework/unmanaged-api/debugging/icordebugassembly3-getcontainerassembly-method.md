---
title: ICorDebugAssembly3::GetContainerAssembly Metodu
ms.date: 03/30/2017
ms.assetid: f5fddeb6-b82e-4ebb-b432-849ce8513c77
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: acb34ac2568ac88797441306820e6e762b5ac46e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
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
 `S_OK` yöntem çağrısının başarılı olursa; Aksi takdirde, `S_FALSE`, ve `ppAssembly` olan **null**.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu derleme başkalarıyla tek kapsayıcı derleme içinde birleştirilmedi varsa, bu yöntem kapsayıcı derleme döndürür. Daha fazla bilgi ve terimler için bkz: [Icordebugprocess6::enablevirtualmodulesplitting](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-enablevirtualmodulesplitting-method.md) konu.  
  
> [!NOTE]
>  Bu yöntem yalnızca .NET yerel ile kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorDebugAssembly3 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
