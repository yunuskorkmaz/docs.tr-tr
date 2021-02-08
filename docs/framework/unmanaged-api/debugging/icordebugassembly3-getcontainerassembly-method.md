---
description: ': ICorDebugAssembly3:: GetContainerAssembly yöntemi hakkında daha fazla bilgi edinin'
title: ICorDebugAssembly3::GetContainerAssembly Yöntemi
ms.date: 03/30/2017
ms.assetid: f5fddeb6-b82e-4ebb-b432-849ce8513c77
ms.openlocfilehash: 5a6bc6dfb1c8403137a9444ff1cc4f64e75da65d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791523"
---
# <a name="icordebugassembly3getcontainerassembly-method"></a>ICorDebugAssembly3::GetContainerAssembly Yöntemi

Bu nesnenin kapsayıcı derlemesini döndürür `ICorDebugAssembly3` .  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetContainerAssembly(  
    ICorDebugAssembly **ppAssembly  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `ppAssembly`  
 Kapsayıcı derlemesini temsil eden bir ICorDebugAssembly nesnesinin adresine yönelik bir işaretçi veya yöntem çağrısı başarısız olursa **null** .  
  
## <a name="return-value"></a>Dönüş Değeri  

 `S_OK` Yöntem çağrısı başarılı olursa; Aksi halde, `S_FALSE` , `ppAssembly` ve **null**.  
  
## <a name="remarks"></a>Açıklamalar  

 Bu derleme, tek bir kapsayıcı derlemesi içindeki diğer kullanıcılarla birleştirilmişse, bu yöntem kapsayıcı derlemesini döndürür. Daha fazla bilgi ve terminoloji için [ICorDebugProcess6:: Enablevirtualmodulebölünmesi](icordebugprocess6-enablevirtualmodulesplitting-method.md) konusuna bakın.  
  
> [!NOTE]
> Bu yöntem yalnızca .NET Native kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugAssembly3 Arabirimi](icordebugassembly3-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
