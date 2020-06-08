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
ms.openlocfilehash: 426b39aa3d1ada5ae44565a742b70681a7bcf6d3
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493480"
---
# <a name="_corvalidateimage-function"></a>_CorValidateImage İşlevi
Yönetilen modül görüntülerini doğrular ve yüklendikten sonra işletim sistemi yükleyicisini bilgilendirir.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
 Bu işlev, `E_INVALIDARG` `E_OUTOFMEMORY` `E_UNEXPECTED` aşağıdaki değerleri ve,,, ve standart değerlerini döndürür `E_FAIL` .  
  
|Döndürülen değer|Description|  
|------------------|-----------------|  
|`STATUS_INVALID_IMAGE_FORMAT`|Görüntü geçersiz. Bu değer HRESULT 0xC000007BL.|  
|`STATUS_SUCCESS`|Görüntü geçerli. Bu değer HRESULT 0x00000000L ' i içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Windows XP ve sonraki sürümlerinde, işletim sistemi yükleyicisi ortak nesne dosyası biçimi (COFF) üstbilgisindeki COM tanımlayıcı dizin bitini inceleyerek yönetilen modülleri denetler. Set bit, yönetilen bir modülü gösterir. Yükleyici yönetilen bir modül algılarsa, MsCorEE. dll ve çağrılarını yükler ve `_CorValidateImage` aşağıdaki eylemleri gerçekleştirir:  
  
- Görüntünün geçerli bir yönetilen modül olduğunu onaylar.  
  
- Görüntüdeki giriş noktasını, ortak dil çalışma zamanında (CLR) bir giriş noktasına değiştirir.  
  
- Windows 'un 64 bitlik sürümleri için, bellekte bulunan görüntüyü PE32 ' dan PE32 + biçimine dönüştürerek değiştirir.  
  
- Yönetilen modül görüntüleri yüklendiğinde yükleyice döndürür.  
  
 Yürütülebilir görüntüler için, işletim sistemi yükleyicisi, yürütülebilir dosyada belirtilen giriş noktası ne olursa olsun [_CorExeMain](corexemain-function.md) işlevini çağırır. DLL derleme görüntüleri için yükleyici [_CorDllMain](cordllmain-function.md) işlevini çağırır.  
  
 `_CorExeMain`ya da `_CorDllMain` aşağıdaki eylemleri gerçekleştirir:  
  
- CLR 'yi başlatır.  
  
- Yönetilen giriş noktasını derlemenin CLR üst bilgisinden konumlandırır.  
  
- Yürütmeye başlar.  
  
 Yükleyici, yönetilen modül görüntüleri kaldırıldığında [_CorImageUnloading](corimageunloading-function.md) işlevini çağırır. Ancak, bu işlev herhangi bir eylem gerçekleştirmez; yalnızca döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Genel Statik İşlevleri](../metadata/metadata-global-static-functions.md)
