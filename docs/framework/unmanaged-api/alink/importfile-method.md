---
title: "ImportFile Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.ImportFile
api_location: alink.dll
api_type: COM
f1_keywords: ImportFile
helpviewer_keywords: ImportFile method
ms.assetid: bcbe321f-b83a-4e9a-9f10-8d913e244dc9
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 46830699ba43c406da313653e1910e8f7a18a2ae
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="importfile-method"></a>ImportFile Yöntemi
Derlemeler ve ilişkisiz modülleri içeri aktarır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT ImportFile(  
    LPCWSTR pszFilename,  
    LPCWSTR pszTargetName,  
    BOOL fSmartImport,  
    mdToken* pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD* pdwCountOfScopes  
) PURE;  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pszFilename`  
 İçeri aktarılacak dosya tam adı.  
  
 `pszTargetName`  
 Derlemeye bağlı olarak dosyayı yeniden adlandırmak için kullanılan isteğe bağlı çıktı dosyası adı.  
  
 `fSmartImport`  
 TRUE ise, Importtypes kullanılan, aksi takdirde içeri aktarma el ile yapılmalıdır.  
  
 `pImportToken`  
 Benzersiz dosya kimliği depolanacağı belirtecine işaretçi. Dosya, bir derlemeyi ya da bir dosya olabilir.  
  
 `ppAssemblyScope`  
 İşaretçi alır [Imetadataassemblyımport arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md). Dosya bir derleme değilse NULL olabilir.  
  
 `pdwCountOfScopes`  
 Dosyaları ve/veya içeri aktarıldığını kapsamların sayısı işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 ALink.h gerektirir  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Ialink arabirimi](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [Ialink2 arabirimi](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [ALink API](../../../../docs/framework/unmanaged-api/alink/index.md)
