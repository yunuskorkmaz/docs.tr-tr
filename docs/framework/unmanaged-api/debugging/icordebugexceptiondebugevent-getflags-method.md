---
description: ': Icordebugexceptiondebugger gevent:: GetFlags yöntemi hakkında daha fazla bilgi edinin'
title: 'Icordebugexceptiondebugger gevent:: GetFlags metodu'
ms.date: 03/30/2017
ms.assetid: 73225303-8852-487e-9a0e-9f0cb95e99d9
ms.openlocfilehash: 54a6c9b0dff2346ca130f80e72fe06dbb3017f10
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693479"
---
# <a name="icordebugexceptiondebugeventgetflags-method"></a>Icordebugexceptiondebugger gevent:: GetFlags metodu

Özel durumun yakalanıp yakalanamayacağını gösteren bir bayrak alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetFlags(  
   [out] CorDebugExceptionFlags *pdwFlags  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pdwFlags`  
 dışı Özel durumun yakalanıp yakalanamayacağını belirten [CorDebugExceptionFlags](cordebugexceptionflags-enumeration.md) değerine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> Bu yöntem yalnızca .NET Native kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugExceptionDebugEvent Arabirimi](icordebugexceptiondebugevent-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
