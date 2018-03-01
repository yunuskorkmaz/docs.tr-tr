---
title: "ICLRStrongName::StrongNameTokenFromAssemblyEx Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRStrongName.StrongNameTokenFromAssemblyEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameTokenFromAssemblyEx
helpviewer_keywords:
- StrongNameTokenFromAssemblyEx method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameTokenFromAssemblyEx method [.NET Framework hosting]
ms.assetid: 648ea90e-5e60-40a0-a56a-3e61bf2fba7c
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5b8b3437d8c07cd57a4791995890cab1b06aafc6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrstrongnamestrongnametokenfromassemblyex-method"></a>ICLRStrongName::StrongNameTokenFromAssemblyEx Yöntemi
Belirtilen derleme dosyasından bir güçlü ad belirteci oluşturur ve belirteci temsil eder ortak anahtarını döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT StrongNameTokenFromAssemblyEx (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `wszFilePath`  
 [in] Derleme için taşınabilir yürütülebilir (PE) dosya yolu.  
  
 `ppbStrongNameToken`  
 [out] Döndürülen güçlü ad belirteci.  
  
 `pcbStrongNameToken`  
 [out] Güçlü ad belirtecin bayt cinsinden boyutu.  
  
 `ppbPublicKeyBlob`  
 [out] Döndürülen ortak anahtarı.  
  
 `pcbPublicKeyBlob`  
 [out] Ortak anahtarın bayt cinsinden boyutu.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `S_OK`Yöntem başarıyla tamamlandı Aksi takdirde hata belirten bir HRESULT değeri (bkz [ortak HRESULT değerleri](http://go.microsoft.com/fwlink/?LinkId=213878) bir listesi için).  
  
## <a name="remarks"></a>Açıklamalar  
 Güçlü ad simgesi bir ortak anahtar kısaltılmış şeklidir. Belirteç derlemeyi imzalamak için kullanılan ortak anahtarı ile oluşturulan 64 bitlik bir karma olur. Belirteç derleme için güçlü ad, bir parçasıdır ve derleme meta verileri okuyabilir.  
  
 Anahtar aldı ve belirteç oluşturulduktan sonra çağırmalıdır [Iclrstrongname::strongnamefreebuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) ayrılmış bellek yayımlamayı yöntemi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MetaHost.h  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [StrongNameTokenFromAssembly Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md)  
 [ICLRStrongName Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
