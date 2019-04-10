---
title: GetScope2 Metodu
ms.date: 03/30/2017
api_name:
- IALink2.GetScope2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetScope2
helpviewer_keywords:
- GetScope2 method
ms.assetid: 49435665-6f5a-4acd-9034-8c9244a04a63
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a3c6b9e1239dc1baed9428d4fe967eb8274a9304
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59206037"
---
# <a name="getscope2-method"></a>GetScope2 Metodu
Bir içeri aktarma kapsamı alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetScope2(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    IMetaDataImport2** ppImportScope  
) PURE;   
```  
  
## <a name="parameters"></a>Parametreler  
 `AssemblyID`  
 Hedef derleme kimliği.  
  
 `FileToken`  
 Alınacağı dosya kimliği.  
  
 `dwScope`  
 İçeri aktarmak için sıfır tabanlı kapsam.  
  
 `ppImportScope`  
 İşaretçi alır [Imetadataımport2 arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md) Belirtilen kapsam için arabirim.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 ALink.h gerektirir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IALink2 Arabirimi](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [IALink Arabirimi](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [ALink API](../../../../docs/framework/unmanaged-api/alink/index.md)
