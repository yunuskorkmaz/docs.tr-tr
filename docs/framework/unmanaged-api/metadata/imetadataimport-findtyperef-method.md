---
title: IMetaDataImport::FindTypeRef Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindTypeRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindTypeRef
helpviewer_keywords:
- IMetaDataImport::FindTypeRef method [.NET Framework metadata]
- FindTypeRef method [.NET Framework metadata]
ms.assetid: 1b2bbf3f-943e-412e-b66c-e802431b055c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8159b5245598993a2075fb402b280f9ab4cb2cfa
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782468"
---
# <a name="imetadataimportfindtyperef-method"></a>IMetaDataImport::FindTypeRef Yöntemi
Bir işaretçi için TypeRef belirteci alır <xref:System.Type> Belirtilen kapsam içinde olan ve belirtilen ada sahip bir başvuru.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT FindTypeRef (  
   [in] mdToken        tkResolutionScope,  
   [in]  LPCWSTR       szName,  
   [out] mdTypeRef     *ptr  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `tkResolutionScope`  
 [in] Modül, derleme veya türünü belirten bir ModuleRef, AssemblyRef veya TypeRef belirteci sırasıyla, hangi tür başvurusu tanımlanır.  
  
 `szName`  
 [in] Aramak için türü başvuru adı.  
  
 `ptr`  
 [out] Eşleşen TypeRef belirteci için bir işaretçi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** COR.h  
  
 **Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
