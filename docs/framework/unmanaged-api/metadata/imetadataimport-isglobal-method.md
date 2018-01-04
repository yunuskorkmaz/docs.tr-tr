---
title: "IMetaDataImport::IsGlobal Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.IsGlobal
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::IsGlobal
helpviewer_keywords:
- IsGlobal method [.NET Framework metadata]
- IMetaDataImport::IsGlobal method [.NET Framework metadata]
ms.assetid: 44cf6908-f555-4ae8-b2cf-24bd974bf2fe
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c23010f7175b63f140ec1367e90e145b18ae6f9c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportisglobal-method"></a>IMetaDataImport::IsGlobal Yöntemi
Alan, yöntemi veya türü tarafından belirtilen meta veri simgesi gösterilir genel kapsama sahip olup olmadığını belirten bir değer alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT IsGlobal (  
   [in]  mdToken     pd,  
   [out] int         *pbGlobal  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pd`  
 [in] Türü, alan veya yöntem temsil eden bir meta veri belirteci.  
  
 `pbGlobal`  
 [out] 1 IF nesne genel kapsama sahip; Aksi takdirde, 0 (sıfır).  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Cor.h  
  
 **Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
