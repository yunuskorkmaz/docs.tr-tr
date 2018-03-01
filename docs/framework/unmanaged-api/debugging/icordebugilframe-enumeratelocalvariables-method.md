---
title: "ICorDebugILFrame::EnumerateLocalVariables Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3a1b53dbefefcea6003ec4a61c8169ed96bac701
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframeenumeratelocalvariables-method"></a>ICorDebugILFrame::EnumerateLocalVariables Yöntemi
Bir numaralandırıcı yerel değişkenler için bu çerçevede alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT EnumerateLocalVariables(   
    [out] ICorDebugValueEnum    **ppValueEnum  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppValueEnum`  
 [out] Bu çerçeve yerel değişkenleri için Numaralandırıcı bir Icordebugvalueenum nesne adresini gösteren bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 `EnumerateLocalVariables`Bu Icordebugılframe nesnesi tarafından temsil edilen çağrı çerçevesi bulunan yerel değişkenleri listesinden bir numaralandırıcı alır. Çünkü bunların bazıları etkin olmayabilir liste çalışan işlevinde, tüm yerel değişkenleri içermeyebilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
