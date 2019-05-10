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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 04e562b41b3d835d66fb9b803ee7db1c7fb8537f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662553"
---
# <a name="corvalidateimage-function"></a>_CorValidateImage İşlevi
Yönetilen modül görüntüleri doğrular ve bunlar yüklendikten sonra işletim sistemi yükleyicisi bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
STDAPI _CorValidateImage (   
   [in] PVOID* ImageBase,  
   [in] LPCWSTR FileName  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ImageBase`  
 [in] Yönetilen kod bir işaretçi olarak doğrulamak için görüntüsünün başlangıç konumu. Görüntü zaten belleğe yüklenmesi gerekir.  
  
 `FileName`  
 [in] Görüntü dosyası adı.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu işlev, standart değerleri döndürür `E_INVALIDARG`, `E_OUTOFMEMORY`, `E_UNEXPECTED`, ve `E_FAIL`, aşağıdaki değerleri yanı sıra.  
  
|Dönüş değeri|Açıklama|  
|------------------|-----------------|  
|`STATUS_INVALID_IMAGE_FORMAT`|Görüntü geçersiz. Bu değer, HRESULT 0xC000007BL sahiptir.|  
|`STATUS_SUCCESS`|Görüntü geçerli değil. Bu değer, HRESULT 0x00000000L sahiptir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Windows XP ve sonraki sürümlerinde, işletim sistemi yükleyicisi yönetilen modüller için ortak nesne dosyası biçimi (COFF) üst bilgisindeki COM tanımlayıcısı dizin bit inceleyerek denetler. Yönetilen bir modül bit kümesinin gösterir. Yükleyici, yönetilen bir modül algılarsa, MsCorEE.dll ve aramalar yükler `_CorValidateImage`, aşağıdaki eylemleri gerçekleştirir:  
  
- Görüntünün geçerli yönetilen bir modül olduğunu doğrular.  
  
- Ortak dil çalışma zamanı (CLR) bir giriş noktası için giriş noktası görüntüde değiştirir.  
  
- Windows 64-bit sürümleri için bellekte PE32 je typu PE32 + biçimine dönüştürerek görüntü değiştirir.  
  
- Yönetilen modül görüntüleri yüklendiğinde yükleyici geri döner.  
  
 Yürütülebilir görüntüler için işletim sistemi yükleyicisi sonra çağıran [_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) işlevi, bağımsız yürütülebilir dosya belirtilen giriş noktası olarak. DLL derleme görüntüler için yükleyici çağırır [_CorDllMain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md) işlevi.  
  
 `_CorExeMain` veya `_CorDllMain` aşağıdaki eylemleri gerçekleştirir:  
  
- CLR'yi başlatır.  
  
- Derlemesinin CLR başlığındaki yönetilen giriş noktasını bulur.  
  
- Yürütmeyi başlatır.  
  
 Yükleyici çağrıları [_corımageunloading](../../../../docs/framework/unmanaged-api/hosting/corimageunloading-function.md) işlev yönetilen modül görüntüleri kaldırıldı. Ancak, bu işlev, herhangi bir işlem gerçekleştirmez; hemen döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** COR.h  
  
 **Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Genel Statik İşlevleri](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
