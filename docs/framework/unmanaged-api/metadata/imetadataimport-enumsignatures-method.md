---
title: IMetaDataImport::EnumSignatures Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumSignatures
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumSignatures
helpviewer_keywords:
- EnumSignatures method [.NET Framework metadata]
- IMetaDataImport::EnumSignatures method [.NET Framework metadata]
ms.assetid: d0d65060-6f90-42a2-95cf-6ffb04352996
topic_type:
- apiref
ms.openlocfilehash: 652ebf1be6a58e08da27aaed5b2e84a8f2aee98a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503776"
---
# <a name="imetadataimportenumsignatures-method"></a>IMetaDataImport::EnumSignatures Yöntemi
Geçerli kapsamdaki tek başına imzaları temsil eden Imza belirteçlerini numaralandırır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT EnumSignatures (  
   [in, out] HCORENUM     *phEnum,  
   [out]     mdSignature  rSignatures[],  
   [in]      ULONG        cMax,  
   [out]     ULONG        *pcSignatures  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `phEnum`  
 [in, out] Numaralandırıcı için bir işaretçi. Bu yöntemin ilk çağrısı için bu NULL olmalıdır.  
  
 `rSignatures`  
 dışı Imza belirteçlerini depolamak için kullanılan dizi.  
  
 `cMax`  
 'ndaki Dizinin en büyük boyutu `rSignatures` .  
  
 `pcSignatures`  
 dışı İçinde döndürülen Imza belirteçleri sayısı `rSignatures` .  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Description|  
|-------------|-----------------|  
|`S_OK`|`EnumSignatures`başarıyla döndürüldü.|  
|`S_FALSE`|Numaralandırılacak belirteç yok. Bu durumda, `pcSignatures` sıfırdır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Imza belirteçleri [ımetadatayayma:: GetTokenFromSig](imetadataemit-gettokenfromsig-method.md) yöntemi tarafından oluşturulur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](imetadataimport2-interface.md)
