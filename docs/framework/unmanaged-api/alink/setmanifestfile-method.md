---
title: "SetManifestFile Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink3.SetManifestFile
api_location: alink.dll
api_type: COM
f1_keywords: SetManifestFile
helpviewer_keywords: SetManifestFile method
ms.assetid: 1b33de4c-19cb-4a36-a93f-8675b2a36d58
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 807452326193d193f3bc603ebc7b74a5a0f1c281
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
 [Ialink3 arabirimi](../../../../docs/framework/unmanaged-api/alink/ialink3-interface.md)  
 [ALink API](../../../../docs/framework/unmanaged-api/alink/index.md)  
 [Ialink arabirimi](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [Al.exe (derleme bağlayıcı)](../../../../docs/framework/tools/al-exe-assembly-linker.md)
