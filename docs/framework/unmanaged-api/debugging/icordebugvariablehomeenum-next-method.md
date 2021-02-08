---
description: 'Şu konuda daha fazla bilgi edinin: ıcordebugvariablehomeenum:: Next yöntemi'
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
ms.openlocfilehash: 0aa0174e67bceaa724ddfeadc2560d12e112b859
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790613"
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
  
|HRESULT|Description|  
|-------------|-----------------|  
|`S_OK`|Yöntem başarıyla tamamlandı.|  
|`S_FALSE`|İçinde yansıtıldıkça alınan örneklerin gerçek sayısı `pceltFetched` , istenen örnek sayısından daha az.|  
  
## <a name="remarks"></a>Açıklamalar  

 [Icordebugvariablehomeenum:: Next](icordebugvariablehomeenum-next-method.md) yöntemi, `celt` Numaralandırıcının geçerli konumundan başlayarak en fazla nesne alır. Yöntemi döndürüldüğünde, `pceltFetched` alınan nesnelerin gerçek sayısını içerir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugVariableHomeEnum Arabirimi](icordebugvariablehomeenum-interface.md)
- [ICorDebugVariableHome Arabirimi](icordebugvariablehome-interface.md)
