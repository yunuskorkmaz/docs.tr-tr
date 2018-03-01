---
title: IMetaDataImport::GetCustomAttributeByName Metodu
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7d234a58d95203a26e8b1cab2cb936e6ee50c2fa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgetcustomattributebyname-method"></a>IMetaDataImport::GetCustomAttributeByName Metodu
Özel öznitelik adı ve sahibi verilen alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetCustomAttributeByName (  
   [in]  mdToken          tkObj,  
   [in]  LPCWSTR          szName,  
   [out] const void       **ppData,  
   [out] ULONG            *pcbData  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `tkObj`  
 [in] Özel öznitelik sahibi nesnesini temsil eden bir meta veri simgesi.  
  
 `szName`  
 [in] Özel öznitelik adı.  
  
 `ppData`  
 [out] Bir özel öznitelik değeri veri dizisi için bir işaretçi.  
  
 `pcbData`  
 [out] Döndürülen verileri bayt cinsinden boyutu *`ppData`.  
  
## <a name="remarks"></a>Açıklamalar  
 Birden çok özel öznitelikleri için aynı sahibi tanımlamak için uygundur; bile aynı ada sahip. Ancak, `GetCustomAttributeByName` yalnızca bir örneğini döndürür. (`GetCustomAttributeByName` bulduğu ilk örneğini döndürür.) Özel bir öznitelik tüm örneklerini bulmak için arama [Imetadataımport::enumcustomattributes](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumcustomattributes-method.md) yöntemi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Cor.h  
  
 **Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
