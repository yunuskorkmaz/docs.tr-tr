---
title: ICorDebugRemoteTarget::GetHostName Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugRemoteTarget.GetHostName
api_location: CorDebug.dll
api_type: COM
f1_keywords: ICorDebugRemoteTarget::GetHostName
helpviewer_keywords:
- ICorDebugRemoteTarget::GetHostName method [.NET Framework debugging]
- GetHostName method, ICorDebugRemoteTarget interface [.NET Framework debugging]
ms.assetid: 1c7276f7-7e54-470c-808c-e13745ac07a1
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2af5d75145b9fdd2d370b76f798c5e350d8bec50
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugremotetargetgethostname-method"></a>ICorDebugRemoteTarget::GetHostName Metodu
Tam etki alanı adı veya uzaktan hata ayıklama hedef makine IPv4 adresini döndürür. IPv6, şu anda desteklenmiyor.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetHostName (  
    [in] ULONG32      cchHostName,  
    [out] ULONG32*    pcchHostName,  
    [out, size_is(cchHostName), length_is(*pcchHostName)]  
            WCHAR szHostName[]  
```  
  
#### <a name="parameters"></a>Parametreler  
 `cchHostName`  
 [in] Karakter, boyutu, `szHostName` arabellek. Bu parametre 0 (sıfır) ise `szHostName` null olmalıdır.  
  
 `pcchHostName`  
 [out] Ana bilgisayar adı veya IP adresi null Sonlandırıcı dahil karakter sayısı. Bu parametre null olabilir.  
  
 `szHostName`  
 [out] Ana bilgisayar adı veya IP adresini içeren bir arabellek.  
  
## <a name="return-value"></a>Dönüş Değeri  
 S_OK  
 Ana bilgisayar adı veya IP adresi başarıyla döndürüldü.  
  
 E_FAIL (veya diğer E_ dönüş kodları)  
 Ana bilgisayar adı veya IP adresi iade edilemiyor.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, hata ayıklayıcı yazıcı tarafından uygulanır. Birden fazla çağrı standardı izlemelidir: ilk çağrıda çağıran her ikisi de null değerini iletir `cchHostName` ve `szHostName`, ve `pcchHostName` gerekli arabellek boyutu döndürür. İkinci çağrıda önceden döndürüldü boyutu geçirilen `cchHostName`, ve uygun şekilde boyutlu bir arabellek geçirilen `szHostName`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** 3.5 SP1  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Icordebugremotetarget arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)  
 [Icordebug arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
