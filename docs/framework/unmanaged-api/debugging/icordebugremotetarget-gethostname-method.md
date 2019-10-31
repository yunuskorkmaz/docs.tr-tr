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
ms.openlocfilehash: a9a6ca9ae3cdb1c6a7398d08c9f99e3cde125cf6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131906"
---
# <a name="icordebugremotetargetgethostname-method"></a>ICorDebugRemoteTarget::GetHostName Yöntemi
Uzaktan hata ayıklama hedef makinesinin tam etki alanı adını veya IPv4 adresini döndürür. IPV6 Şu anda desteklenmiyor.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetHostName (  
    [in] ULONG32      cchHostName,  
    [out] ULONG32*    pcchHostName,  
    [out, size_is(cchHostName), length_is(*pcchHostName)]  
            WCHAR szHostName[]  
```  
  
## <a name="parameters"></a>Parametreler  
 `cchHostName`  
 'ndaki `szHostName` arabelleğinin karakter cinsinden boyutu. Bu parametre 0 (sıfır) ise, `szHostName` null olmalıdır.  
  
 `pcchHostName`  
 dışı Ana bilgisayar adı veya IP adresi içinde null Sonlandırıcı dahil olmak üzere karakter sayısı. Bu parametre null olabilir.  
  
 `szHostName`  
 dışı Ana bilgisayar adını veya IP adresini içeren arabellek.  
  
## <a name="return-value"></a>Dönüş Değeri  
 S_OK  
 Ana bilgisayar adı veya IP adresi başarıyla döndürüldü.  
  
 E_FAıL (veya diğer E_ dönüş kodları)  
 Ana bilgisayar adı veya IP adresi döndürülemiyor.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, hata ayıklayıcı yazıcı tarafından uygulanır. Bu, birden çok çağrı paradigmasını izlemelidir: ilk çağrıda, çağıran `cchHostName` ve `szHostName`için null değerini geçirir ve `pcchHostName` gereken arabelleğin boyutunu döndürür. İkinci çağrıda, daha önce döndürülen boyut `cchHostName`geçirilir ve `szHostName`uygun boyutta bir arabellek geçirilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** 3,5 SP1  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugRemoteTarget Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)
- [ICorDebug Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
