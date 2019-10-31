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
ms.openlocfilehash: 42da5bb761ba8ce388bd41d46e8fdc4561ad0290
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136877"
---
# <a name="_corvalidateimage-function"></a>_CorValidateImage İşlevi
Yönetilen modül görüntülerini doğrular ve yüklendikten sonra işletim sistemi yükleyicisini bilgilendirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
STDAPI _CorValidateImage (   
   [in] PVOID* ImageBase,  
   [in] LPCWSTR FileName  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ImageBase`  
 'ndaki Yönetilen kod olarak doğrulanacak görüntünün başlangıç konumuna yönelik bir işaretçi. Görüntü zaten belleğe yüklenmiş olmalıdır.  
  
 `FileName`  
 'ndaki Görüntünün dosya adı.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu işlev, `E_INVALIDARG`, `E_OUTOFMEMORY`, `E_UNEXPECTED`ve `E_FAIL`gibi standart değerleri, ayrıca aşağıdaki değerleri döndürür.  
  
|Dönüş değeri|Açıklama|  
|------------------|-----------------|  
|`STATUS_INVALID_IMAGE_FORMAT`|Görüntü geçersiz. Bu değer HRESULT 0xC000007BL.|  
|`STATUS_SUCCESS`|Görüntü geçerli. Bu değer HRESULT 0x00000000L ' i içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Windows XP ve sonraki sürümlerinde, işletim sistemi yükleyicisi ortak nesne dosyası biçimi (COFF) üstbilgisindeki COM tanımlayıcı dizin bitini inceleyerek yönetilen modülleri denetler. Set bit, yönetilen bir modülü gösterir. Yükleyici yönetilen bir modül algılarsa, MsCorEE. dll dosyasını yükler ve `_CorValidateImage`çağırır ve aşağıdaki eylemleri gerçekleştirir:  
  
- Görüntünün geçerli bir yönetilen modül olduğunu onaylar.  
  
- Görüntüdeki giriş noktasını, ortak dil çalışma zamanında (CLR) bir giriş noktasına değiştirir.  
  
- Windows 'un 64 bitlik sürümleri için, bellekte bulunan görüntüyü PE32 ' dan PE32 + biçimine dönüştürerek değiştirir.  
  
- Yönetilen modül görüntüleri yüklendiğinde yükleyice döndürür.  
  
 Yürütülebilir görüntüler için, işletim sistemi yükleyicisi, yürütülebilir dosyada belirtilen giriş noktası ne olursa olsun, [_Corexemain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) işlevini çağırır. DLL derleme görüntüleri için yükleyici [_Cordllmain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md) işlevini çağırır.  
  
 `_CorExeMain` veya `_CorDllMain` aşağıdaki eylemleri gerçekleştirir:  
  
- CLR 'yi başlatır.  
  
- Yönetilen giriş noktasını derlemenin CLR üst bilgisinden konumlandırır.  
  
- Yürütmeye başlar.  
  
 Yükleyici, yönetilen modül görüntüleri kaldırıldığında [_Corımagebellekten kaldırma](../../../../docs/framework/unmanaged-api/hosting/corimageunloading-function.md) işlevini çağırır. Ancak, bu işlev herhangi bir eylem gerçekleştirmez; yalnızca döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Genel Statik İşlevleri](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
