---
title: IMetaDataImport::GetCustomAttributeProps Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetCustomAttributeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetCustomAttributeProps
helpviewer_keywords:
- GetCustomAttributeProps method [.NET Framework metadata]
- IMetaDataImport::GetCustomAttributeProps method [.NET Framework metadata]
ms.assetid: 6eefb243-a281-41c1-bcdc-7e17513bc446
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4619d5a1444d42c6f3ac43306fbd979a6a70f12b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54672181"
---
# <a name="imetadataimportgetcustomattributeprops-method"></a>IMetaDataImport::GetCustomAttributeProps Metodu
Kendi meta veri belirteci verilen özel özniteliğinin değerini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetCustomAttributeProps (  
   [in]            mdCustomAttribute   cv,  
   [out, optional] mdToken             *ptkObj,  
   [out, optional] mdToken             *ptkType,  
   [out, optional] void const          **ppBlob,  
   [out, optional] ULONG               *pcbSize  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `cv`  
 [in] Alınacak özel öznitelik temsil eden bir meta veri belirteci.  
  
 `ptkObj`  
 [out, isteğe bağlı] Özel öznitelik değiştiren nesnesini temsil eden bir meta veri belirteci. Bu değer, meta veri belirteci dışında herhangi bir türde olabilir `mdCustomAttribute`.  
  
 `ptkType`  
 [out, isteğe bağlı] Bir `mdMethodDef` veya `mdMemberRef` meta veri belirteci temsil eden <xref:System.Type> döndürülen özel özniteliğinin.  
  
 `ppBlob`  
 [out, isteğe bağlı] Özel öznitelik değeri olan verilerin bir dizisine bir işaretçi.  
  
 `pcbSize`  
 [out, isteğe bağlı] Döndürülen verileri baytlık boyutu *`ppBlob`.  
  
## <a name="remarks"></a>Açıklamalar  
 Özel bir öznitelik, bir veri, meta veri altyapısı tarafından anlaşılır biçimi dizisi olarak depolanır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** COR.h  
  
 **Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
