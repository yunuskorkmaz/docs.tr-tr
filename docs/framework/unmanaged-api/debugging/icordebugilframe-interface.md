---
title: "Icordebugılframe Interface1"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugILFrame
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugILFrame
helpviewer_keywords: ICorDebugILFrame interface [.NET Framework debugging]
ms.assetid: d5cf5056-da4d-4629-914d-afe42a5393df
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d8d370fa971f698eb694127c72ff96499b85143d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugilframe-interface1"></a>Icordebugılframe Interface1
Yığın çerçevesi Microsoft Ara dili (MSIL) kodunun temsil eder. Bu arabirim Icordebugframe arabirimi sınıfıdır.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Cansetıp yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-cansetip-method.md)|Yönerge işaretçisi belirtilen uzaklık konuma ayarlamak güvenli olup olmadığını belirten bir değer alır.|  
|[EnumerateArguments yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratearguments-method.md)|Bir numaralandırıcı Bu çerçevede bağımsız değişkenleri alır.|  
|[EnumerateLocalVariables yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md)|Bir numaralandırıcı yerel değişkenler için bu çerçevede alır.|  
|[GetArgument yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getargument-method.md)|Belirtilen bağımsız değişkenin değeri bu MSIL yığın çerçevesinde alır.|  
|[Getıp yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getip-method.md)|Yönerge işaretçisi değerini ve nasıl yönerge işaretçisi değerini edinilen açıklayan Bitsel bir birleşimi değeri alır.|  
|[GetLocalVariable yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md)|Bu MSIL yığın çerçevesinde belirtilen yerel değişkenin değerini alır.|  
|[GetStackDepth yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getstackdepth-method.md)|Henüz uygulanmadı.|  
|[GetStackValue yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getstackvalue-method.md)|Henüz uygulanmadı.|  
|[SetIP yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md)|Yönerge işaretçisi MSIL kodda belirtilen uzaklık konumuna ayarlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorDebugILFrame` Özel Icordebugframe arabirimi bir arabirimdir. Kullanıldığı MSIL kod çerçeveleri için veya tam zamanında (JIT) için çerçeveler derlenmiş. JIT derlenmiş çerçeveleri her ikisini de uygulamak `ICorDebugILFrame` arabirimi ve Icordebugnativeframe arabirimi.  
  
> [!NOTE]
>  Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata ayıklama arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
