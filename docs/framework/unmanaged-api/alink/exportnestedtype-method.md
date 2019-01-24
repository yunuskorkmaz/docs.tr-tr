---
title: ExportNestedType Metodu
ms.date: 03/30/2017
api_name:
- IALink.ExportNestedType
- ExportNestedType
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ExportNestedType
helpviewer_keywords:
- ExportNestedType method
ms.assetid: dec7df60-4d30-47c8-99db-72e0419e5f76
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5c7ea671af5c6c725df136810bb8cf6610a6f83f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54710345"
---
# <a name="exportnestedtype-method"></a>ExportNestedType Metodu
İç içe geçmiş türler dışarı aktarılabilir olarak belirtir. [ExportType yöntemi](../../../../docs/framework/unmanaged-api/alink/exporttype-method.md) dışarı aktarma iç içe geçmiş türleri de kullanabilirsiniz, ancak bu daha hızlı bir yöntemdir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT ExportNestedType(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    mdTypeDef       TypeToken,  
    mdExportedType  ParentType,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;   
```  
  
#### <a name="parameters"></a>Parametreler  
 `AssemblyID`  
 Dışarı aktarmak için derleme kimliği.  
  
 `FileToken`  
 Dosya belirteci veya derleme dosyasının dışarı aktarılabilir hale türünü tanımlar.  
  
 `TypeToken`  
 Dışarı aktarılabilir hale türünde belirteç türü.  
  
 `ParentType`  
 Üst tür belirteci.  
  
 `pszTypename`  
 Dışarı aktarmak için tam nitelikli tür adı.  
  
 `dwFlags`  
 `ComType` gibi bayrakları `tdPublic` veya `tdNested`. Bu değer için geçirilebilir [DefineExportedType yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).  
  
 `pType`  
 Dışarı aktarılan tür için belirteci alır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 ALink.h gerektirir  
  
## <a name="see-also"></a>Ayrıca bkz.
- [IALink Arabirimi](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [IALink2 Arabirimi](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [ALink API](../../../../docs/framework/unmanaged-api/alink/index.md)
