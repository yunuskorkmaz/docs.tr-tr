---
title: 'Icordebugvariablehomeenum:: Next yöntemi'
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHomeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHomeEnum::Next
helpviewer_keywords:
- ICorDebugVariableHomeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugVariableHomeEnum interface [.NET Framework debugging]
ms.assetid: eb9ea96c-5b58-4655-8104-094fc8b393b8
topic_type:
- apiref
ms.openlocfilehash: 2bb6fee00bb99555bc19f35e1250880cc3985f7f
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790934"
---
# <a name="icordebugvariablehomeenumnext-method"></a>Icordebugvariablehomeenum:: Next yöntemi
Bir işlevdeki yerel değişkenler ve bağımsız değişkenler hakkında bilgi içeren, belirtilen [ıcordebugvariablehome](icordebugvariablehome-interface.md) örneği sayısını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)] ICorDebugVariableHome *homes[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `celt`  
 'ndaki Alınacak nesne sayısı.  
  
 `homes`  
 Her biri bir işlevin yerel değişkeni veya bağımsız değişkeni hakkında bilgi sağlayan [ıcordebugvariablehome](icordebugvariablehome-interface.md) nesnesine işaret eden bir işaretçiler dizisi.  
  
 `pceltFetched`  
 dışı Gerçekte nesnelerde döndürülen örneklerin sayısı.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi aşağıdaki değerleri döndürür.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|`S_OK`|Yöntem başarıyla tamamlandı.|  
|`S_FALSE`|`pceltFetched`' de yansıtıldıkça alınan gerçek örnek sayısı, istenen örnek sayısından daha az.|  
  
## <a name="remarks"></a>Açıklamalar  
 [Icordebugvariablehomeenum:: Next](icordebugvariablehomeenum-next-method.md) yöntemi, Numaralandırıcının geçerli konumundan başlayarak en fazla `celt` nesne alır. Yöntemi döndürüldüğünde, `pceltFetched` alınan nesnelerin gerçek sayısını içerir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugVariableHomeEnum Arabirimi](icordebugvariablehomeenum-interface.md)
- [ICorDebugVariableHome Arabirimi](icordebugvariablehome-interface.md)
