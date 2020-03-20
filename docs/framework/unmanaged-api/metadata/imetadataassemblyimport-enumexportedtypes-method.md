---
title: IMetaDataAssemblyImport::EnumExportedTypes Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.EnumExportedTypes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::EnumExportedTypes
helpviewer_keywords:
- EnumExportedTypes method [.NET Framework metadata]
- IMetaDataAssemblyImport::EnumExportedTypes method [.NET Framework metadata]
ms.assetid: e5912ed8-e4ce-438b-8ea3-d9e4c288d109
topic_type:
- apiref
ms.openlocfilehash: f00fe5bce2f808265add228406dfaa2ccc267545
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176012"
---
# <a name="imetadataassemblyimportenumexportedtypes-method"></a>IMetaDataAssemblyImport::EnumExportedTypes Yöntemi
Derleme bildiriminde başvurulan dışa aktarılan türleri geçerli meta veri kapsamında günceller.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT EnumExportedTypes (  
    [in, out] HCORENUM     *phEnum,
    [out] mdExportedType   rExportedTypes[],
    [in]  ULONG            cMax,
    [out] ULONG            *pcTokens  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `phEnum`  
 [içinde, dışarı] Sayıya işaretçisi. `EnumExportedTypes` Yöntem ilk kez çağrıldığında bu null bir değer olmalıdır.  
  
 `rExportedTypes`  
 [çıkış] `mdExportedType` Meta veri belirteçlerinin numaralandırması.  
  
 `cMax`  
 [içinde] `rExportedTypes` Diziye yerleştirilebilir `mdExportedType` belirteçleri maksimum sayısı.  
  
 `pcTokens`  
 [çıkış] Yerleştirilen belirteçlerin `mdExportedType` `rExportedTypes`sayısı.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|`S_OK`|`EnumExportedTypes`başarıyla döndürülür.|  
|`S_FALSE`|Sayısala rendelemek için hiçbir belirteçleri vardır. Bu durumda, `pcTokens` sıfıra ayarlanır.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** Cor.h  
  
 **Kütüphane:** MsCorEE.dll'de kaynak olarak kullanılır  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataAssemblyImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
