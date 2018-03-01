---
title: IMetaDataImport::GetRVA Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataImport.GetRVA
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetRVA
helpviewer_keywords:
- GetRVA method [.NET Framework metadata]
- IMetaDataImport::GetRVA method [.NET Framework metadata]
ms.assetid: ea422217-988b-4acd-b2db-c55357938275
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6c055afaa129b52c67cd0463a5d44afec5cde103
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgetrva-method"></a>IMetaDataImport::GetRVA Metodu
Göreli sanal adres (RAV) ve yöntem veya belirtilen belirtecin tarafından temsil edilen alan uygulama bayraklarını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetRVA (  
   [in]  mdToken     tk,   
   [out] ULONG       *pulCodeRVA,   
   [out]  DWORD      *pdwImplFlags  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `tk`  
 [in] İçin RVA dönmek için kod nesnesini temsil eden bir MethodDef veya fieldDef simgesi meta veri simgesi. Belirtecin bir fieldDef simgesi ise, alan genel değişkeni olmalıdır.  
  
 `pulCodeRVA`  
 [out] Belirtecin tarafından temsil edilen kod nesne göreli sanal adresini gösteren bir işaretçi.  
  
 `pdwImplFlags`  
 [out] Uygulama bayrakları yöntemi için bir işaretçi. Bu değer gelen bir bit maskesi olan [Cormethodımpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) numaralandırması. Değeri `pdwImplFlags` geçerli yalnızca `tk` MethodDef belirteci.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Cor.h  
  
 **Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
