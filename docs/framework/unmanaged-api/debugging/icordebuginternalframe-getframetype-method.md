---
description: ': ICorDebugInternalFrame:: GetFrameType yöntemi hakkında daha fazla bilgi edinin'
title: ICorDebugInternalFrame::GetFrameType Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugInternalFrame.GetFrameType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame::GetFrameType
helpviewer_keywords:
- GetFrameType method [.NET Framework debugging]
- ICorDebugInternalFrame::GetFrameType method [.NET Framework debugging]
ms.assetid: da278a29-dc2e-4bf7-96ce-801bdc4d7025
topic_type:
- apiref
ms.openlocfilehash: ea96f032ebfa5914503287d124242b74a84ea11f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791185"
---
# <a name="icordebuginternalframegetframetype-method"></a>ICorDebugInternalFrame::GetFrameType Yöntemi

Bu iç çerçevenin türünü alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetFrameType (  
    [out] CorDebugInternalFrameType  *pType  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pType`  
 dışı Bu nesne tarafından temsil edilen iç çerçeve türünü gösteren CorDebugInternalFrameType numaralandırması değerine yönelik bir işaretçi `ICorDebugInternalFrame` .  
  
## <a name="remarks"></a>Açıklamalar  

 İç çerçeve türü hiçbir STUBFRAME_NONE olmaz. Hata ayıklayıcılar, tanınmayan iç çerçeve türlerini düzgün şekilde yoksaymalıdır.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
