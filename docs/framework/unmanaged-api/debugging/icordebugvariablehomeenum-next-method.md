---
title: "ICorDebugVariableHomeEnum::Next yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorDebugVariableHomeEnum.Next
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugVariableHomeEnum::Next
helpviewer_keywords:
- ICorDebugVariableHomeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugVariableHomeEnum interface [.NET Framework debugging]
ms.assetid: eb9ea96c-5b58-4655-8104-094fc8b393b8
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 480317a4ec0515411f1ca8156a5bc4d06aa3f38a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugvariablehomeenumnext-method"></a>ICorDebugVariableHomeEnum::Next yöntemi
Belirtilen sayıda alır [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) yerel değişkenleri ve bir işlev bağımsız değişkenleri hakkında bilgi içeren örnekleri.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)] ICorDebugVariableHome *homes[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `celt`  
 [in] Alınacak nesne sayısı.  
  
 `homes`  
 Her biri işaret işaretçileri, bir dizi bir [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) yerel değişken ya da işlevin bağımsız değişkeninin hakkında bilgi sağlayan nesne.  
  
 `pceltFetched`  
 [out] Gerçekte nesneleri döndürülen örnek sayısı.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem, aşağıdaki değerleri döndürür.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|`S_OK`|Yöntem başarıyla tamamlandı.|  
|`S_FALSE`|Gerçek örneklerinin sayısını alınan, yansıtılan `pceltFetched`, istenen örneklerinin sayısını'dan küçük.|  
  
## <a name="remarks"></a>Açıklamalar  
 [ICorDebugVariableHomeEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md) yöntemi alır en fazla `celt` Numaralayıcı geçerli konumdan başlayarak nesneleri. Yöntem döndüğünde `pceltFetched` alınan nesneler gerçek sayısını içerir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorDebugVariableHomeEnum arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)  
 [ICorDebugVariableHome arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
