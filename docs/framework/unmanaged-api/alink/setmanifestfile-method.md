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
ms.openlocfilehash: a253503f3046c004cc7109a31b5aa8fd8e8dc195
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54618057"
---
# <a name="setmanifestfile-method"></a>SetManifestFile Yöntemi
Bağlayıcı derleme oluşturduğunda kullandığı bildirim dosyası sıfırlamak sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT SetManifestFile(  
    LPCWSTR pszFile  
) PURE;  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pszFile`  
  
 İçerikleri Win32 kaynakları blob yerleştirilir bildirimi dosyasının adı.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu, Win32ResBlob için soran önce çağırın. Değerini `pszFile` parametredir içerikleri okuma ve Win32 kaynakları, kimliği rt_manıfest ile koymak bildirim dosyasının adı. Bir parametre null kullanarak çağrıldığında, daha önce okuma herhangi bir bildirim temizlenir. Bu, bir başlatma süresi, bağlayıcı durumunu sıfırlamak sağlar.  
  
## <a name="requirements"></a>Gereksinimler  
 ALink.h gerektirir  
  
## <a name="see-also"></a>Ayrıca bkz.
- [IALink3 Yöntemi](../../../../docs/framework/unmanaged-api/alink/ialink3-interface.md)
- [ALink API](../../../../docs/framework/unmanaged-api/alink/index.md)
- [IALink Arabirimi](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [Al.exe (Bütünleştirilmiş Kod Bağlayıcı)](../../../../docs/framework/tools/al-exe-assembly-linker.md)
