---
title: "ImportFile2 Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.ImportFile2
api_location: alink.dll
api_type: COM
f1_keywords: ImportFile2
helpviewer_keywords: ImportFile2 method
ms.assetid: 9a6be861-c260-4a35-acea-3372ea515a0f
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 4d7e842152e84992124ec29cd551c3b5d50a6d61
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="importfile2-method"></a>ImportFile2 Yöntemi
Derlemeler ve ilişkisiz modülleri içeri aktarır. Bu yöntem benzer [ImportFile yöntemi](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), ancak içeri aktarılan dosya diskte yok olsa bile çalışır.  
  
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
 Derlemeye bağlı olarak dosyayı yeniden adlandırmak için kullanılan isteğe bağlı çıktı dosyası adı.  
  
 `pAssemblyScopeIn`  
 İsteğe bağlı kapsam [Imetadataassemblyımport arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) arabirimi.  
  
 `fSmartImport`  
 TRUE ise, Importtypes kullanılan, aksi takdirde içeri aktarma el ile yapılmalıdır.  
  
 `pImportToken`  
 Dosya veya derleme Kimliğini alır.  
  
 `ppAssemblyScope`  
 Alan [Imetadataassemblyımport arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) arabirimi. Dosya bir derleme değilse null değerini DÖNDÜRÜR.  
  
 `pdwCountOfScopes`  
 Bulunan dosyaları ve/veya içeri kapsamları alır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 ALink.h gerektirir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Ialink arabirimi](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [Ialink2 arabirimi](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [ALink API](../../../../docs/framework/unmanaged-api/alink/index.md)
