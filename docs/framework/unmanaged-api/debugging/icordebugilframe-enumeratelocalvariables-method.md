---
title: ICorDebugILFrame::EnumerateLocalVariables Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.EnumerateLocalVariables
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::EnumerateLocalVariables
helpviewer_keywords:
- EnumerateLocalVariables method [.NET Framework debugging]
- ICorDebugILFrame::EnumerateLocalVariables method [.NET Framework debugging]
ms.assetid: 1a67fa1b-2419-4cd0-aad4-6f46a0719b4b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3cc9601105d05740e6db0a41bae521bd9a276d74
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988656"
---
# <a name="icordebugilframeenumeratelocalvariables-method"></a>ICorDebugILFrame::EnumerateLocalVariables Yöntemi
Bir numaralandırıcı bu çerçevesinde yerel değişkenler için alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT EnumerateLocalVariables(   
    [out] ICorDebugValueEnum    **ppValueEnum  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ppValueEnum`  
 [out] Yerel değişkenleri bu çerçevesi için Numaralandırıcı Icordebugvalueenum nesnenin adresi için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 `EnumerateLocalVariables` kullanılabilir bu Icordebugılframe nesnesi tarafından temsil edilen çağrı çerçevesinde yerel değişkenler listeleyen bir numaralandırıcıyı alır. Bunlardan bazıları etkin olmayabilir çünkü liste çalışan işlevde harcanan, tüm yerel değişkenlerin içermeyebilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
