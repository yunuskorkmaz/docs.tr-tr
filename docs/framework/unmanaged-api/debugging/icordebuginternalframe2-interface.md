---
title: ICorDebugInternalFrame2 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugInternalFrame2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame2
helpviewer_keywords:
- ICorDebugInternalFrame2 interface [.NET Framework debugging]
ms.assetid: d4755569-85b8-4ff4-bf50-0e608e76429f
topic_type:
- apiref
ms.openlocfilehash: a17c46d5ef08963bb0d7fc280ba8b90531e41c5b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719638"
---
# <a name="icordebuginternalframe2-interface"></a>ICorDebugInternalFrame2 Arabirimi

Yığın adresi ve ICorDebugFrame nesneleriyle ilişkili konum dahil olmak üzere iç çerçeveler hakkında bilgi sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetFrameAddress Yöntemi](icordebuginternalframe2-getframeaddress-method.md)|İç çerçevenin yığın adresini döndürür.|  
|[IsCloserToLeaf Yöntemi](icordebuginternalframe2-isclosertoleaf-method.md)|`this`İç karenin belirtilen ICorDebugFrame nesnesinden daha yakın olup olmadığını denetler.|  
  
## <a name="remarks"></a>Açıklamalar  

 Bu arabirim, ICorDebugInternalFrame arabirimini genişletir.  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
- [Hata Ayıklama](index.md)
