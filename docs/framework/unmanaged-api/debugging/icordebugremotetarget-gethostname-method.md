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
ms.openlocfilehash: 020724c422af7cba0165e6f37d0eacb7742153ec
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379268"
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
 'ndaki Arabelleğin karakter cinsinden boyutu `szHostName` . Bu parametre 0 (sıfır) ise null olmalıdır `szHostName` .  
  
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
 Bu yöntem, hata ayıklayıcı yazıcı tarafından uygulanır. Birden çok çağrı paradigmasını izlemelidir: ilk çağrıda, çağıran her ikisine de null değeri geçirir `cchHostName` `szHostName` ve `pcchHostName` gereken arabelleğin boyutunu döndürür. İkinci çağrıda, daha önce döndürülen boyut geçirilir `cchHostName` ve uygun boyutta bir arabellek geçirilir `szHostName` .  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** 3,5 SP1  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugRemoteTarget Arabirimi](icordebugremotetarget-interface.md)
- [ICorDebug Arabirimi](icordebug-interface.md)
