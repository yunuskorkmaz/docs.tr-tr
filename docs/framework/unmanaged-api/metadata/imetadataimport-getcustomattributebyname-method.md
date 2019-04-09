---
title: IMetaDataImport::GetCustomAttributeByName Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetCustomAttributeByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetCustomAttributeByName
helpviewer_keywords:
- IMetaDataImport::GetCustomAttributeByName method [.NET Framework metadata]
- GetCustomAttributeByName method [.NET Framework metadata]
ms.assetid: 909aa530-2e3b-4d0a-a38a-a2750e535d7d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 61029074347d554faaefe790c1e408e860e34690
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59183033"
---
# <a name="imetadataimportgetcustomattributebyname-method"></a>IMetaDataImport::GetCustomAttributeByName Yöntemi
Özel öznitelik adını ve sahibini verilen alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetCustomAttributeByName (  
   [in]  mdToken          tkObj,  
   [in]  LPCWSTR          szName,  
   [out] const void       **ppData,  
   [out] ULONG            *pcbData  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `tkObj`  
 [in] Özel öznitelik sahip nesnesini temsil eden bir meta veri belirteci.  
  
 `szName`  
 [in] Özel öznitelik adı.  
  
 `ppData`  
 [out] Özel öznitelik değeri olan verilerin bir dizisine bir işaretçi.  
  
 `pcbData`  
 [out] Döndürülen verileri baytlık boyutu *`ppData`.  
  
## <a name="remarks"></a>Açıklamalar  
 Birden çok özel öznitelikler için aynı sahibi tanımlamak için geçerlidir; hatta aynı ada sahip olabilir. Ancak, `GetCustomAttributeByName` yalnızca bir örneğini döndürür. (`GetCustomAttributeByName` bulduğu ilk örneği döndürür.) Tüm özel öznitelik örneklerini bulmak için arama [Imetadataımport::enumcustomattributes](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumcustomattributes-method.md) yöntemi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** COR.h  
  
 **Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
