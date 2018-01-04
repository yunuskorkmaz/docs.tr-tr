---
title: ICorDebugFrame::GetCode Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFrame.GetCode
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFrame::GetCode
helpviewer_keywords:
- GetCode method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetCode method [.NET Framework debugging]
ms.assetid: fbaa0794-a031-4015-8beb-2749e47ac340
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a99b652a439a284033f3e7a9ecc46b3599fae00b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugframegetcode-method"></a>ICorDebugFrame::GetCode Metodu
Bir işaretçi Bu yığın çerçevesi ile ilişkili kodunu alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetCode (  
    [out] ICorDebugCode      **ppCode  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppCode`  
 [out] Bir işaretçi adresine Icordebugcode nesnenin bu çerçeveyle ilişkili kodunu temsil eder.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
