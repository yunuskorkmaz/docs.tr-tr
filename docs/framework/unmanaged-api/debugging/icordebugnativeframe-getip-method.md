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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 38f913b742f7ece2f136454f801ae780124aed87
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59073539"
---
# <a name="icordebugnativeframegetip-method"></a>ICorDebugNativeFrame::GetIP Metodu
Alır yerel kod, yönerge işaretçisini şu anda ayarlanmış konumu uzaklığı.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetIP (  
    [out] ULONG32           *pnOffset  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pnOffset`  
 [out] Yerel kod uzaklık konumunda bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu "Icordebugnativeframe" tarafından temsil edilen yığın çerçevesini etkin olursa, uzaklık yürütülmesi gereken sonraki yönergeyi adresidir. Bu yığın çerçevesi etkin değilse, uzaklık yığın çerçevesinin yeniden etkinleştirildiğinde yürütülecek sonraki yönergeyi adresidir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
