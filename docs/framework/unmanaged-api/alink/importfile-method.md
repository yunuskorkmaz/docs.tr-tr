---
title: ImportFile Yöntemi
ms.date: 03/30/2017
api_name:
- IALink.ImportFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportFile
helpviewer_keywords:
- ImportFile method
ms.assetid: bcbe321f-b83a-4e9a-9f10-8d913e244dc9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 54b0a02af7f22e775e3f9567de79664c9805b4e2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
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
 [IALink Arabirimi](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [IALink2 Arabirimi](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [ALink API](../../../../docs/framework/unmanaged-api/alink/index.md)
