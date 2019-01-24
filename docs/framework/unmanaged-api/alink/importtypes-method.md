---
title: ImportTypes Yöntemi
ms.date: 03/30/2017
api_name:
- IALink.ImportTypes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportTypes
helpviewer_keywords:
- ImportTypes method
ms.assetid: 351d4b4c-c939-486d-9471-51914a55f471
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6591fb4a2b4944dc0d02f70f0f90ffd87e071c47
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54735015"
---
# <a name="importtypes-method"></a>ImportTypes Yöntemi
Türleri aracılığıyla alınan her bir kapsamdan içeri aktarma başlatır [ImportFile yöntemi](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT ImportTypes(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    HALINKENUM* phEnum,  
    IMetaDataImport** ppImportScope,  
    DWORD* pdwCountOfTypes  
) PURE;  
```  
  
#### <a name="parameters"></a>Parametreler  
 `AssemblyID`  
 Almak için derleme kimliği.  
  
 `FileToken`  
 Alınacak dosya kimliği.  
  
 `dwScope`  
 İçeri aktarmak için sıfır tabanlı kapsam.  
  
 `phEnum`  
 Numaralandırıcı tanıtıcı türleri için bu kapsamda yer alır.  
  
 `ppImportScope`  
 İsteğe bağlı olarak alan [Imetadataımport arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) arabirimi.  
  
 `pdwCountOfTypes`  
 İsteğe bağlı olarak belirtilen kapsamda türleri sayısını alır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 ALink.h gerektirir  
  
## <a name="see-also"></a>Ayrıca bkz.
- [IALink Arabirimi](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [IALink2 Arabirimi](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [ALink API](../../../../docs/framework/unmanaged-api/alink/index.md)
