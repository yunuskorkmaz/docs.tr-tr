---
title: ICorDebugAssembly3::GetContainerAssembly Metodu
ms.date: 03/30/2017
ms.assetid: f5fddeb6-b82e-4ebb-b432-849ce8513c77
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9c01898bcbd76f7e6de9445d5d1f511203c100ed
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54585191"
---
# <a name="icordebugassembly3getcontainerassembly-method"></a>ICorDebugAssembly3::GetContainerAssembly Metodu
Bu kapsayıcı derleme döndürür `ICorDebugAssembly3` nesne.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetContainerAssembly(  
    ICorDebugAssembly **ppAssembly  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppAssembly`  
 Kapsayıcı derlemesi temsil eden Icordebugassembly nesnenin adresini bir işaretçiye veya **null** yöntem çağrısı başarısız olursa.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `S_OK` metot çağrısı başarılı olursa; Aksi takdirde, `S_FALSE`, ve `ppAssembly` olduğu **null**.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu derleme başkalarıyla tek kapsayıcı derleme içinde birleştirilmiştir, bu yöntem, kapsayıcı derleme döndürür. Daha fazla bilgi ve terimler için bkz. [Icordebugprocess6::enablevirtualmodulesplitting](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-enablevirtualmodulesplitting-method.md) konu.  
  
> [!NOTE]
>  Bu yöntem yalnızca .NET Native ile kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ICorDebugAssembly3 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
