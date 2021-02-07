---
description: ': ICorDebugMemoryBuffer:: GetStartAddress yöntemi hakkında daha fazla bilgi edinin'
title: 'ICorDebugMemoryBuffer:: GetStartAddress yöntemi'
ms.date: 03/30/2017
ms.assetid: f804d9ab-8c88-44f0-b278-5fcca7f87726
ms.openlocfilehash: 46720d70b8a1019e712b577b24dec5d4c3d5a31d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722717"
---
# <a name="icordebugmemorybuffergetstartaddress-method"></a>ICorDebugMemoryBuffer:: GetStartAddress yöntemi

Bellek arabelleğinin başlangıç adresini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetStartAddress(  
   [out] LPCVOID *address  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `address`  
 dışı Bellek arabelleğinin başlangıç adresine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!WARNING]
> Bu yöntem yalnızca .NET Native kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugMemoryBuffer Arabirimi](icordebugmemorybuffer-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
