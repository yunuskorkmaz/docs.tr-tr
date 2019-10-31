---
title: ICLRStrongName::GetHashFromHandle Metodu
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromHandle
- ICLRStrongName.StrongNameCompareAssemblies
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromHandle
helpviewer_keywords:
- GetHashFromHandle method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::GetHashFromHandle method [.NET Framework hosting]
ms.assetid: 3bedbb7d-3cdd-4175-b370-10ae734062db
topic_type:
- apiref
ms.openlocfilehash: 19d4518b7ec125df717b2f901bbd92cbd1b659bc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73135164"
---
# <a name="iclrstrongnamegethashfromhandle-method"></a>ICLRStrongName::GetHashFromHandle Metodu
Belirtilen karma algoritmasını kullanarak, belirtilen dosya tanıtıcısına sahip dosyanın içeriği üzerinde bir karma oluşturur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetHashFromHandle (  
    [in]  HANDLE   hFile,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `hFile`  
 'ndaki Karma hale getirilen dosyanın tanıtıcısı.  
  
 `piHashAlg`  
 [in, out] Karma algoritmayı belirten bir sabit. Varsayılan algoritma için sıfır kullanın.  
  
 `pbHash`  
 dışı Döndürülen karma arabelleği.  
  
 `cchHash`  
 'ndaki İstenen en büyük boyut `pbHash`.  
  
 `pchHash`  
 dışı Döndürülen `pbHash`bayt cinsinden boyutu.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarıyla tamamlanırsa `S_OK`; Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](https://go.microsoft.com/fwlink/?LinkId=213878) ).  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MetaHost. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRStrongName Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
