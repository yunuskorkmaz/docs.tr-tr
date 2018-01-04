---
title: "StrongNameCompareAssemblies İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameCompareAssemblies
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: StrongNameCompareAssemblies
helpviewer_keywords: StrongNameCompareAssemblies function [.NET Framework strong naming]
ms.assetid: 763f2375-efc6-4219-8806-a3b0567ef72b
topic_type: apiref
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1ed98b1713427a71c73c30ddd64188f61d51045c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="strongnamecompareassemblies-function"></a>StrongNameCompareAssemblies İşlevi
İki derleme yalnızca güçlü ad imzaları tarafından farklı olup olmadığını belirler.  
  
 Bu işlev kullanım dışı bırakıldı. Kullanım [Iclrstrongname::strongnamecompareassemblies](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamecompareassemblies-method.md) yöntemi yerine.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
BOOLEAN StrongNameCompareAssemblies (  
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
 `true`başarılı tamamlanma; Aksi takdirde `false`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** StrongName.h  
  
 **Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="remarks"></a>Açıklamalar  
 Bir derleme tanımlayıcı ad imzası derlemenin metin adı, sürüm, kültür ve ortak anahtar belirteci oluşur.  
  
 Varsa `StrongNameCompareAssemblies` işlevi yok başarıyla tamamlanması, çağrı [Strongnameerrorınfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) son oluşturulan hata alınacak işlev.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [StrongNameCompareAssemblies Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamecompareassemblies-method.md)  
 [ICLRStrongName Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
