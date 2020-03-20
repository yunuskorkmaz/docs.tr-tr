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
ms.openlocfilehash: 218b65b5899692774c434ae136a3976ecb97ea2f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177302"
---
# <a name="imetadataimportenummethods-method"></a>IMetaDataImport::EnumMethods Yöntemi
Belirtilen tipteki yöntemleri temsil eden MethodDef belirteçlerini oyalar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT EnumMethods (  
   [in, out] HCORENUM   *phEnum,
   [in]  mdTypeDef      cl,
   [out] mdMethodDef    rMethods[],
   [in]  ULONG          cMax,
   [out] ULONG          *pcTokens  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `phEnum`  
 [içinde, dışarı] Sayıya işaretçisi. Bu yöntemin ilk araması için NULL olmalıdır.  
  
 `cl`  
 [içinde] Türü temsil eden ve sayısallama yöntemlerini temsil eden bir TypeDef belirteci.  
  
 `rMethods`  
 [çıkış] MethodDef belirteçlerini depolamak için dizi.  
  
 `cMax`  
 [içinde] MethodDef `rMethods` dizisinin en büyük boyutu.  
  
 `pcTokens`  
 [çıkış] MethodDef belirteçlerinin sayısı `rMethods`.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|`S_OK`|`EnumMethods`başarıyla döndürülür.|  
|`S_FALSE`|Sayısala çıkarmak için MethodDef belirteçleri yoktur. Bu durumda, `pcTokens` sıfırdır.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** Cor.h  
  
 **Kütüphane:** MsCorEE.dll bir kaynak olarak dahil  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
