---
title: ICLRStrongName::StrongNameCompareAssemblies Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameCompareAssemblies
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameCompareAssemblies
helpviewer_keywords:
- ICLRStrongName::StrongNameCompareAssemblies method [.NET Framework hosting]
- StrongNameCompareAssemblies method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: b1fb356c-72cf-4aa4-8376-f291a6d97c01
topic_type:
- apiref
ms.openlocfilehash: ddcbe84053aa7f4cafd81e905f8aef988f92875e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95685709"
---
# <a name="iclrstrongnamestrongnamecompareassemblies-method"></a>ICLRStrongName::StrongNameCompareAssemblies Yöntemi

İki derlemenin yalnızca kendi tanımlayıcı ad imzalarına göre farklı olup olmadığını belirler.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT StrongNameCompareAssemblies (  
    [in]  LPCWSTR   wszAssembly1,  
    [in]  LPCWSTR   wszAssembly2,  
    [out] DWORD     *pdwResult  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `wszAssembly1`  
 'ndaki İlk derlemenin yolu.  
  
 `wszAssembly2`  
 'ndaki İkinci derlemenin yolu.  
  
 `pdwResult`  
 dışı Aşağıdaki değerlerden biri:  
  
- `SN_CMP_DIFFERENT` (0)-derlemelerin farklı veriler içerdiğini belirtir.  
  
- `SN_CMP_IDENTICAL` (1)-derlemelerin imzaları ve sağlama toplamı dahil olmak üzere tam olarak aynı olduğunu belirtir.  
  
- `SN_CMP_SIGONLY` (2)-derlemelerin yalnızca imzaya ve sağlama toplamına göre farklı olduğunu belirtir.  
  
## <a name="return-value"></a>Dönüş Değeri  

 `S_OK` Yöntem başarıyla tamamlanırsa; Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](/windows/win32/seccrypto/common-hresult-values) ).  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MetaHost. h  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="remarks"></a>Açıklamalar  

 Bir derlemenin tanımlayıcı ad imzası, derlemenin metin adı, sürüm, kültür ve ortak anahtar belirtecinden oluşur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRStrongName Arabirimi](iclrstrongname-interface.md)
