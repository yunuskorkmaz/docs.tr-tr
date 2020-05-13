---
title: ICorDebugHeapValue Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue
helpviewer_keywords:
- ICorDebugHeapValue interface [.NET Framework debugging]
ms.assetid: 1bca66db-0359-4ae8-846e-e35f7e547e8b
topic_type:
- apiref
ms.openlocfilehash: 36a485413490045ca49b99fca4fe5d43edc37114
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213016"
---
# <a name="icordebugheapvalue-interface"></a>ICorDebugHeapValue Arabirimi

Ortak dil çalışma zamanı (CLR) atık toplayıcısı tarafından toplanan bir nesneyi temsil eden "ICorDebugValue" öğesinin bir alt sınıfı.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[CreateRelocBreakpoint Yöntemi](icordebugheapvalue-createrelocbreakpoint-method.md)|Uygulanmaz.|  
|[IsValid Yöntemi](icordebugheapvalue-isvalid-method.md)|Tarafından temsil edilen nesnenin geçerli olup olmadığını `ICorDebugHeapValue` veya çöp toplayıcı tarafından geri kazanıldığını belirten bir değer alır. Bu yöntem 2,0 .NET Framework sürümünde kullanımdan kaldırılmıştır.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
