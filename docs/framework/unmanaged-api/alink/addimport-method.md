---
title: "Addımport Method1"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- AddImport
- IALink.AddImport
api_location: alink.dll
api_type: COM
f1_keywords: AddImport
helpviewer_keywords: AddImport method
ms.assetid: 4fedf8a0-08c8-43d0-aa00-20f2a521c991
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: cd0e55cab6f0fdb7f971d7cf06e5703340e32307
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="addimport-method1"></a>Addımport Method1
İçeri aktarmalar derlemeye ekler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT AddImport(  
    mdAssembly      AssemblyID,  
    mdToken         ImportToken,  
    DWORD           dwFlags,  
    mdFile*         pFileToken  
) PURE;  
```  
  
#### <a name="parameters"></a>Parametreler  
 `AssemblyID`  
 Derleme engagement'ta benzersiz kimliği.  
  
 `ImportToken`  
 Benzersiz kimliği alınan [ImportFile yöntemi](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), içeri aktarılacak dosya.  
  
 `dwFlags`  
 COM + FileDef bayrakları gibi `ffContainsNoMetaData` ve `ffWriteable`. `dwFlags`geçirilir [DefineFile yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).  
  
 `pFileToken`  
 Sonuç dosyası kimliği aldığı belirteci işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 ALink.h gerektirir  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Ialink arabirimi](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [Ialink2 arabirimi](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [ALink API](../../../../docs/framework/unmanaged-api/alink/index.md)
