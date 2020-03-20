---
title: IMetaDataImport::EnumMembersWithName Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMembersWithName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMembersWithName
helpviewer_keywords:
- IMetaDataImport::EnumMembersWithName method [.NET Framework metadata]
- EnumMembersWithName method [.NET Framework metadata]
ms.assetid: 7c9e9120-3104-42f0-86ce-19a025f20dcc
topic_type:
- apiref
ms.openlocfilehash: 7410f91a853f3a677a105dc2e12a86d723c9fad6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177313"
---
# <a name="imetadataimportenummemberswithname-method"></a>IMetaDataImport::EnumMembersWithName Yöntemi
Belirtilen türdeki üyeleri temsil eden ÜyeDef belirteçlerini belirtilen adla oyalar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT EnumMembersWithName (  
   [in, out] HCORENUM    *phEnum,
   [in]      mdTypeDef   cl,
   [in]      LPCWSTR     szName,
   [out]     mdToken     rMembers[],
   [in]      ULONG       cMax,
   [out]     ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `phEnum`  
 [içinde, dışarı] Sayıya işaretçisi.  
  
 `cl`  
 [içinde] Üyelerini sayısala dizecek türü temsil eden bir TypeDef belirteci.  
  
 `szName`  
 [içinde] Üyenin kapsamını sınırlayan üye adı.  
  
 `rMembers`  
 [çıkış] ÜyeDef belirteçlerini depolamak için kullanılan dizi.  
  
 `cMax`  
 [içinde] `rMembers` Dizinin en büyük boyutu.  
  
 `pcTokens`  
 [çıkış] ÜyeDef belirteçlerinin gerçek sayısı `rMembers`.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem alanları ve yöntemleri, ancak özellikleri veya olayları sayısallar. [IMetaDataImport aksine::EnumMembers,](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummembers-method.md) `EnumMembersWithName` belirtilen adı olmayan tüm alan ve üye belirteçleri atar.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|`S_OK`|`EnumTypeDefs`başarıyla döndürülür.|  
|`S_FALSE`|Sayısala kaydolacak ÜyeDef belirteçleri yoktur. Bu durumda, `pcTokens` sıfırdır.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** Cor.h  
  
 **Kütüphane:** MsCorEE.dll bir kaynak olarak dahil  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
