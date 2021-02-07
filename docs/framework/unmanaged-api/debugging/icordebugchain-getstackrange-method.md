---
description: ': Icordebugzincirine:: GetStackRange metodu hakkında daha fazla bilgi edinin'
title: ICorDebugChain::GetStackRange Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetStackRange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetStackRange
helpviewer_keywords:
- ICorDebugChain::GetStackRange method [.NET Framework debugging]
- GetStackRange method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 554284e7-3f6c-4d40-8da5-1c9317fbd484
topic_type:
- apiref
ms.openlocfilehash: 066dda06564655350d799dabb54acd622b828172
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99694937"
---
# <a name="icordebugchaingetstackrange-method"></a>ICorDebugChain::GetStackRange Metodu

Bu zincir için yığın segmentinin adres aralığını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pStart`  
 dışı `CORDB_ADDRESS` Yığın segmentinin başlangıç adresi olan değere yönelik bir işaretçi.  
  
 `pEnd`  
 dışı `CORDB_ADDRESS` Yığın kesiminin bitiş adresi olan değere yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  

 Sayısal Aralık yalnızca yığın çerçeve konumlarının karşılaştırılmasının anlamı vardır. Aslında yığında depolandıkları hakkında varsayımlar yapamazsınız.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
