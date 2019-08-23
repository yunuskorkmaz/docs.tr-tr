---
title: ICorDebugILFrame Arabirimi
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
ms.openlocfilehash: 0a40436fcf1485c5d08d175b0396af2b6870c19a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917017"
---
# <a name="icordebugilframe-interface"></a>ICorDebugILFrame Arabirimi

Microsoft ara dili (MSIL) kodunun yığın çerçevesini temsil eder. Bu arabirim, ICorDebugFrame arabiriminin bir alt sınıfıdır.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[CanSetIP Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-cansetip-method.md)|Belirtilen konum konumuna yönerge işaretçisini ayarlamak için güvenli olup olmadığını gösteren bir değer alır.|  
|[EnumerateArguments Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratearguments-method.md)|Bu çerçevedeki bağımsız değişkenler için bir Numaralandırıcı alır.|  
|[EnumerateLocalVariables Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md)|Bu çerçevedeki yerel değişkenler için bir Numaralandırıcı alır.|  
|[GetArgument Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getargument-method.md)|Bu MSIL yığın çerçevesindeki belirtilen bağımsız değişkenin değerini alır.|  
|[GetIP Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getip-method.md)|Yönerge işaretçisinin değerini ve yönerge işaretçisi değerinin nasıl elde edileceğini açıklayan bit düzeyinde birleşim değerini alır.|  
|[GetLocalVariable Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md)|Bu MSIL yığın çerçevesinde belirtilen yerel değişkenin değerini alır.|  
|[GetStackDepth Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getstackdepth-method.md)|Uygulanmadı.|  
|[GetStackValue Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getstackvalue-method.md)|Uygulanmadı.|  
|[SetIP Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md)|Yönerge işaretçisini MSIL kodunda belirtilen konum konumunu ayarlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Arabirim `ICorDebugILFrame` , özelleştirilmiş bir ICorDebugFrame arabirimidir. MSIL kod çerçeveleri ya da tam zamanında (JıT) derlenmiş çerçeveler için kullanılır. JIT ile derlenen çerçeveler hem `ICorDebugILFrame` arabirimini hem de ICorDebugNativeFrame arabirimini uygular.  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi** CorDebug. IDL, CorDebug. h  
  
 **Kitaplığı** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
