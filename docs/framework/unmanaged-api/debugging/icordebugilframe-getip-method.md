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
ms.openlocfilehash: 7a7b8985e7580282d0e38205f9b1d6078f86cee6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988617"
---
# <a name="icordebugilframegetip-method"></a>ICorDebugILFrame::GetIP Metodu
Yönerge işaretçisi değerini ve nasıl yönerge işaretçisini değerini edinilen açıklayan bir karşılaştırmaya değerini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetIP (  
    [out] ULONG32               *pnOffset,   
    [out] CorDebugMappingResult *pMappingResult  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pnOffset`  
 [out] Yönerge işaretçisi değeri.  
  
 `pMappingResult`  
 [out] Yönerge işaretçisinin değeri nasıl edinilen açıklayan CorDebugMappingResult numaralandırma değerlerinin Bitsel bir birleşimi için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Yönerge işaretçisi işlev Microsoft Ara dili (MSIL) kodu yığın çerçeve uzaklık değeri. Yığın çerçevesinin etkin olursa, bu adresi yürütülecek sonraki yönergedir. Yığın çerçevesinin etkin değilse, bu yığın çerçevesinin yeniden etkinleştirildiğinde yürütülecek sonraki yönergeyi adresidir.  
  
 Bu çerçeve, just-ın-time (JIT) derlenmiş çerçeve ise, yönerge işaretçisini değerini değeri yalnızca yaklaşık olabilir geriye doğru gerçek yerel yönerge işaretçisinden eşleme tarafından belirlenir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
