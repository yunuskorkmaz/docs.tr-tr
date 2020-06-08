---
title: IMetaDataEmit2::SetGenericParamProps Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.SetGenericParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::SetGenericParamProps
helpviewer_keywords:
- IMetaDataEmit2::SetGenericParamProps method [.NET Framework metadata]
- SetGenericParamProps method [.NET Framework metadata]
ms.assetid: cd93a48d-1fed-4706-bec6-a05dc3b64fbd
topic_type:
- apiref
ms.openlocfilehash: 8feba8e67f3a90dd48fd957065a9c166c204b87c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492749"
---
# <a name="imetadataemit2setgenericparamprops-method"></a>IMetaDataEmit2::SetGenericParamProps Yöntemi
Belirtilen belirteç tarafından başvurulan genel parametre tanımının özellik değerlerini ayarlar.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT SetGenericParamProps (  
    [in] mdGenericParam   gp,
    [in] DWORD            dwParamFlags,
    [in] LPCWSTR          szName,
    [in] DWORD            reserved,
    [in] mdToken          rtkConstraints[]  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `gp`  
 'ndaki Değerleri ayarlanacak genel parametre tanımının belirteci.  
  
 `dwParamFlags`  
 'ndaki Genel parametrenin türünü açıklayan [CorGenericParamAttr](corgenericparamattr-enumeration.md) numaralandırması değeri.  
  
 `szName`  
 'ndaki Seçim. Değerlerinin ayarlanacağı parametrenin adı.  
  
 `reserved`  
 'ndaki Gelecekteki genişletilebilirlik için ayrılmıştır.  
  
 `rtkConstraints`  
 'ndaki Seçim. Tür kısıtlamaları sıfır ile sonlandırılmış dizi. Dizi üyeleri bir `mdTypeDef` , `mdTypeRef` veya `mdTypeSpec` meta veri belirteci olmalıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit2 Arabirimi](imetadataemit2-interface.md)
- [IMetaDataEmit Arabirimi](imetadataemit-interface.md)
