---
title: ICorDebugNativeFrame2 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame2
helpviewer_keywords:
- ICorDebugNativeFrame2 interface [.NET Framework debugging]
ms.assetid: 52a80838-af36-4399-bc97-d8a4c6d76df2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 638ce7933ededf2ff7b03b1c5aed7f6bdbfebc6c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912789"
---
# <a name="icordebugnativeframe2-interface"></a>ICorDebugNativeFrame2 Arabirimi
Alt ve üst çerçeve ilişkilerini sınayan yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[IsChild Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ischild-method.md)|Geçerli çerçevenin bir alt çerçeve olup olmadığını belirler.|  
|[IsMatchingParentFrame Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ismatchingparentframe-method.md)|Belirtilen çerçevenin geçerli çerçevenin üst öğesi olup olmadığını belirler.|  
|[GetStackParameterSize Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-getstackparametersize-method.md)|X86 işletim sistemlerindeki yığındaki parametrelerin birikmiş boyutunu döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu arabirim "ICorDebugNativeFrame" arabirimini mantıksal olarak genişletir.  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi** CorDebug. IDL, CorDebug. h  
  
 **Kitaplığı** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
