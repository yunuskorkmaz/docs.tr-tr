---
title: IMetaDataImport::GetNameFromToken Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetNameFromToken
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetNameFromToken
helpviewer_keywords:
- GetNameFromToken method [.NET Framework metadata]
- IMetaDataImport::GetNameFromToken method [.NET Framework metadata]
ms.assetid: 32114ecf-8916-4ab2-a201-179c017344f1
topic_type: apiref
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e77954d5730417a005c6c1ac07fa171bd0f1b13a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportgetnamefromtoken-method"></a>IMetaDataImport::GetNameFromToken Metodu
Belirtilen meta veri simgesi tarafından başvurulan nesne UTF-8 adını alır. Bu yöntem artık kullanılmıyor.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetNameFromToken (  
   [in] mdToken      tk,  
   [out] MDUTF8CSTR  *pszUtf8NamePtr  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `tk`  
 [in] Adını döndürmek için nesneyi gösteren belirteci.  
  
 `pszUtf8NamePtr`  
 [out] Bir işaretçi yığınındaki UTF-8 nesne adı.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetNameFromToken`Kullanımdan kalktı. Alternatif olarak, belirtecin gerekli, gibi belirli türü özelliklerini almak için bir yöntem çağrısı `GetFieldProps` bir alan için veya `GetMethodProps` bir yöntem için.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Cor.h  
  
 **Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:** 1.0  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Imetadataımport arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [Imetadataımport2 arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
