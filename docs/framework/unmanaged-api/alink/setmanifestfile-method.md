---
title: SetManifestFile Yöntemi
ms.date: 03/30/2017
api_name:
- IALink3.SetManifestFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetManifestFile
helpviewer_keywords:
- SetManifestFile method
ms.assetid: 1b33de4c-19cb-4a36-a93f-8675b2a36d58
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8f8398c16b27836b772e8ac56ee1f7e8494f4be0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="setmanifestfile-method"></a>SetManifestFile Yöntemi
Bağlayıcı derleme oluşturduğunda kullanan bildirim dosyası sıfırlamak mı sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT SetManifestFile(  
    LPCWSTR pszFile  
) PURE;  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pszFile`  
  
 İçerikleri Win32 kaynakları blob'a put bildirim dosyasının adı.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu için Win32ResBlob soran önce çağırın. Değeri `pszFile` parametredir içerikleri okuma ve kimliği, RT_MANIFEST Win32 kaynaklarla koymak bildirim dosyasının adı. Null parametresiyle çağrıldığında, daha önce okuma herhangi bildirimi temizlenir. Bu, başlangıç zamanı bağlayıcı durumunu sıfırlamak için sağlar.  
  
## <a name="requirements"></a>Gereksinimler  
 ALink.h gerektirir  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IALink3 Yöntemi](../../../../docs/framework/unmanaged-api/alink/ialink3-interface.md)  
 [ALink API](../../../../docs/framework/unmanaged-api/alink/index.md)  
 [IALink Arabirimi](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [Al.exe (Bütünleştirilmiş Kod Bağlayıcı)](../../../../docs/framework/tools/al-exe-assembly-linker.md)
