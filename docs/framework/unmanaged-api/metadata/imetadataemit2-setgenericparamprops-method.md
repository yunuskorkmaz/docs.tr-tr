---
title: IMetaDataEmit2::SetGenericParamProps Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.SetGenericParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::SetGenericParamProps
helpviewer_keywords:
- IMetaDataEmit2::SetGenericParamProps method [.NET Framework metadata]
- SetGenericParamProps method [.NET Framework metadata]
ms.assetid: cd93a48d-1fed-4706-bec6-a05dc3b64fbd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4daf24c1712b18d933da702e9e1ef1cbdbfc3639
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59081911"
---
# <a name="imetadataemit2setgenericparamprops-method"></a>IMetaDataEmit2::SetGenericParamProps Yöntemi
Belirtilen belirteç tarafından başvurulan genel parametre tanımı için özellik değerlerini ayarlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT SetGenericParamProps (  
    [in] mdGenericParam   gp,   
    [in] DWORD            dwParamFlags,   
    [in] LPCWSTR          szName,   
    [in] DWORD            reserved,   
    [in] mdToken          rtkConstraints[]  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `gp`  
 [in] Genel parametre tanımı için olan değerleri ayarlamak belirteç.  
  
 `dwParamFlags`  
 [in] Değerini [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) türünü genel parametresi için açıklayan sabit listesi.  
  
 `szName`  
 [in] İsteğe bağlı. Değerleri ayarlamak istediğiniz parametrenin adı.  
  
 `reserved`  
 [in] Sonra genişletilebilmek için ayrılmış.  
  
 `rtkConstraints`  
 [in] İsteğe bağlı. Tür kısıtlamaları Sıfırla sonlandırılmış dizisi. Dizi üyeleri olmalıdır bir `mdTypeDef`, `mdTypeRef`, veya `mdTypeSpec` meta veri belirteci.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** COR.h  
  
 **Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [IMetaDataEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
