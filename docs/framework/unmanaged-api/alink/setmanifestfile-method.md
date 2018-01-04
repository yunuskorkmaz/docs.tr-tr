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
ms.workload: dotnet
ms.openlocfilehash: cf48153454fbb2c24dc3f1cfe1f82deefa4ee723
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
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
