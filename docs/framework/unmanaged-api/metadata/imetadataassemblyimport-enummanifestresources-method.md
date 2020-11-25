---
title: IMetaDataAssemblyImport::EnumManifestResources Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.EnumManifestResources
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::EnumManifestResources
helpviewer_keywords:
- IMetaDataAssemblyImport::EnumManifestResources method [.NET Framework metadata]
- EnumManifestResources method [.NET Framework metadata]
ms.assetid: 9543b111-5705-40c9-935c-a3ffc7a581aa
topic_type:
- apiref
ms.openlocfilehash: c72e5b9544d1d8ae989405ac9bfdb22050b1aaaf
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731627"
---
# <a name="imetadataassemblyimportenummanifestresources-method"></a>IMetaDataAssemblyImport::EnumManifestResources Yöntemi

Geçerli derleme bildiriminde başvurulan kaynaklar için bir Numaralandırıcı işaretçisi alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT EnumManifestResources (  
    [in, out] HCORENUM         *phEnum,
    [out] mdManifestResource   rManifestResources[],
    [in]  ULONG                cMax,
    [out] ULONG                *pcTokens  
);
```  
  
## <a name="parameters"></a>Parametreler  

 `phEnum`  
 [in, out] Numaralandırıcı için bir işaretçi. Yöntem ilk kez çağrıldığında bu null bir değer olmalıdır `EnumManifestResources` .  
  
 `rManifestResources`  
 dışı Meta veri belirteçlerini depolamak için kullanılan dizi `mdManifestResource` .  
  
 `cMax`  
 'ndaki `mdManifestResource` İçine yerleştirilebilecek en fazla belirteç sayısı `rManifestResources` .  
  
 `pcTokens`  
 dışı `mdManifestResource` Gerçekte içine yerleştirilmiş olan belirteçlerin sayısı `rManifestResources` .  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|`S_OK`|`EnumManifestResources` başarıyla döndürüldü.|  
|`S_FALSE`|Numaralandırılacak belirteç yok. Bu durumda, `pcTokens` sıfır olarak ayarlanır.|  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE.dll kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataAssemblyImport Arabirimi](imetadataassemblyimport-interface.md)
