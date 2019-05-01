---
title: ICLRStrongName::GetHashFromAssemblyFile Metodu
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromAssemblyFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromAssemblyFile
helpviewer_keywords:
- ICLRStrongName::GetHashFromAssemblyFile method [.NET Framework hosting]
- GetHashFromAssemblyFile method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 0b67ea03-d474-4605-acaa-57455790250c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 714827da24b3fc0a334210fd94e61f80cb2afe49
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993115"
---
# <a name="iclrstrongnamegethashfromassemblyfile-method"></a>ICLRStrongName::GetHashFromAssemblyFile Metodu
Belirtilen karma algoritması kullanılarak, belirtilen derleme dosyasının bir karmasını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetHashFromAssemblyFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `szFilePath`  
 [in] Karma hale getirilecek dosyanın yolu.  
  
 `piHashAlg`  
 [out içinde] Sabit karma algoritmasını belirtir. Sıfır varsayılan karma algoritması için kullanın.  
  
 `pbHash`  
 [out] Döndürülen karma arabellek.  
  
 `cchHash`  
 [in] İstenen en büyük boyutunu `pbHash`.  
  
 `pchHash`  
 [out] Bayt cinsinden boyutu döndürülen `pbHash`.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `S_OK` yöntemi başarıyla tamamlandı Aksi takdirde hata olduğunu gösteren HRESULT değerini (bkz [ortak HRESULT değerlerini](https://go.microsoft.com/fwlink/?LinkId=213878) bir listesi için).  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MetaHost.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [GetHashFromAssemblyFileW Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md)
- [ICLRStrongName Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
