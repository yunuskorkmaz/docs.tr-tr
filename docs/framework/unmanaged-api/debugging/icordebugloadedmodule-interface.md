---
description: ': ICorDebugLoadedModule arabirimi hakkında daha fazla bilgi edinin'
title: ICorDebugLoadedModule Arabirimi
ms.date: 03/30/2017
ms.assetid: 34be6369-2e75-4a95-a538-3b29ac97cf6d
ms.openlocfilehash: 6a1b466a9d2d7781fad7ac2bc8c24f0b2a5c23e0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801234"
---
# <a name="icordebugloadedmodule-interface"></a>ICorDebugLoadedModule Arabirimi

Yüklü bir modül hakkında bilgi sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetBaseAddress Yöntemi](icordebugloadedmodule-getbaseaddress-method.md)|Yüklenen modülün temel adresini alır.|  
|[GetName Yöntemi](icordebugloadedmodule-getname-method.md)|Yüklenen modülün adını alır.|  
|[GetSize Yöntemi](icordebugloadedmodule-getsize-method.md)|Yüklenen modülün bayt cinsinden boyutunu alır.|  
  
## <a name="remarks"></a>Açıklamalar  

 `ICorDebugLoadedModule`Arabirim bir hata ayıklayıcı tarafından uygulanır ve hata ayıklayıcıdan yüklenen modül hakkında bilgi almak IÇIN clr hata ayıklama arabirimleri tarafından kullanılır.  
  
> [!NOTE]
> Bu arabirim yalnızca .NET Native kullanılabilir. Bu arabirimi .NET Native dışında ICorDebug senaryolarında uygularsanız, ortak dil çalışma zamanı bu arabirimi yoksayar.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
- [Hata Ayıklama](index.md)
