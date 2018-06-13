---
title: Icordebugılframe Interface1
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame
helpviewer_keywords:
- ICorDebugILFrame interface [.NET Framework debugging]
ms.assetid: d5cf5056-da4d-4629-914d-afe42a5393df
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4a97704e00278e19181df569f108f428cb1ec90f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417751"
---
# <a name="icordebugilframe-interface1"></a>Icordebugılframe Interface1
Yığın çerçevesi Microsoft Ara dili (MSIL) kodunun temsil eder. Bu arabirim Icordebugframe arabirimi sınıfıdır.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[CanSetIP Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-cansetip-method.md)|Yönerge işaretçisi belirtilen uzaklık konuma ayarlamak güvenli olup olmadığını belirten bir değer alır.|  
|[EnumerateArguments Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratearguments-method.md)|Bir numaralandırıcı Bu çerçevede bağımsız değişkenleri alır.|  
|[EnumerateLocalVariables Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md)|Bir numaralandırıcı yerel değişkenler için bu çerçevede alır.|  
|[GetArgument Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getargument-method.md)|Belirtilen bağımsız değişkenin değeri bu MSIL yığın çerçevesinde alır.|  
|[GetIP Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getip-method.md)|Yönerge işaretçisi değerini ve nasıl yönerge işaretçisi değerini edinilen açıklayan Bitsel bir birleşimi değeri alır.|  
|[GetLocalVariable Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md)|Bu MSIL yığın çerçevesinde belirtilen yerel değişkenin değerini alır.|  
|[GetStackDepth Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getstackdepth-method.md)|Henüz uygulanmadı.|  
|[GetStackValue Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getstackvalue-method.md)|Henüz uygulanmadı.|  
|[SetIP Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md)|Yönerge işaretçisi MSIL kodda belirtilen uzaklık konumuna ayarlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorDebugILFrame` Özel Icordebugframe arabirimi bir arabirimdir. Kullanıldığı MSIL kod çerçeveleri için veya tam zamanında (JIT) için çerçeveler derlenmiş. JIT derlenmiş çerçeveleri her ikisini de uygulamak `ICorDebugILFrame` arabirimi ve Icordebugnativeframe arabirimi.  
  
> [!NOTE]
>  Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
