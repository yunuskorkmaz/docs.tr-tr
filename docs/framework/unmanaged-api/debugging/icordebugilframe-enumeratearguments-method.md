---
title: "ICorDebugILFrame::EnumerateArguments Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugILFrame.EnumerateArguments
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugILFrame::EnumerateArguments
helpviewer_keywords:
- ICorDebugILFrame::EnumerateArguments method [.NET Framework debugging]
- EnumerateArguments method [.NET Framework debugging]
ms.assetid: 00ac81e2-a774-422a-bd88-54a4b3c99f73
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bf345f3fa684b57a33e3452916535b1cd7db3c8b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
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
 `EnumerateArguments`Bu Icordebugılframe nesnesi tarafından temsil edilen çağrısı çerçevesinde kullanılabilen bağımsız değişkenler listeleyebilirsiniz bir numaralandırıcı alır. Listede olan bağımsız değişkenler bulunacaktır [vararg](/cpp/windows/vararg) (diğer bir deyişle, bir değişken sayıda bağımsız değişken) olmayan bağımsız değişkenler yanı sıra `vararg`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
