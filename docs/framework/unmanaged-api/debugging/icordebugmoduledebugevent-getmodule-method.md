---
title: 'Icordebugmoduledebuggevent:: GetModule yöntemi'
ms.date: 03/30/2017
ms.assetid: b1141c35-4253-4e34-b3e4-ed406a9dea4f
ms.openlocfilehash: 4d9eea8fb5c42002763a0ae52a186bf2c1e6d2ee
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792913"
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
 Modülün yüklenip yüklenmediğini veya bellekten kaldırılmadığını anlamak için [GetEventKind](icordebugdebugevent-geteventkind-method.md) metodunu çağırabilirsiniz.  
  
> [!NOTE]
> Bu yöntem yalnızca .NET Native kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugModuleDebugEvent Arabirimi](icordebugmoduledebugevent-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
