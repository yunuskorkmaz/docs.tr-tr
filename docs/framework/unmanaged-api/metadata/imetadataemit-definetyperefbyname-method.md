---
title: IMetaDataEmit::DefineTypeRefByName Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineTypeRefByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineTypeRefByName
helpviewer_keywords:
- DefineTypeRefByName method [.NET Framework metadata]
- IMetaDataEmit::DefineTypeRefByName method [.NET Framework metadata]
ms.assetid: c30a4ce3-2d3e-411a-98df-e62ac4a5dd50
topic_type:
- apiref
ms.openlocfilehash: b83c868f1a804d4e6f32adffc190ae086aa5e0a0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719345"
---
# <a name="imetadataemitdefinetyperefbyname-method"></a>IMetaDataEmit::DefineTypeRefByName Yöntemi

Geçerli kapsamın dışında belirtilen kapsamda tanımlı bir tür için meta veri belirteci alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT DefineTypeRefByName (
    [in]  mdToken     tkResolutionScope,
    [in]  LPCWSTR     szName,
    [out] mdTypeRef   *ptr
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `tkResolutionScope`  
 'ndaki Çözümleme kapsamını belirten belirteç. Aşağıdaki belirteç türleri geçerlidir:  
  
- `mdModuleRef`, türü çağıranın tanımlandığı derlemede tanımlanmışsa.  
  
- `mdAssemblyRef`tür, çağıranın tanımlandığı bir derlemede tanımlıysa.  
  
- `mdTypeRef`türü, iç içe bir tür ise.  
  
- `mdModule`, türü çağıranın tanımlandığı modülde tanımlanmışsa.  
  
- Tür genel olarak tanımlanmışsa null.  
  
 `szName`  
 'ndaki Unicode 'daki hedef türünün adı.  
  
 `ptr`  
 dışı `mdTypeRef` Türe atanmış belirtece yönelik bir işaretçi.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MSCorEE.dll kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit Arabirimi](imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](imetadataemit2-interface.md)
