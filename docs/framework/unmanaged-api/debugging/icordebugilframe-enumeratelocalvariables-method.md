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
ms.openlocfilehash: 6fd7694901534ad6897bbf78239081af6314e4bd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415476"
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
 `EnumerateLocalVariables` Bu Icordebugılframe nesnesi tarafından temsil edilen çağrı çerçevesi bulunan yerel değişkenleri listesinden bir numaralandırıcı alır. Çünkü bunların bazıları etkin olmayabilir liste çalışan işlevinde, tüm yerel değişkenleri içermeyebilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
