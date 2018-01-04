---
title: ICorDebugMergedAssemblyRecord arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: fe280b11-9479-4e34-a07c-0d1ea8088422
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6086d1a82b5f086d857ac612a9d454a6ed77ba1f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmergedassemblyrecord-interface"></a>ICorDebugMergedAssemblyRecord arabirimi
Birleştirilmiş bir derleme hakkında bilgi sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetCulture Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getculture-method.md)|Derleme kültür adı dizesini alır.|  
|[GetIndex Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getindex-method.md)|Derlemenin ön eki dizinini alır.|  
|[GetPublicKey Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getpublickey-method.md)|Derlemenin ortak anahtarı alır.|  
|[GetPublicKeyToken Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getpublickeytoken-method.md)|Derlemenin ortak anahtar belirteci alır.|  
|[GetSimpleName Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getsimplename-method.md)|Basit derlemenin adını alır.|  
|[GetVersion Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getversion-method.md)|Derlemenin sürüm bilgisi alır.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
>  Bu arabirim yalnızca .NET yerel ile kullanılabilir. Bu arabirim .NET yerel dışında Icordebug senaryoları için uygularsanız, ortak dil çalışma zamanı bu arabirim göz ardı eder.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
