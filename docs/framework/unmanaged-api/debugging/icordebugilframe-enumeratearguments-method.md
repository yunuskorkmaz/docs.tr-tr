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
ms.openlocfilehash: 2e4a727dcfbc80b131f526a08b00bd0ec91ca209
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415028"
---
# <a name="icordebugilframeenumeratearguments-method"></a>ICorDebugILFrame::EnumerateArguments Yöntemi
Bir numaralandırıcı Bu çerçevede bağımsız değişkenleri alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT EnumerateArguments (  
    [out] ICorDebugValueEnum    **ppValueEnum  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppValueEnum`  
 [out] Bu çerçeve değişkenlerinde Numaralandırıcı bir Icordebugvalueenum nesne adresini gösteren bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 `EnumerateArguments` Bu Icordebugılframe nesnesi tarafından temsil edilen çağrısı çerçevesinde kullanılabilen bağımsız değişkenler listeleyebilirsiniz bir numaralandırıcı alır. Listede olan bağımsız değişkenler bulunacaktır [vararg](/cpp/windows/vararg) (diğer bir deyişle, bir değişken sayıda bağımsız değişken) olmayan bağımsız değişkenler yanı sıra `vararg`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
