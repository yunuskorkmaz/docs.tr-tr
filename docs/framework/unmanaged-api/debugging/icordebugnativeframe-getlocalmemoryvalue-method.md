---
title: ICorDebugNativeFrame::GetLocalMemoryValue Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetLocalMemoryValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetLocalMemoryValue
helpviewer_keywords:
- GetLocalMemoryValue method [.NET Framework debugging]
- ICorDebugNativeFrame::GetLocalMemoryValue method [.NET Framework debugging]
ms.assetid: b600b3a2-9908-42d8-8093-ab6f39e9a2c9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6c44f3e369ac64773811a6aea74756783dedd2fc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59209469"
---
# <a name="icordebugnativeframegetlocalmemoryvalue-method"></a>ICorDebugNativeFrame::GetLocalMemoryValue Metodu
Bir bağımsız değişken veya yerel değişken bu yerel çerçeve için belirtilen bellek konumunda depolanan değeri alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetLocalMemoryValue (  
    [in]  CORDB_ADDRESS      address,  
    [in]  ULONG              cbSigBlob,  
    [in]  PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `address`  
 [in] A `CORDB_ADDRESS` değerini içeren bellek konumu belirten bir değer.  
  
 `cbSigBlob`  
 [in] Tarafından başvurulan ikili meta veri imzası boyutunu belirten bir tamsayı `pvSigBlob` parametresi.  
  
 `pvSigBlob`  
 [in] A `PCCOR_SIGNATURE` değerin türü. ikili meta verileri imza işaret eden bir değer.  
  
 `ppValue`  
 [out] Belirtilen bellek konumunda depolanan alınan değeri temsil eden bir "ICorDebugValue" nesnenin adresi için bir işaretçi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
