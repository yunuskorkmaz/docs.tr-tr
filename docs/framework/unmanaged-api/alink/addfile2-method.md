---
title: "AddFile2 Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- AddFile2
- IALink2.AddFile2
api_location: alink.dll
api_type: COM
f1_keywords: AddFile2
helpviewer_keywords: AddFile2 method
ms.assetid: 03bc49bf-a89b-4fb6-a88d-97482e061195
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: fe10a3ca8930087a52d02905534696dbb2d8fb25
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="addfile2-method"></a>AddFile2 Yöntemi
Dosyaları derlemeye ekler. Ayrıca ilişkisiz modülleri oluşturmak için kullanılabilir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT AddFile2(  
    mdAssembly AssemblyID,  
    LPCWSTR pszFilename,  
    DWORD dwFlags,  
    IMetaDataEmit2* pEmitter,  
    mdFile* pFileToken  
) PURE;  
```  
  
#### <a name="parameters"></a>Parametreler  
 `AssemblyID`  
 Dosya ekleneceği derleme kimliği.  
  
 `pszFilename`  
 Eklenecek dosyanın adı.  
  
 `dwFlags`  
 COM + `FileDef` gibi bayrakları `ffContainsNoMetaData` ve `ffWriteable`. `dwFlags`geçirilir [DefineFile yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).  
  
 `pEmitter`  
 Arabirimini [Imetadataemit2 arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md) arabirimi.  
  
 `pFileToken`  
 Eklenen dosyanın kimliği alır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 ALink.h gerektirir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Ialink2 arabirimi](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [Ialink arabirimi](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [ALink API](../../../../docs/framework/unmanaged-api/alink/index.md)
