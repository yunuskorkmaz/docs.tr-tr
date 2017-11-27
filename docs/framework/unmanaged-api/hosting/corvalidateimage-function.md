---
title: "_CorValidateImage İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: _CorValidateImage
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: _CorValidateImage
helpviewer_keywords: _CorValidateImage function [.NET Framework hosting]
ms.assetid: 0117e080-05f9-4772-885d-e1847230947c
topic_type: apiref
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e2396219a5e4bfd95a9dc7134e2e603ed7a15a3d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
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
  
#### <a name="parameters"></a>Parametreler  
 `ImageBase`  
 [in] Yönetilen kod bir işaretçi olarak doğrulamak için görüntüsünün başlangıç konumu. Görüntü zaten belleğe yüklenmiş olmalıdır.  
  
 `FileName`  
 [in] Yansıma Dosya adı.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu işlev, standart değerleri döndürür `E_INVALIDARG`, `E_OUTOFMEMORY`, `E_UNEXPECTED`, ve `E_FAIL`, aşağıdaki değerleri yanı sıra.  
  
|Dönüş değeri|Açıklama|  
|------------------|-----------------|  
|`STATUS_INVALID_IMAGE_FORMAT`|Görüntüsü geçersiz. Bu değer HRESULT 0xC000007BL sahiptir.|  
|`STATUS_SUCCESS`|Görüntü geçerli değil. Bu değer HRESULT 0x00000000L sahiptir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Windows XP ve sonraki sürümlerinde, işletim sistemi yükleyicisi ortak nesne dosya biçimi (COFF) üstbilgisinde COM tanımlayıcısı dizin bit inceleyerek yönetilen modülleri için denetler. Yönetilen bir modül kümesini bit gösterir. Yükleyici yönetilen bir modül algılarsa, MsCorEE.dll ve çağrıları yüklerken `_CorValidateImage`, aşağıdaki eylemleri gerçekleştirir:  
  
-   Görüntü geçerli bir yönetilen modül olduğunu doğrular.  
  
-   Ortak dil çalışma zamanı (CLR) bir giriş noktası için giriş noktası görüntüdeki değiştirir.  
  
-   Windows'un 64 bit sürümleri için PE32 PE32 + biçimine dönüştürerek bellekte görüntüsü değiştirir.  
  
-   Yönetilen modül görüntüleri yüklendiğinde yükleyicisi geri döner.  
  
 Yürütülebilir görüntüler, işletim sistemi yükleyicisi sonra çağırır [_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) işlevi, bağımsız olarak yürütülebilir dosya belirtilen giriş noktası. DLL derleme görüntülerde yükleyicisi çağırır [_CorDllMain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md) işlevi.  
  
 `_CorExeMain`veya `_CorDllMain` aşağıdaki eylemleri gerçekleştirir:  
  
-   CLR başlatır.  
  
-   Derlemenin CLR başlığından yönetilen giriş noktası bulur.  
  
-   Yürütme başlar.  
  
 Yükleyici çağrıları [_corımageunloading](../../../../docs/framework/unmanaged-api/hosting/corimageunloading-function.md) işlev yönetildiğinde modülü görüntüleri kaldırıldı. Ancak, bu işlev, herhangi bir işlem gerçekleştirmez; yalnızca döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Cor.h  
  
 **Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Meta veri genel statik işlevleri](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
