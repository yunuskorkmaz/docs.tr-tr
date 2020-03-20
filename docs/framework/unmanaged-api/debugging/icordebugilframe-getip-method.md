---
title: ICorDebugILFrame::GetIP Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.GetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::GetIP
helpviewer_keywords:
- GetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::GetIP method [.NET Framework debugging]
ms.assetid: 18217ba1-1776-4297-a3b9-f77e64b0fead
topic_type:
- apiref
ms.openlocfilehash: f30516a8f59b90de9b4c052d92a8c88575ace3c4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178832"
---
# <a name="icordebugilframegetip-method"></a>ICorDebugILFrame::GetIP Metodu
Yönerge işaretçisinin değerini ve yönerge işaretçisinin değerinin nasıl elde edildiğini açıklayan bitwise birleşim değerini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetIP (  
    [out] ULONG32               *pnOffset,
    [out] CorDebugMappingResult *pMappingResult  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pnOffset`  
 [çıkış] Yönerge işaretçisinin değeri.  
  
 `pMappingResult`  
 [çıkış] Yönerge işaretçisinin değerinin nasıl elde edildiğini açıklayan CorDebugMappingResult numaralandırma değerlerinin bitwise birleşimine işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Yönerge işaretçisinin değeri, yığın çerçevesinin işlevin Microsoft ara dili (MSIL) koduna mahsup çalışmasıdır. Yığın çerçevesi etkinse, bu adres yürütülecek bir sonraki yönergedir. Yığın çerçevesi etkin değilse, bu adres, yığın çerçevesi yeniden etkinleştirildiğinde yürütülecek sonraki yönergedir.  
  
 Bu çerçeve tam zamanında (JIT) derlenmiş bir çerçeveyse, yönerge işaretçisinin değeri gerçek yerel yönerge işaretçisinden geriye doğru eşlenerek belirlenir, böylece değer yalnızca yaklaşık olabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** CorDebug.idl, CorDebug.h  
  
 **Kütüphane:** CorGuids.lib  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
