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
ms.openlocfilehash: cbc056e9a3cc00178b32dee4011da4403dff508a
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212782"
---
# <a name="icordebugheapvalue2createhandle-method"></a>ICorDebugHeapValue2::CreateHandle Yöntemi
Bu ICorDebugHeapValue2 nesnesi tarafından temsil edilen yığın değeri için belirtilen türden bir tanıtıcı oluşturur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT CreateHandle (  
    [in] CorDebugHandleType      type,
    [out] ICorDebugHandleValue   **ppHandle  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `type`  
 'ndaki Oluşturulacak tanıtıcının türünü belirten Cordebugghandlitype numaralandırmasının değeri.  
  
 `ppHandle`  
 dışı Bu yığın değeri için yeni tanıtıcıyı temsil eden bir ıcorıbu Ghandtavalue nesnesinin adresine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Tanıtıcı, yığın değeriyle ilişkili uygulama etki alanında oluşturulur ve uygulama etki alanı kaldırıldığında geçersiz olur.  
  
 Aynı yığın değeri için bu işleve birden çok çağrı birden çok tanıtıcı oluşturacak. Tutamaçlar çöp toplayıcısının performansını etkilediği için, hata ayıklayıcı kendisini her seferinde etkin olan görece küçük tanıtıcılara (yaklaşık 256) sınıralmalıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
