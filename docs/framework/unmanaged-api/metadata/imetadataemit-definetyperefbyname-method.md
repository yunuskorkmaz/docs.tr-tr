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
ms.openlocfilehash: 23a6931b31ea2d7e4e8d1cb3dc8adf3a51216315
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175752"
---
# <a name="imetadataemitdefinetyperefbyname-method"></a>IMetaDataEmit::DefineTypeRefByName Yöntemi
Geçerli kapsam dışında, belirtilen kapsamda tanımlanan bir tür için bir meta veri belirteci alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT DefineTypeRefByName (
    [in]  mdToken     tkResolutionScope,
    [in]  LPCWSTR     szName,
    [out] mdTypeRef   *ptr
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `tkResolutionScope`  
 [içinde] Çözüm kapsamını belirten belirteç. Aşağıdaki belirteç türleri geçerlidir:  
  
- `mdModuleRef`, tür, arayanın tanımlandığı aynı derlemede tanımlanırsa.  
  
- `mdAssemblyRef`, tür, arayanın tanımlandığı derleme den başka bir derlemede tanımlanmışsa.  
  
- `mdTypeRef`, tür iç içe bir tür ise.  
  
- `mdModule`, tür, arayanın tanımlandığı aynı modülde tanımlanmışsa.  
  
- Null, tür genel olarak tanımlanırsa.  
  
 `szName`  
 [içinde] Unicode'da hedef türün adı.  
  
 `ptr`  
 [çıkış] Türe `mdTypeRef` atanan belirteç için bir işaretçi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** Cor.h  
  
 **Kütüphane:** MSCorEE.dll'de kaynak olarak kullanılır  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
