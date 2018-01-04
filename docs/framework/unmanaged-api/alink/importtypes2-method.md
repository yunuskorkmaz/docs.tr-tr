---
title: "ImportTypes2 Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink2.ImportTypes2
api_location: alink.dll
api_type: COM
f1_keywords: ImportTypes2
helpviewer_keywords: ImportTypes2 method
ms.assetid: 32f3ba58-9695-41e9-ba58-fd19e45ed396
topic_type: apiref
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 47c49253a1e2839939ef4e671f155e4a44d07529
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="importtypes2-method"></a>ImportTypes2 Yöntemi
Türleri alma işlemini başlatır. Üzerinden içe aktarılan her kapsamdan türleri almaya başlamak için bu yöntemi çağırın [ImportFile yöntemi](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT ImportTypes2(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    HALINKENUM* phEnum,  
    IMetaDataImport2** ppImportScope,  
    DWORD* pdwCountOfTypes  
) PURE;  
```  
  
#### <a name="parameters"></a>Parametreler  
 `AssemblyID`  
 İçeri aktarılacak derlemeye kimliği.  
  
 `FileToken`  
 İçeri aktarmak için dosya kimliği.  
  
 `dwScope`  
 Sıfır tabanlı kapsamı içeri aktarılacak.  
  
 `phEnum`  
 Numaralandırıcı tanıtıcı türleri için verilen kapsam içinde alır.  
  
 `ppImportScope`  
 İsteğe bağlı olarak alan [Imetadataımport2 arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md) arabirimi.  
  
 `pdwCountOfTypes`  
 İsteğe bağlı olarak belirtilen kapsamında türleri sayısını alır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 ALink.h gerektirir  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IALink2 Arabirimi](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [IALink Arabirimi](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [ALink API](../../../../docs/framework/unmanaged-api/alink/index.md)
