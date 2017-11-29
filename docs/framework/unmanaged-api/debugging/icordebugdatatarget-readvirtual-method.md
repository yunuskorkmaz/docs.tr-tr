---
title: "ICorDebugDataTarget::ReadVirtual Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugDataTarget.ReadVirtual Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugDataTarget::ReadVirtual
helpviewer_keywords:
- ICorDebugDataTarget::ReadVirtual method [.NET Framework debugging]
- ReadVirtual method, ICorDebugDataTarget interface [.NET Framework debugging]
ms.assetid: 55e57640-b3d2-413d-b4f4-fbc27fb8e37c
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b9b9f0399c05155a9925624e5c9d6bcb6a52f024
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugdatatargetreadvirtual-method"></a>ICorDebugDataTarget::ReadVirtual Yöntemi
Belirtilen adresten başlayarak bitişik bellek bloğu alır ve sağlanan arabellek döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT ReadVirtual(  
    [in] CORDB_ADDRESS   address,  
    [out, size_is(bytesRequested), length_is(*pBytesRead)]  
          BYTE *     pBuffer,  
    [in]  ULONG32    bytesRequested,  
    [out] ULONG32 *  pBytesRead);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `address`  
 [in] İstenen bellek başlangıç adresi.  
  
 `pbuffer`  
 [out] Bellek depolanacağı arabelleği.  
  
 `bytesRequested`  
 [in] Hedef adres almak için bayt sayısı.  
  
 `pBytesRead`  
 [out] Hedef adres gerçekte okunan bayt sayısı. Bu daha az olabilir `bytesRequested`.  
  
## <a name="remarks"></a>Açıklamalar  
 İlk bayta kalan (belirtilen başlangıç adresindeki) okuyabilir, çağrı (null ile sonlandırılmış dizeler gibi uzunluğu kendiliğinden açıklayıcı ile veri yapılarının verimli okuma desteklemek için) başarı döndürmelidir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Icordebugdatatarget arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)  
 [Hata ayıklama arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Hata ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
