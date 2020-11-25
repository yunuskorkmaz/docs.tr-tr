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
ms.openlocfilehash: a4518e93db887dbdc4397636479be8bf5a705c2d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733730"
---
# <a name="setmanifestfile-method"></a>SetManifestFile Yöntemi

Bağlayıcının, derlemeyi oluşturduğunda kullandığı bildirim dosyasını belirtmenize veya sıfırlamasına olanak sağlar.  
  
## <a name="syntax"></a>Söz dizimi  
  
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

 Win32ResBlob sorulmadan önce bunu çağırın. Parametresinin değeri, `pszFile` içeriği okunan ve RT_MANIFEST kimliği olan Win32 kaynaklarına yerleştirilen bildirim dosyasının adıdır. NULL parametresi kullanılarak çağrıldığında, daha önce okuma bildirimi temizlenir. Bu, bir tane, bağlayıcının durumunu başlatma zamanına sıfırlamasına olanak sağlar.  
  
## <a name="requirements"></a>Gereksinimler  

 ALink. h gerektirir  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IALink3 Arabirimi](ialink3-interface.md)
- [ALink API](index.md)
- [IALink Arabirimi](ialink-interface.md)
- [Al.exe (bütünleştirilmiş kod bağlayıcı)](../../tools/al-exe-assembly-linker.md)
