---
title: IMetaDataImport::GetCustomAttributeByName Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetCustomAttributeByName
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetCustomAttributeByName
helpviewer_keywords:
- IMetaDataImport::GetCustomAttributeByName method [.NET Framework metadata]
- GetCustomAttributeByName method [.NET Framework metadata]
ms.assetid: 909aa530-2e3b-4d0a-a38a-a2750e535d7d
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5b689c54b5e8d741d32bc941b4e78e6674f15e01
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
 [Imetadataımport arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [Imetadataımport2 arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
