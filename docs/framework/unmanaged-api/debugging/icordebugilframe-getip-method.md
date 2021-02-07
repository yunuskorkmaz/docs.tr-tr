---
description: ': ICorDebugILFrame:: GetIP Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: f3977d4fbe57b24e7b98b7a597b0db7ad171eb1c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99691880"
---
# <a name="icordebugilframegetip-method"></a>ICorDebugILFrame::GetIP Metodu

Yönerge işaretçisinin değerini ve yönerge işaretçisi değerinin nasıl elde edileceğini açıklayan bit düzeyinde birleşim değerini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetIP (  
    [out] ULONG32               *pnOffset,
    [out] CorDebugMappingResult *pMappingResult  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pnOffset`  
 dışı Yönerge işaretçisinin değeri.  
  
 `pMappingResult`  
 dışı Yönerge işaretçisinin değerinin nasıl elde edildiğini tanımlayan CorDebugMappingResult numaralandırma değerlerinin bit düzeyinde birleşimine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  

 Yönerge işaretçisinin değeri, yığın çerçevesinin işlevin Microsoft ara dil (MSIL) koduna olan aralıkdır. Yığın çerçevesi etkinse, bu adres yürütülecek sonraki yönergedir. Yığın çerçevesi etkin değilse, bu adres yığın çerçevesi yeniden etkinleştirildiğinde yürütülecek sonraki yönergedir.  
  
 Bu çerçeve tam zamanında (JıT) derlenmiş bir çerçevedir, yönerge işaretçisinin değeri gerçek yerel yönerge işaretçisinden geriye doğru eşleme yaparak belirlenir, bu nedenle değer yalnızca yaklaşık olabilir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
