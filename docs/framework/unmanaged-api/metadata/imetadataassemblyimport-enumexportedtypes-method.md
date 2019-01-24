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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1beb76012d5f0351ee644c8dea89cabdbe2c8970
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54555030"
---
# <a name="imetadataassemblyimportenumexportedtypes-method"></a>IMetaDataAssemblyImport::EnumExportedTypes Yöntemi
Başvurulan derleme bildiriminde geçerli meta veri kapsamda dışarı aktarılan türlerini numaralandırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT EnumExportedTypes (  
    [in, out] HCORENUM     *phEnum,   
    [out] mdExportedType   rExportedTypes[],   
    [in]  ULONG            cMax,   
    [out] ULONG            *pcTokens  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `phEnum`  
 [out içinde] Numaralandırıcı bir işaretçi. Bu boş olmalıdır ne zaman değer `EnumExportedTypes` yöntemi ilk kez çağrılır.  
  
 `rExportedTypes`  
 [out] Numaralandırmasını `mdExportedType` meta veri belirteçleri.  
  
 `cMax`  
 [in] En fazla `mdExportedType` yerleştirilebilir belirteçleri `rExportedTypes` dizisi.  
  
 `pcTokens`  
 [out] Sayısını `mdExportedType` belirteçleri gerçekten yerleştirilen `rExportedTypes`.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|`S_OK`|`EnumExportedTypes` başarıyla döndürüldü.|  
|`S_FALSE`|Numaralandırılacak hiçbir belirteçleri vardır. Bu durumda, `pcTokens` sıfır olarak ayarlanır.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** COR.h  
  
 **Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [IMetaDataAssemblyImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
