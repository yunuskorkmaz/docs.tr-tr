---
title: ICorDebugClass2 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugClass2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass2
helpviewer_keywords:
- ICorDebugClass2 interface [.NET Framework debugging]
ms.assetid: 5416de70-43f2-4cdf-a11f-d570759c9c0c
topic_type:
- apiref
ms.openlocfilehash: ce3f289ae914817071fad5274c45d1e5fae71a06
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717987"
---
# <a name="icordebugclass2-interface"></a>ICorDebugClass2 Arabirimi

Bir genel sınıfı veya türünde bir yöntem parametresi olan bir sınıfı temsil eder <xref:System.Type> . Bu arabirim [ICorDebugClass](icordebugclass-interface.md)'ı genişletir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetParameterizedType Yöntemi](icordebugclass2-getparameterizedtype-method.md)|Bu sınıf için tür bildirimini alır.|  
|[SetJMCStatus Yöntemi](icordebugclass2-setjmcstatus-method.md)|Bu sınıfın her bir yöntemi için, yöntemin Kullanıcı tanımlı kod olup olmadığını belirten bir değer ayarlar.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugClass Arabirimi](icordebugclass-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
