---
description: ': ICorDebugNativeFrame:: GetIP Yöntemi hakkında daha fazla bilgi edinin'
title: ICorDebugNativeFrame::GetIP Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetIP
helpviewer_keywords:
- GetIP method, ICorDebugNativeFrame interface [.NET Framework debugging]
- ICorDebugNativeFrame::GetIP method [.NET Framework debugging]
ms.assetid: 99f693f3-d3b9-4fd8-9d09-b8efd03f7b67
topic_type:
- apiref
ms.openlocfilehash: f36a14c38aa6c3754cf78eca8c657adc76469067
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637858"
---
# <a name="icordebugnativeframegetip-method"></a>ICorDebugNativeFrame::GetIP Metodu

Yönerge işaretçisinin Şu anda ayarlandığı yerel kod konumu konumunu alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetIP (  
    [out] ULONG32           *pnOffset  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pnOffset`  
 dışı Yerel koddaki konum konumunu gösteren bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  

 Bu "ICorDebugNativeFrame" tarafından temsil edilen yığın çerçevesi etkin ise, konum yürütülecek sonraki yönergenin adresidir. Bu yığın çerçevesi etkin değilse, Aralık, yığın çerçevesi yeniden etkinleştirildiğinde yürütülecek sonraki yönergenin adresidir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
