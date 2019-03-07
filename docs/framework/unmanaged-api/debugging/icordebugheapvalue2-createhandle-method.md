---
title: ICorDebugHeapValue2::CreateHandle Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue2.CreateHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue2::CreateHandle
helpviewer_keywords:
- CreateHandle method [.NET Framework debugging]
- ICorDebugHeapValue2::CreateHandle method [.NET Framework debugging]
ms.assetid: fbc418e8-fa22-420d-84ec-e0e1800db041
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 078dfd7162c250f0279b8bc372aeb39662aa0119
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57498542"
---
# <a name="icordebugheapvalue2createhandle-method"></a>ICorDebugHeapValue2::CreateHandle Yöntemi
Bu Icordebugheapvalue2 nesnesi tarafından temsil edilen yığın değeri için belirtilen türün bir tanıtıcı oluşturur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT CreateHandle (  
    [in] CorDebugHandleType      type,   
    [out] ICorDebugHandleValue   **ppHandle  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `type`  
 [in] Oluşturulacak tanıtıcı türü belirtir CorDebugHandleType sabit listesi değeri.  
  
 `ppHandle`  
 [out] Bu yığın değer için yeni işleyici temsil eden Icordebughandlevalue nesnenin adresini bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Tanıtıcı, yığın değeriyle ilişkili olan uygulama etki alanında oluşturulur ve uygulama etki alanı bellekten alırsa geçersiz hale gelir.  
  
 Bu işlev için yığını değerin birden çok çağrı birden çok oluşturacaksınız. Tanıtıcıları çöp toplayıcı performansı etkilediğinden, hata ayıklayıcı kendisini tutamaçlarını (yaklaşık 256) aynı anda etkin olan görece daha az sayıda sınırlamanız gerekir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
