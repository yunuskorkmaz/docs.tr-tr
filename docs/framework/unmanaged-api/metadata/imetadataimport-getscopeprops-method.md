---
title: IMetaDataImport::GetScopeProps Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetScopeProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetScopeProps
helpviewer_keywords:
- IMetaDataImport::GetScopeProps method [.NET Framework metadata]
- GetScopeProps method [.NET Framework metadata]
ms.assetid: c8ba42d2-d9fa-43cb-bbc0-f33e1e592cb6
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5b0936a9f47e2d0fa52816b78a7eecf3d244d594
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportgetscopeprops-method"></a>IMetaDataImport::GetScopeProps Metodu
Ad ve isteğe bağlı olarak derleme veya modülü sürüm tanıtıcısı geçerli meta veri kapsamdaki alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetScopeProps (  
   [out] LPWSTR           szName,  
   [in]  ULONG            cchName,  
   [out] ULONG            *pchName,  
   [out, optional] GUID   *pmvid  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `szName`  
 [out] Bütünleştirilmiş kod veya modül adı için bir arabellek.  
  
 `cchName`  
 [in] Geniş karakter cinsinden boyutu `szName`.  
  
 `pchName`  
 [out] Döndürülen geniş karakter sayısını `szName`.  
  
 `pmvid`  
 [out, isteğe bağlı] Derleme veya Modül sürümü benzersiz olarak tanımlayan bir GUID için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 [Imetadataemit::setmoduleprops](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md) yöntemi bu özellikleri ayarlamak için kullanılır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Cor.h  
  
 **Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Imetadataımport arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [Imetadataımport2 arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
