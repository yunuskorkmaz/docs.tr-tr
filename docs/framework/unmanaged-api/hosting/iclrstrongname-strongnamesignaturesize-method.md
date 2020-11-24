---
title: ICLRStrongName::StrongNameSignatureSize Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureSize
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureSize method [.NET Framework hosting]
- StrongNameSignatureSize method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 76d4f93a-5e25-4399-abcc-a1389549481d
topic_type:
- apiref
ms.openlocfilehash: f43a4e65442ca79ece71ce7e5e014309a611d7cc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95671622"
---
# <a name="iclrstrongnamestrongnamesignaturesize-method"></a>ICLRStrongName::StrongNameSignatureSize Yöntemi

Tanımlayıcı ad imzasının boyutunu döndürür. Bu yöntem genellikle derleyiciler tarafından, gecikmeli imzalanmış bir derleme oluştururken dosyada ne kadar alan ayrılacağını tespit etmek için kullanılır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT StrongNameSignatureSize (
    [in]  BYTE   *pbPublicKeyBlob,  
    [in]  ULONG  cbPublicKeyBlob,
    [in]  DWORD  *pcbSize  
);
```  
  
## <a name="parameters"></a>Parametreler  

 `pbPublicKeyBlob`  
 'ndaki Tanımlayıcı ad imzasını oluşturmak için kullanılan anahtar çiftinin ortak bölümünü içeren [PublicKeyBlob](../strong-naming/publickeyblob-structure.md) türünde bir yapı.  
  
 `cbPublicKeyBlob`  
 'ndaki Bayt cinsinden boyutu `pbPublicKeyBlob` .  
  
 `pcbSize`  
 'ndaki Tanımlayıcı ad imzasını depolamak için gereken bayt sayısı.  
  
## <a name="return-value"></a>Dönüş Değeri  

 `S_OK` Yöntem başarıyla tamamlanırsa; Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](/windows/win32/seccrypto/common-hresult-values) ).  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MetaHost. h  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRStrongName Arabirimi](iclrstrongname-interface.md)
