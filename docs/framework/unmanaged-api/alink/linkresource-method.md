---
title: LinkResource Yöntemi
ms.date: 03/30/2017
api_name:
- IALink.LinkResource
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- LinkResource
helpviewer_keywords:
- LinkResource method
ms.assetid: c404acb3-4c59-4100-9a4c-483cbdb1d736
topic_type:
- apiref
ms.openlocfilehash: 4f2f13976dfd4e5601bf8b54bed7b851884fbb9d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95690453"
---
# <a name="linkresource-method"></a>LinkResource Yöntemi

Bir kaynaktaki bağlantılar.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT LinkResource(  
    mdAssembly  AssemblyID,  
    LPCWSTR     pszFileName,  
    LPCWSTR     pszNewLocation,  
    LPCWSTR     pszResourceName,  
    DWORD       dwFlags  
) PURE;  
```  
  
## <a name="parameters"></a>Parametreler  

 `AssemblyID`  
 Derlemenin KIMLIĞI.  
  
 `pszFileName`  
 Dosyanın adı.  
  
 `pszNewLocation`  
 İsteğe bağlı yeni dosya adı. NULL olmayan bir değer, `pszFileName` pszNewLocation ' a kopyalanacaktır.  
  
 `pszResourceName`  
 Kaynağın adı.  
  
 `dwFlags`  
 Ve gibi erişilebilirlik bayrakları `mrPublic` `mrPrivate` . Bu parametre [DefineManifestResource metoduna](../metadata/imetadataassemblyemit-definemanifestresource-method.md)geçirilebilir.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Yöntem başarılı olursa S_OK döndürür.  
  
## <a name="requirements"></a>Gereksinimler  

 ALink. h gerektirir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IALink Arabirimi](ialink-interface.md)
- [IALink2 Arabirimi](ialink2-interface.md)
- [ALink API](index.md)
