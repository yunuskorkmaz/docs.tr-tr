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
ms.openlocfilehash: 3890cb4236f113bc6efc23bfb606d19a525ec234
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210273"
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
