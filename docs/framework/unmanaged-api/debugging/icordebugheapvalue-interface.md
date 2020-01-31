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
ms.openlocfilehash: fa31b8a6cc96935319e9bef3e561790b65e33a87
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777584"
---
# <a name="icordebugheapvalue-interface"></a>ICorDebugHeapValue Arabirimi

Ortak dil çalışma zamanı (CLR) atık toplayıcısı tarafından toplanan bir nesneyi temsil eden "ICorDebugValue" öğesinin bir alt sınıfı.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[CreateRelocBreakpoint Yöntemi](icordebugheapvalue-createrelocbreakpoint-method.md)|Uygulanmadı.|  
|[IsValid Yöntemi](icordebugheapvalue-isvalid-method.md)|Bu `ICorDebugHeapValue` tarafından temsil edilen nesnenin geçerli olup olmadığını veya çöp toplayıcı tarafından geri alındığını gösteren bir değer alır. Bu yöntem 2,0 .NET Framework sürümünde kullanımdan kaldırılmıştır.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
