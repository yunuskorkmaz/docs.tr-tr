---
title: _CorValidateImage İşlevi
ms.date: 03/30/2017
api_name:
- _CorValidateImage
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- _CorValidateImage
helpviewer_keywords:
- _CorValidateImage function [.NET Framework hosting]
ms.assetid: 0117e080-05f9-4772-885d-e1847230947c
topic_type:
- apiref
ms.openlocfilehash: 3a6da0e845fa50d090cdf0808b211a5806c40961
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178210"
---
# <a name="_corvalidateimage-function"></a>_CorValidateImage İşlevi
Yönetilen modül görüntülerini doğrular ve yüklendikten sonra işletim sistemi yükleyicisini onaylar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
STDAPI _CorValidateImage (
   [in] PVOID* ImageBase,  
   [in] LPCWSTR FileName  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ImageBase`  
 [içinde] Yönetilen kod olarak doğrulamak için görüntünün başlangıç konumuna bir işaretçi. Görüntü zaten belleğe yüklenmiş olmalıdır.  
  
 `FileName`  
 [içinde] Resmin dosya adı.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu işlev standart `E_INVALIDARG`değerleri `E_OUTOFMEMORY` `E_UNEXPECTED`, `E_FAIL`, , ve , yanı sıra aşağıdaki değerleri döndürür.  
  
|Döndürülen değer|Açıklama|  
|------------------|-----------------|  
|`STATUS_INVALID_IMAGE_FORMAT`|Görüntü geçersiz. Bu değer HRESULT 0xC000007BL vardır.|  
|`STATUS_SUCCESS`|Görüntü geçerli. Bu değer HRESULT 0x00000000L vardır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Windows XP ve sonraki sürümlerde, işletim sistemi yükleyiciortak nesne dosya biçimi (COFF) üstbilgisinde COM Tanımlayıcı Dizin bitini inceleyerek yönetilen modülleri denetler. Bir ayar biti yönetilen bir modülü gösterir. Yükleyici yönetilen bir modülü algılarsa, MsCorEE.dll `_CorValidateImage`yükler ve aşağıdaki eylemleri gerçekleştiren çağrıları yapar:  
  
- Görüntünün geçerli bir yönetilen modül olduğunu doğrular.  
  
- Görüntüdeki giriş noktasını ortak dil çalışma zamanındaki (CLR) bir giriş noktasına değiştirir.  
  
- Windows'un 64 bit sürümleri için, BELLEKteki görüntüyü PE32'den PE32+ biçimine dönüştürerek değiştirir.  
  
- Yönetilen modül görüntüleri yüklendiğinde yükleyiciye geri döner.  
  
 Çalıştırılabilir görüntüler için, işletim sistemi yükleyicisi, yürütülebilir de belirtilen giriş noktası ne olursa olsun, [_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) işlevini çağırır. DLL montaj görüntüleri için yükleyici [_CorDllMain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md) işlevini çağırır.  
  
 `_CorExeMain`veya `_CorDllMain` aşağıdaki eylemleri gerçekleştirir:  
  
- CLR'yi başharfe iter.  
  
- Derlemenin CLR üstbilgisinden yönetilen giriş noktasını bulur.  
  
- İdam başlar.  
  
 Yönetilen modül görüntüleri boşaltıldığında yükleyici [_CorImageUnloading](../../../../docs/framework/unmanaged-api/hosting/corimageunloading-function.md) işlevini çağırır. Ancak, bu işlev herhangi bir eylem gerçekleştirmez; sadece geri döner.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** Cor.h  
  
 **Kütüphane:** MsCorEE.dll bir kaynak olarak dahil  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Genel Statik İşlevleri](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
