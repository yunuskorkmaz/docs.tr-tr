---
title: "ImportFileEx2 Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink2.ImportFileEx2
api_location: alink.dll
api_type: COM
f1_keywords: ImportFileEx2
helpviewer_keywords: ImportFileEx2 method
ms.assetid: 02c789fd-16fc-48c6-9619-56e87e2a37ca
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c2416a630f9bd763d4d4d31170cc606b160bb854
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="importfileex2-method"></a>ImportFileEx2 Yöntemi
Derlemeler ve ilişkisiz modülleri içeri aktarır. Bu yöntem benzer [ImportFile yöntemi](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), ancak içeri aktarılan dosya diskte yok olsa bile çalışır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT ImportFileEx2(  
    LPCWSTR pszFilename,  
    LPCWSTR pszTargetName,  
    IMetaDataAssemblyImport* pAssemblyScopeIn,  
    BOOL fSmartImport,  
    DWORD dwOpenFlags,  
    mdToken* pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD* pdwCountOfScopes  
) PURE;  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pszFilename`  
 İçeri aktarılacak dosya adı.  
  
 `pszTargetName`  
 Hedef dosya adı isteğe bağlıdır.  
  
 `pAssemblyScopeIn`  
 İsteğe bağlı alma kapsam [Imetadataassemblyımport arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) arabirimi.  
  
 `fSmartImport`  
 TRUE ise, Importtypes kullanılan, aksi takdirde içeri aktarma el ile yapılmalıdır.  
  
 `dwOpenFlags`  
 Boyunca geçirilecek bayrakları [OpenScope yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md).  
  
 `pImportToken`  
 Derleme veya dosya için benzersiz kimlik alır.  
  
 `ppAssemblyScope`  
 Derleme alma kapsamı alır [Imetadataassemblyımport arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) arabirimi. Dosya bir derleme değilse NULL olabilir.  
  
 `pdwCountOfScopes`  
 Dosyaları ve/veya içeri kapsamları sayısını alır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 ALink.h gerektirir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Ialink2 arabirimi](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [Ialink arabirimi](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [ALink API](../../../../docs/framework/unmanaged-api/alink/index.md)
