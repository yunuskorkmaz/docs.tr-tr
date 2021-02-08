---
description: ': ICorDebugILFrame Arabirimi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 251fa18151ff286bee3e1bcf7707bf5f7145b4f1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791367"
---
# <a name="icordebugilframe-interface"></a>ICorDebugILFrame Arabirimi

Microsoft ara dili (MSIL) kodunun yığın çerçevesini temsil eder. Bu arabirim, ICorDebugFrame arabiriminin bir alt sınıfıdır.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[CanSetIP Yöntemi](icordebugilframe-cansetip-method.md)|Belirtilen konum konumuna yönerge işaretçisini ayarlamak için güvenli olup olmadığını gösteren bir değer alır.|  
|[EnumerateArguments Yöntemi](icordebugilframe-enumeratearguments-method.md)|Bu çerçevedeki bağımsız değişkenler için bir Numaralandırıcı alır.|  
|[EnumerateLocalVariables Yöntemi](icordebugilframe-enumeratelocalvariables-method.md)|Bu çerçevedeki yerel değişkenler için bir Numaralandırıcı alır.|  
|[GetArgument Yöntemi](icordebugilframe-getargument-method.md)|Bu MSIL yığın çerçevesindeki belirtilen bağımsız değişkenin değerini alır.|  
|[GetIP Yöntemi](icordebugilframe-getip-method.md)|Yönerge işaretçisinin değerini ve yönerge işaretçisi değerinin nasıl elde edileceğini açıklayan bit düzeyinde birleşim değerini alır.|  
|[GetLocalVariable Yöntemi](icordebugilframe-getlocalvariable-method.md)|Bu MSIL yığın çerçevesinde belirtilen yerel değişkenin değerini alır.|  
|[GetStackDepth Yöntemi](icordebugilframe-getstackdepth-method.md)|Uygulanmaz.|  
|[GetStackValue Yöntemi](icordebugilframe-getstackvalue-method.md)|Uygulanmaz.|  
|[SetIP Yöntemi](icordebugilframe-setip-method.md)|Yönerge işaretçisini MSIL kodunda belirtilen konum konumunu ayarlar.|  
  
## <a name="remarks"></a>Açıklamalar  

 `ICorDebugILFrame`Arabirim, özelleştirilmiş bir ICorDebugFrame arabirimidir. MSIL kod çerçeveleri ya da tam zamanında (JıT) derlenmiş çerçeveler için kullanılır. JıT ile derlenen çerçeveler hem arabirimini hem de `ICorDebugILFrame` ICorDebugNativeFrame arabirimini uygular.  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
