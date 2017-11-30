---
title: "ICLRStrongName::StrongNameCompareAssemblies Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName.StrongNameCompareAssemblies
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::StrongNameCompareAssemblies
helpviewer_keywords:
- ICLRStrongName::StrongNameCompareAssemblies method [.NET Framework hosting]
- StrongNameCompareAssemblies method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: b1fb356c-72cf-4aa4-8376-f291a6d97c01
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ab69a0d0bb5894c2393e240b4f89b9a16dd98939
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="iclrstrongnamestrongnamecompareassemblies-method"></a>ICLRStrongName::StrongNameCompareAssemblies Yöntemi
İki derleme yalnızca güçlü ad imzaları tarafından farklı olup olmadığını belirler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT StrongNameCompareAssemblies (  
    [in]  LPCWSTR   wszAssembly1,  
    [in]  LPCWSTR   wszAssembly2,  
    [out] DWORD     *pdwResult  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `wszAssembly1`  
 [in] İlk derleme yolu.  
  
 `wszAssembly2`  
 [in] İkinci derleme yolu.  
  
 `pdwResult`  
 [out] Aşağıdaki değerlerden biri:  
  
-   `SN_CMP_DIFFERENT`(0) - derlemeler farklı veri içerdiğini belirtir.  
  
-   `SN_CMP_IDENTICAL`(1) - derlemeler tam olarak aynı, kendi imzaları ve sağlama toplamı dahil olduğunu belirtir.  
  
-   `SN_CMP_SIGONLY`(2) - derlemeler yalnızca imza ve sağlama toplamı tarafından farklı olduğunu belirtir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `S_OK`Yöntem başarıyla tamamlandı Aksi takdirde hata belirten bir HRESULT değeri (bkz [ortak HRESULT değerleri](http://go.microsoft.com/fwlink/?LinkId=213878) bir listesi için).  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MetaHost.h  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="remarks"></a>Açıklamalar  
 Bir derleme tanımlayıcı ad imzası derlemenin metin adı, sürüm, kültür ve ortak anahtar belirteci oluşur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Iclrstrongname arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
