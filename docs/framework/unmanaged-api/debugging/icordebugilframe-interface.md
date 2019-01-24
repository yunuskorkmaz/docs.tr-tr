---
title: Icordebugılframe arabirimi1
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
ms.openlocfilehash: 73cf7f26b228fa5aa458a6de312df3bf777e0206
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54580518"
---
# <a name="icordebugilframe-interface1"></a>Icordebugılframe arabirimi1
Microsoft Ara dili (MSIL) kodunun bir yığın çerçevesini temsil eder. Icordebugframe arabirimi öğesinin arabirimidir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[CanSetIP Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-cansetip-method.md)|Belirtilen uzaklık konuma yönerge işaretçisi ayarlama güvenli olup olmadığını gösteren bir değer alır.|  
|[EnumerateArguments Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratearguments-method.md)|Bir numaralandırıcı bu çerçeveye bağımsız değişkenleri alır.|  
|[EnumerateLocalVariables Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md)|Bir numaralandırıcı bu çerçevesinde yerel değişkenler için alır.|  
|[GetArgument Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getargument-method.md)|Bu MSIL yığın çerçevesi içinde belirtilen bağımsız değişkenin değerini alır.|  
|[GetIP Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getip-method.md)|Yönerge işaretçisi değerini ve nasıl yönerge işaretçisini değerini edinilen açıklayan bir karşılaştırmaya değerini alır.|  
|[GetLocalVariable Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md)|Bu MSIL yığın çerçevesi içinde belirtilen yerel değişkenin değerini alır.|  
|[GetStackDepth Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getstackdepth-method.md)|Henüz uygulanmadı.|  
|[GetStackValue Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getstackvalue-method.md)|Henüz uygulanmadı.|  
|[SetIP Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md)|MSIL kodunu belirtilen uzaklık konuma yönerge işaretçisini ayarlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorDebugILFrame` Özelleştirilmiş bir Icordebugframe arabirimi arabirimidir. Kullanıldığı çerçeveler için MSIL kod çerçeveleri veya just-in-time (JIT) için derlenmiş. JIT olarak derlenmiş çerçeveleri her ikisini de uygulamak `ICorDebugILFrame` arabirimi ve Icordebugnativeframe arabirimi.  
  
> [!NOTE]
>  Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
