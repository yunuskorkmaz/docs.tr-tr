---
title: ICLRStrongName::StrongNameSignatureVerificationFromImage Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureVerificationFromImage
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureVerificationFromImage
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureVerificationFromImage method [.NET Framework hosting]
- StrongNameSignatureVerificationFromImage method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: da91c138-ee30-4fd4-a040-464d97d7e41a
topic_type:
- apiref
ms.openlocfilehash: 1ba7355fae1888436d57562cc21d3865ebc7a4f4
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83763182"
---
# <a name="iclrstrongnamestrongnamesignatureverificationfromimage-method"></a>ICLRStrongName::StrongNameSignatureVerificationFromImage Yöntemi
Zaten bellekle eşlenmiş bir derlemenin ilişkili ortak anahtar için geçerli olduğunu doğrular.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT StrongNameSignatureVerificationFromImage (  
    [in]  BYTE    *pbBase,  
    [in]  DWORD   dwLength,  
    [in]  DWORD   dwInFlags,  
    [out] DWORD   *pdwOutFlags  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pbBase`  
 'ndaki Eşlenen derleme bildiriminin göreli sanal adresi.  
  
 `dwLength`  
 'ndaki Eşlenen görüntünün bayt cinsinden boyutu.  
  
 `dwInFlags`  
 'ndaki Doğrulama davranışını etkileyen bayraklar. Aşağıdaki değerler desteklenir:  
  
- `SN_INFLAG_FORCE_VER`(0x00000001)-kayıt defteri ayarlarını geçersiz kılmak gerekli olsa bile doğrulamayı zorlar.  
  
- `SN_INFLAG_INSTALL`(0x00000002)-Bu görüntüde gerçekleştirilen ilk doğrulamanın olduğunu belirtir.  
  
- `SN_INFLAG_ADMIN_ACCESS`(0x00000004)-önbelleğin yalnızca yönetici ayrıcalıklarına sahip olan kullanıcılar için erişime izin verolacağını belirtir.  
  
- `SN_INFLAG_USER_ACCESS`(0x00000008)-derlemenin yalnızca geçerli kullanıcı için erişilebilir olacağını belirtir.  
  
- `SN_INFLAG_ALL_ACCESS`(0x00000010)-önbelleğin erişim kısıtlaması garantisi sunmayacak olduğunu belirtir.  
  
- `SN_INFLAG_RUNTIME`(0x80000000)-iç hata ayıklama için ayrılmıştır.  
  
 `pdwOutFlags`  
 dışı Ek çıkış bilgileri için bayrak. Aşağıdaki değer desteklenir:  
  
- `SN_OUTFLAG_WAS_VERIFIED`(0x00000001)-Bu değer `false` , kayıt defteri ayarları nedeniyle doğrulamanın başarılı olduğunu belirtmek için olarak ayarlanır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `S_OK`Yöntem başarıyla tamamlanırsa; Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](/windows/win32/seccrypto/common-hresult-values) ).  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MetaHost. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRStrongName Arabirimi](iclrstrongname-interface.md)
