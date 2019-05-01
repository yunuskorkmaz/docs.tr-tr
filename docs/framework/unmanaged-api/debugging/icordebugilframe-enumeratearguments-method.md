---
title: ICorDebugILFrame::EnumerateArguments Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.EnumerateArguments
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::EnumerateArguments
helpviewer_keywords:
- ICorDebugILFrame::EnumerateArguments method [.NET Framework debugging]
- EnumerateArguments method [.NET Framework debugging]
ms.assetid: 00ac81e2-a774-422a-bd88-54a4b3c99f73
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 49d7fb1de0b2ea63c1a766023b23acc42e027af8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61995572"
---
# <a name="icordebugilframeenumeratearguments-method"></a>ICorDebugILFrame::EnumerateArguments Yöntemi
Bir numaralandırıcı bu çerçeveye bağımsız değişkenleri alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT EnumerateArguments (  
    [out] ICorDebugValueEnum    **ppValueEnum  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ppValueEnum`  
 [out] Numaralandırıcı bağımsız değişkenlerin Bu çerçevede Icordebugvalueenum nesnenin adresi için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 `EnumerateArguments` bağımsız değişkenler bu Icordebugılframe nesnesi tarafından temsil edilen çağrı çerçevede kullanılabilir listeleyen bir numaralandırıcıyı alır. Bu liste olan bağımsız değişkenler içerir [vararg](/cpp/windows/vararg) (diğer bir deyişle, değişken sayıda bağımsız değişkenler) olmayan bağımsız değişkenleri yanı sıra `vararg`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
