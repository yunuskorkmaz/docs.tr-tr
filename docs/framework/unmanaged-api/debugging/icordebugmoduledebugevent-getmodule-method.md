---
title: 'Icordebugmoduledebuggevent:: GetModule yöntemi'
ms.date: 03/30/2017
ms.assetid: b1141c35-4253-4e34-b3e4-ed406a9dea4f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e68fab11a881854ae4c3fe073f73150694d31ae5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965103"
---
# <a name="icordebugmoduledebugeventgetmodule-method"></a>Icordebugmoduledebuggevent:: GetModule yöntemi
Yeni yüklenen veya kaldırılan birleştirilmiş modülü alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetModule(  
   [out]ICorDebugModule **ppModule  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ppModule`  
 dışı Yeni yüklenen veya kaldırılan birleştirilmiş modülü temsil eden ICorDebugModule nesnesinin adresine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Modülün yüklenip yüklenmediğini veya bellekten kaldırılmadığını anlamak için [GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) metodunu çağırabilirsiniz.  
  
> [!NOTE]
> Bu yöntem yalnızca .NET Native kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi** CorDebug. IDL, CorDebug. h  
  
 **Kitaplığı** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugModuleDebugEvent Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
