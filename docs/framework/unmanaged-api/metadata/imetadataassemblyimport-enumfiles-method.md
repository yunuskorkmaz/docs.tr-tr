---
title: IMetaDataAssemblyImport::EnumFiles Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.EnumFiles
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::EnumFiles
helpviewer_keywords:
- IMetaDataAssemblyImport::EnumFiles method [.NET Framework metadata]
- EnumFiles method [.NET Framework metadata]
ms.assetid: f0d721e2-b946-426d-8e20-9124bd04e4cb
topic_type:
- apiref
ms.openlocfilehash: 70f76318f51047cb81262f744a6fbed5fe401692
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177811"
---
# <a name="imetadataassemblyimportenumfiles-method"></a>IMetaDataAssemblyImport::EnumFiles Yöntemi
Geçerli derleme bildiriminde başvurulan dosyaları güncelleştirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT EnumFiles (  
    [in, out] HCORENUM    *phEnum,
    [out] mdFile          rFiles[],
    [in]  ULONG           cMax,
    [out] ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `phEnum`  
 [içinde, dışarı] Sayıya işaretçisi. Bu yöntemin ilk araması için null bir değer olmalıdır.  
  
 `rFiles`  
 [çıkış] `mdFile` Meta veri belirteçlerini depolamak için kullanılan dizi.  
  
 `cMax`  
 [içinde] Yerleştirilebilen `mdFile` en fazla belirteç `rFiles`sayısı.  
  
 `pcTokens`  
 [çıkış] Yerleştirilen belirteçlerin `mdFile` `rFiles`sayısı.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|`S_OK`|`EnumFiles`başarıyla döndürülür.|  
|`S_FALSE`|Sayısala rendelemek için hiçbir belirteçleri vardır. Bu durumda, `pcTokens` sıfıra ayarlanır.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** Cor.h  
  
 **Kütüphane:** MsCorEE.dll'de kaynak olarak kullanılır  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataAssemblyImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
