---
title: IMetaDataImport::EnumMethodImpls Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMethodImpls
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMethodImpls
helpviewer_keywords:
- EnumMethodImpls method [.NET Framework metadata]
- IMetaDataImport::EnumMethodImpls method [.NET Framework metadata]
ms.assetid: 4e0f865d-88b5-44bd-be35-492622e5e08e
topic_type:
- apiref
ms.openlocfilehash: e766cec8fd84713e12c43cd1095650ed5b757bcb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175479"
---
# <a name="imetadataimportenummethodimpls-method"></a>IMetaDataImport::EnumMethodImpls Yöntemi
Belirtilen tipteki yöntemleri temsil eden MethodBody ve MethodDeclaration belirteçlerini okurum.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT EnumMethodImpls (  
   [in, out] HCORENUM    *phEnum,
   [in]      mdTypeDef   td,
   [out]     mdToken     rMethodBody[],
   [out]     mdToken     rMethodDecl[],
   [in]      ULONG       cMax,
   [in]      ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `phEnum`  
 [içinde, dışarı] Sayıya işaretçisi. Bu yöntemin ilk araması için NULL olmalıdır.  
  
 `td`  
 [içinde] Yöntem uygulamaları numaralandırmak için türü için bir TypeDef belirteci.  
  
 `rMethodBody`  
 [çıkış] MethodBody belirteçlerini depolamak için dizi.  
  
 `rMethodDecl`  
 [çıkış] MethodDeclaration belirteçlerini depolayabilmek için dizi.  
  
 `cMax`  
 [içinde] Ve `rMethodBody` `rMethodDecl` dizilerin maksimum boyutu.  
  
 `pcTokens`  
 [içinde] Döndürülen yöntemlerin gerçek `rMethodBody` `rMethodDecl`sayısı ve .  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|`S_OK`|`EnumMethodImpls`başarıyla döndürülür.|  
|`S_FALSE`|Sayısala maksat için herhangi bir yöntem belirteçleri vardır. Bu durumda, `pcTokens` sıfırdır.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** Cor.h  
  
 **Kütüphane:** MsCorEE.dll bir kaynak olarak dahil  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
