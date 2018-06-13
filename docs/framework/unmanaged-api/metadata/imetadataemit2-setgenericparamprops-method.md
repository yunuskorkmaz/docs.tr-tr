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
ms.openlocfilehash: 2d74ee7512f640ab906f1119f61e4998b5e882eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33445693"
---
# <a name="imetadataemit2setgenericparamprops-method"></a>IMetaDataEmit2::SetGenericParamProps Yöntemi
Belirtilen belirteç tarafından başvurulan genel parametresini tanımı için özellik değerlerini ayarlar.  
  
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
  
#### <a name="parameters"></a>Parametreler  
 `gp`  
 [in] Hangi değerlerini ayarlamak genel parametresini tanımı için belirteci.  
  
 `dwParamFlags`  
 [in] Değerini [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) türünü genel parametresi için açıklayan numaralandırması.  
  
 `szName`  
 [in] İsteğe bağlı. Değerleri ayarlanacak parametresinin adı.  
  
 `reserved`  
 [in] Gelecekteki genişletilebilirliği için ayrılmış.  
  
 `rtkConstraints`  
 [in] İsteğe bağlı. Tür kısıtlamaları sıfır sonlandırılan dizisi. Dizi üyeleri olmalıdır bir `mdTypeDef`, `mdTypeRef`, veya `mdTypeSpec` meta veri simgesi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Cor.h  
  
 **Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IMetaDataEmit2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 [IMetaDataEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
