---
description: ': ICLRStrongName:: StrongNameGetBlobFromImage yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 32f04e21f1f08f3872ccdd27a64f39ea29d7e060
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799622"
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
 'ndaki İçindeki görüntünün bayt cinsinden boyutu `pbBase` .  
  
 `pbBlob`  
 'ndaki Görüntünün ikili gösterimini içeren bir arabellek.  
  
 `pcbBlob`  
 [in, out] İstenen en büyük boyut (bayt) `pbBlob` . Dönüş sonrasında, bayt cinsinden gerçek boyut `pbBlob` .  
  
## <a name="return-value"></a>Dönüş Değeri  

 `S_OK` Yöntem başarıyla tamamlanırsa; Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](/windows/win32/seccrypto/common-hresult-values) ).  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MetaHost. h  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [StrongNameGetBlob Yöntemi](iclrstrongname-strongnamegetblob-method.md)
- [ICLRStrongName Arabirimi](iclrstrongname-interface.md)
