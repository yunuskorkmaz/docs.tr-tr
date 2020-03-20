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
ms.openlocfilehash: c7a1bf3cb10cbc8cdae2788b45e1badaf66a9dbd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178874"
---
# <a name="icordebugheapvalue2createhandle-method"></a>ICorDebugHeapValue2::CreateHandle Yöntemi
Bu ICorDebugHeapValue2 nesnesi tarafından temsil edilen yığın değeri için belirtilen türde bir tutamaç oluşturur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT CreateHandle (  
    [in] CorDebugHandleType      type,
    [out] ICorDebugHandleValue   **ppHandle  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `type`  
 [içinde] Oluşturulacak tutamaç türünü belirten CorDebugHandleType numaralandırmasının değeri.  
  
 `ppHandle`  
 [çıkış] Bu yığın değeri için yeni tanıtıcıyı temsil eden bir ICorDebugHandleValue nesnesinin adresine işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Tanıtıcı, yığın değeriyle ilişkili uygulama etki alanında oluşturulur ve uygulama etki alanı boşaltılırsa geçersiz olur.  
  
 Aynı yığın değeri için bu işleve yapılan birden çok çağrı birden çok tutamaç oluşturur. Tutamaçları çöp toplayıcının performansını etkilediğinden, hata ayıklayıcı nın kendisini bir seferde etkin olan nispeten az sayıda (yaklaşık 256) tutamakla sınırlaması gerekir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** CorDebug.idl, CorDebug.h  
  
 **Kütüphane:** CorGuids.lib  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
