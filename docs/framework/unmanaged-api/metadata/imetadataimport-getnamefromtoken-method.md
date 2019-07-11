---
title: IMetaDataImport::GetNameFromToken Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetNameFromToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetNameFromToken
helpviewer_keywords:
- GetNameFromToken method [.NET Framework metadata]
- IMetaDataImport::GetNameFromToken method [.NET Framework metadata]
ms.assetid: 32114ecf-8916-4ab2-a201-179c017344f1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fa6e8665e5e2194eb4a3dffad8e97a69deb202d0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778981"
---
# <a name="imetadataimportgetnamefromtoken-method"></a>IMetaDataImport::GetNameFromToken Yöntemi
Belirtilen meta veri belirteci tarafından başvurulan nesne UTF-8 adını alır. Bu yöntem artık kullanılmıyor.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetNameFromToken (  
   [in] mdToken      tk,  
   [out] MDUTF8CSTR  *pszUtf8NamePtr  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `tk`  
 [in] Adı döndürülecek nesne temsil eden belirteç.  
  
 `pszUtf8NamePtr`  
 [out] Yığın UTF-8 nesnenin adına yönelik işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetNameFromToken` artık kullanılmıyor. Alternatif olarak, belirteç gereklidir, gibi belirli türünü özelliklerini almak için bir yöntemi çağırmak `GetFieldProps` bir alanın veya `GetMethodProps` için bir yöntem.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** COR.h  
  
 **Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:** 1.0  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
