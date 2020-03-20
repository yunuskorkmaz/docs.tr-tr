---
title: IMetaDataImport::EnumPermissionSets Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumPermissionSets
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumPermissionSets
helpviewer_keywords:
- EnumPermissionSets method [.NET Framework metadata]
- IMetaDataImport::EnumPermissionSets method [.NET Framework metadata]
ms.assetid: 347d7e5c-c90f-45ad-bd1e-2c7912b0b19c
topic_type:
- apiref
ms.openlocfilehash: e628cf5dab8006b0df0ab6c60dc995cd0c6bb29d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175453"
---
# <a name="imetadataimportenumpermissionsets-method"></a>IMetaDataImport::EnumPermissionSets Yöntemi
Belirli bir meta veri kapsamındaki nesnelerin izinlerini oyalar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT EnumPermissionSets  
   [in, out] HCORENUM      *phEnum,
   [in]      mdToken       tk,
   [in]      DWORD         dwActions,  
   [out]     mdPermission  rPermission[],  
   [in]      ULONG         cMax,  
   [out]     ULONG         *pcTokens  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `phEnum`  
 [içinde, dışarı] Sayıya işaretçisi. Bu yöntemin ilk araması için NULL olmalıdır.  
  
 `tk`  
 [içinde] Aramanın kapsamını sınırlayan bir meta veri belirteci veya mümkün olan en geniş kapsamı aramak için NULL.  
  
 `dwActions`  
 [içinde] Tüm eylemleri <xref:System.Security.Permissions.SecurityAction> döndürmek için `rPermission`dahil olacak değerleri veya sıfırı temsil eden bayraklar.  
  
 `rPermission`  
 [çıkış] İzin belirteçlerini depolamak için kullanılan dizi.  
  
 `cMax`  
 [içinde] `rPermission` Dizinin en büyük boyutu.  
  
 `pcTokens`  
 [çıkış] Döndürülen İzin belirteçlerinin `rPermission`sayısı.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|`S_OK`|`EnumPermissionSets`başarıyla döndürülür.|  
|`S_FALSE`|Sayısala rendelemek için hiçbir belirteçleri vardır. Bu durumda, `pcTokens` sıfırdır.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** Cor.h  
  
 **Kütüphane:** MsCorEE.dll bir kaynak olarak dahil  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
