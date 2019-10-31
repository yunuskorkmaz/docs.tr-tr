---
title: ICLRStrongName::StrongNameGetBlobFromImage Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameGetBlobFromImage
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameGetBlobFromImage
helpviewer_keywords:
- StrongNameGetBlobFromImage method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameGetBlobFromImage method [.NET Framework hosting]
ms.assetid: 0f5a2ec8-e776-4fd8-bda6-937b6834575a
topic_type:
- apiref
ms.openlocfilehash: ad3b151165eb233bd3a4a78d8f4d612a696b7e93
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73135104"
---
# <a name="iclrstrongnamestrongnamegetblobfromimage-method"></a>ICLRStrongName::StrongNameGetBlobFromImage Yöntemi
Belirtilen bellek adresindeki derleme görüntüsünün ikili gösterimini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT StrongNameGetBlobFromImage (  
    [in]  BYTE        *pbBase,  
    [in]  DWORD       dwLength,  
    [in]  BYTE        *pbBlob,  
    [in, out] DWORD   *pcbBlob  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pbBase`  
 'ndaki Eşlenen derleme bildiriminin bellek adresi.  
  
 `dwLength`  
 'ndaki `pbBase`konumundaki görüntünün bayt cinsinden boyutu.  
  
 `pbBlob`  
 'ndaki Görüntünün ikili gösterimini içeren bir arabellek.  
  
 `pcbBlob`  
 [in, out] `pbBlob`istenen en büyük boyut (bayt cinsinden). Dönüş sonrasında, `pbBlob`bayt cinsinden gerçek boyut.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarıyla tamamlanırsa `S_OK`; Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](https://go.microsoft.com/fwlink/?LinkId=213878) ).  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MetaHost. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [StrongNameGetBlob Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md)
- [ICLRStrongName Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
