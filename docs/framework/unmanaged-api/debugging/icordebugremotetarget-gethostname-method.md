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
ms.openlocfilehash: f177d441da3bd967750781e487d9fed42bc132f5
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791943"
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
  
 E_FAIL (veya diğer E_ dönüş kodları)  
 Ana bilgisayar adı veya IP adresi döndürülemiyor.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, hata ayıklayıcı yazıcı tarafından uygulanır. Bu, birden çok çağrı paradigmasını izlemelidir: ilk çağrıda, çağıran `cchHostName` ve `szHostName`için null değerini geçirir ve `pcchHostName` gereken arabelleğin boyutunu döndürür. İkinci çağrıda, daha önce döndürülen boyut `cchHostName`geçirilir ve `szHostName`uygun boyutta bir arabellek geçirilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** 3,5 SP1  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugRemoteTarget Arabirimi](icordebugremotetarget-interface.md)
- [ICorDebug Arabirimi](icordebug-interface.md)
