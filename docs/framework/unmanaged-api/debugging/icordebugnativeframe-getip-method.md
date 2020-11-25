---
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
ms.openlocfilehash: c9c0598f8e7b3e8654124f50663c912f3cd61659
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709316"
---
# <a name="icordebugnativeframegetip-method"></a>ICorDebugNativeFrame::GetIP Metodu

Yönerge işaretçisinin Şu anda ayarlandığı yerel kod konumu konumunu alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
