---
title: ImportFile2 Yöntemi
ms.date: 03/30/2017
api_name:
- IALink.ImportFile2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportFile2
helpviewer_keywords:
- ImportFile2 method
ms.assetid: 9a6be861-c260-4a35-acea-3372ea515a0f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b3c145bae61922894f4893d532923319ccf16f85
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54499018"
---
# <a name="importfile2-method"></a>ImportFile2 Yöntemi
Derlemeler ve bağlantısız modülleri içeri aktarır. Bu yöntem benzer [ImportFile yöntemi](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), ancak içeri aktarılan dosyanın diskte mevcut değilse bile çalışır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT ImportFile2(  
    LPCWSTR         pszFilename,  
    LPCWSTR         pszTargetName,  
    IMetaDataAssemblyImport* pAssemblyScopeIn,  
    BOOL            fSmartImport,  
    mdToken*        pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD*          pdwCountOfScopes  
) PURE;  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pszFilename`  
 İçeri aktarılacak dosya adı.  
  
 `pszTargetName`  
 Bütünleştirilmiş kod içine bağlı olarak dosyayı yeniden adlandırmak için kullanılabilecek isteğe bağlı bir çıkış dosyası adı.  
  
 `pAssemblyScopeIn`  
 İsteğe bağlı kapsam [Imetadataassemblyımport arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) arabirimi.  
  
 `fSmartImport`  
 TRUE ise Importtypes kullanılır, aksi takdirde içe aktarma el ile uygulanması gerekir.  
  
 `pImportToken`  
 Dosya veya derleme Kimliğini alır.  
  
 `ppAssemblyScope`  
 Alan [Imetadataassemblyımport arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) arabirimi. Dosyanın bir derleme değilse null değerini DÖNDÜRÜR.  
  
 `pdwCountOfScopes`  
 Bulunan dosyaları ve/veya içe kapsamları alır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 ALink.h gerektirir.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [IALink Arabirimi](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [IALink2 Arabirimi](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [ALink API](../../../../docs/framework/unmanaged-api/alink/index.md)
