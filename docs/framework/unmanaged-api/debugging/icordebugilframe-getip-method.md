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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bd421d705a96778159cb80ad92d9ac654e88985f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33414072"
---
# <a name="icordebugilframegetip-method"></a>ICorDebugILFrame::GetIP Metodu
Yönerge işaretçisi değerini ve nasıl yönerge işaretçisi değerini edinilen açıklayan Bitsel bir birleşimi değeri alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetIP (  
    [out] ULONG32               *pnOffset,   
    [out] CorDebugMappingResult *pMappingResult  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pnOffset`  
 [out] Yönerge işaretçisi değeri.  
  
 `pMappingResult`  
 [out] Yönerge işaretçisi değerini nasıl edinilen açıklamak CorDebugMappingResult numaralandırma değerlerinin Bitsel bir birleşimi için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Yönerge işaretçisi işlevin Microsoft Ara dili (MSIL) koda yığın çerçeve uzaklık değeri. Yığın çerçevesi etkin değilse, bu yürütmek için sonraki yönerge adresidir. Yığın çerçevesi etkin değilse, bu yığın çerçevesi etkinleştirildiğinde yürütmek için sonraki yönerge adresidir.  
  
 Bu çerçeve tam zamanında (JIT) derlenmiş çerçeve ise, yönerge işaretçisi değerini değeri yalnızca yaklaşık olabilir geriye doğru gerçek yerel yönerge işaretçi eşleme tarafından belirlenir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
