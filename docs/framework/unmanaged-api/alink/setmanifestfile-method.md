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
ms.openlocfilehash: b293c30060107d18c6b609efc82c4128a73cc1c7
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787201"
---
# <a name="setmanifestfile-method"></a>SetManifestFile Yöntemi
Bağlayıcının, derlemeyi oluşturduğunda kullandığı bildirim dosyasını belirtmenize veya sıfırlamasına olanak sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT SetManifestFile(  
    LPCWSTR pszFile  
) PURE;  
```  
  
## <a name="parameters"></a>Parametreler  
 `pszFile`  
  
 İçeriği Win32 kaynakları blobuna yerleştirilen bildirim dosyasının adı.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Win32ResBlob sorulmadan önce bunu çağırın. `pszFile` Parametresinin değeri, içeriği okunan bildirim dosyasının adı ve kimliği RT_MANIFEST olan Win32 kaynaklarına konur. NULL parametresi kullanılarak çağrıldığında, daha önce okuma bildirimi temizlenir. Bu, bir tane, bağlayıcının durumunu başlatma zamanına sıfırlamasına olanak sağlar.  
  
## <a name="requirements"></a>Gereksinimler  
 ALink. h gerektirir  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IALink3 Yöntemi](ialink3-interface.md)
- [ALink API](index.md)
- [IALink Arabirimi](ialink-interface.md)
- [Al.exe (Bütünleştirilmiş Kod Bağlayıcı)](../../tools/al-exe-assembly-linker.md)
