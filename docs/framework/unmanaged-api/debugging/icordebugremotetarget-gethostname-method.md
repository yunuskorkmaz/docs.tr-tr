---
title: ICorDebugRemoteTarget::GetHostName Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugRemoteTarget.GetHostName
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemoteTarget::GetHostName
helpviewer_keywords:
- ICorDebugRemoteTarget::GetHostName method [.NET Framework debugging]
- GetHostName method, ICorDebugRemoteTarget interface [.NET Framework debugging]
ms.assetid: 1c7276f7-7e54-470c-808c-e13745ac07a1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fda739a71a133a8c6177d0c7b8e0402d1dc97c4f
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57202216"
---
# <a name="icordebugremotetargetgethostname-method"></a>ICorDebugRemoteTarget::GetHostName Yöntemi
Tam etki alanı adı veya uzaktan hata ayıklama hedef makinesinin IPv4 adresini döndürür. IPv6 şu anda desteklenmiyor.  
  
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
 [in] Karakter cinsinden boyutu, `szHostName` arabellek. Bu parametre 0 (sıfır) ise `szHostName` null olmalıdır.  
  
 `pcchHostName`  
 [out] Konak adı veya IP adresi null sonlandırıcıyı da dahil olmak üzere karakter sayısı. Bu parametre null olabilir.  
  
 `szHostName`  
 [out] Ana bilgisayar adı veya IP adresini içeren arabellek.  
  
## <a name="return-value"></a>Dönüş Değeri  
 S_OK  
 Konak adı veya IP adresi başarıyla döndürüldü.  
  
 E_FAIL (veya diğer E_ dönüş kodları)  
 Konak adı veya IP adresini döndürmek yüklenemiyor.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, hata ayıklayıcıyı yazan tarafından uygulanır. Birden fazla arama paradigması izlemelidir: İlk çağrı, çağıran her ikisi de null geçirir `cchHostName` ve `szHostName`, ve `pcchHostName` gerekli arabellek boyutunu döndürür. İkinci çağrıda, daha önce döndürülen boyutu geçirilen `cchHostName`, ve uygun boyutlandırılmış bir arabellek geçirilen `szHostName`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** 3.5 SP1  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ICorDebugRemoteTarget Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)
- [ICorDebug Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
