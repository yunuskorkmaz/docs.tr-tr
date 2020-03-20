---
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
ms.openlocfilehash: 64e697323377d664b7b1e36bbf5931a44465cc51
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178951"
---
# <a name="icordebugchaingetstackrange-method"></a>ICorDebugChain::GetStackRange Metodu
Bu zincirin yığın kesiminin adres aralığını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pStart`  
 [çıkış] Yığın kesiminin `CORDB_ADDRESS` başlangıç adresi olan bir değeriçin işaretçi.  
  
 `pEnd`  
 [çıkış] Yığın kesiminin `CORDB_ADDRESS` bitiş adresi olan bir değerin işaretçisi.  
  
## <a name="remarks"></a>Açıklamalar  
 Sayısal aralık yalnızca yığın çerçeve konumlarının karşılaştırılması için anlamlıdır. Yığında gerçekte nelerin depolanmış olduğu hakkında herhangi bir varsayımda bulunamazsınız.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** CorDebug.idl, CorDebug.h  
  
 **Kütüphane:** CorGuids.lib  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
