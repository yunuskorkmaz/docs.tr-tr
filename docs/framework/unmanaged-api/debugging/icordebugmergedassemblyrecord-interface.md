---
title: ICorDebugMergedAssemblyRecord Arabirimi
ms.date: 03/30/2017
ms.assetid: fe280b11-9479-4e34-a07c-0d1ea8088422
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8fd7a5f630bcf97277a4f98f2408ecaf04883fa3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916985"
---
# <a name="icordebugmergedassemblyrecord-interface"></a>ICorDebugMergedAssemblyRecord Arabirimi
Birleştirilmiş bir derleme hakkında bilgi sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetCulture Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getculture-method.md)|Derlemenin kültür adı dizesini alır.|  
|[GetIndex Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getindex-method.md)|Derlemenin önek dizinini alır.|  
|[GetPublicKey Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getpublickey-method.md)|Derlemenin ortak anahtarını alır.|  
|[GetPublicKeyToken Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getpublickeytoken-method.md)|Derlemenin ortak anahtar belirtecini alır.|  
|[GetSimpleName Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getsimplename-method.md)|Derlemenin basit adını alır.|  
|[GetVersion Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getversion-method.md)|Derlemenin sürüm bilgilerini alır.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> Bu arabirim yalnızca .NET Native kullanılabilir. Bu arabirimi .NET Native dışında ICorDebug senaryolarında uygularsanız, ortak dil çalışma zamanı bu arabirimi yoksayar.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi** CorDebug. IDL, CorDebug. h  
  
 **Kitaplığı** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
