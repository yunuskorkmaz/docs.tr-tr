---
description: ': ICorDebugNativeFrame:: GetLocalMemoryRegisterValue yöntemi hakkında daha fazla bilgi edinin'
title: ICorDebugNativeFrame::GetLocalMemoryRegisterValue Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetLocalMemoryRegisterValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetLocalMemoryRegisterValue
helpviewer_keywords:
- ICorDebugNativeFrame::GetLocalMemoryRegisterValue method [.NET Framework debugging]
- GetLocalMemoryRegisterValue method
ms.assetid: 33a19f6e-1029-4d53-af64-19591c6e58ee
topic_type:
- apiref
ms.openlocfilehash: a0858aa11713bb71c485174c2f1624a0c7cda821
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99718037"
---
# <a name="icordebugnativeframegetlocalmemoryregistervalue-method"></a>ICorDebugNativeFrame::GetLocalMemoryRegisterValue Metodu

Bir bağımsız değişkenin veya yerel değişkenin değerini alır, bu yerel çerçeve için sırasıyla alt sözcük ve yüksek sözcük belirtilen yazmaç ve bellek konumunda depolanır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetLocalMemoryRegisterValue (  
    [in] CORDB_ADDRESS      highWordAddress,  
    [in] CorDebugRegister   lowWordRegister,  
    [in] ULONG              cbSigBlob,  
    [in] PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `highWordAddress`  
 'ndaki `CORDB_ADDRESS` Değerin yüksek sözcüğünü içeren bellek konumunu belirten bir değer.  
  
 `lowWordRegister`  
 'ndaki Değerin düşük sözcüğünü içeren kaydı belirten "CorDebugRegister" numaralandırmasının değeri.  
  
 `cbSigBlob`  
 'ndaki Parametresi tarafından başvurulan ikili meta veri imzasının boyutunu belirten bir tamsayı `pvSigBlob` .  
  
 `pvSigBlob`  
 'ndaki `PCCOR_SIGNATURE` Değerin türünün ikili meta veri imzasına işaret eden bir değer.  
  
 `ppValue`  
 dışı Belirtilen yazmaç ve bellek konumunda depolanan alınan değeri temsil eden bir "ICorDebugValue" nesnesinin adresine yönelik bir işaretçi.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
