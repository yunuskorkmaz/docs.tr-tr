---
title: ICorDebugFrame::GetCode Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetCode
helpviewer_keywords:
- GetCode method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetCode method [.NET Framework debugging]
ms.assetid: fbaa0794-a031-4015-8beb-2749e47ac340
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 15206fbd7724383b1ec6df123790d3171e58e9f7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33411924"
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
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
