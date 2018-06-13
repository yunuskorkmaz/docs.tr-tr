---
title: IMetaDataImport::EnumMethods Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMethods
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMethods
helpviewer_keywords:
- IMetaDataImport::EnumMethods method [.NET Framework metadata]
- EnumMethods method [.NET Framework metadata]
ms.assetid: 8cc3b0c3-d97d-4f71-9e7d-ef2a92b4959a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 933694a6a033dbfe817e3848b9008f05b86f51f3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33449018"
---
# <a name="imetadataimportenummethods-method"></a>IMetaDataImport::EnumMethods Yöntemi
Belirtilen türdeki yöntemleri temsil eden MethodDef belirteçleri numaralandırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT EnumMethods (  
   [in, out] HCORENUM   *phEnum,   
   [in]  mdTypeDef      cl,   
   [out] mdMethodDef    rMethods[],   
   [in]  ULONG          cMax,   
   [out] ULONG          *pcTokens  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `phEnum`  
 [içinde out] Numaralayıcı gösteren bir işaretçi. Bu, bu yöntem ilk çağrısı için NULL olmalıdır.  
  
 `cl`  
 [in] Numaralandırılacak yöntemleriyle türünü temsil eden bir TypeDef simgesi.  
  
 `rMethods`  
 [out] MethodDef belirteçleri depolama dizisi.  
  
 `cMax`  
 [in] En büyük boyutunu MethodDef `rMethods` dizi.  
  
 `pcTokens`  
 [out] Döndürülen MethodDef belirteçleri sayısı `rMethods`.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|`S_OK`|`EnumMethods` başarıyla döndürüldü.|  
|`S_FALSE`|Numaralandırılacak hiçbir MethodDef belirteçleri vardır. Bu durumda, `pcTokens` sıfırdır.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Cor.h  
  
 **Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
