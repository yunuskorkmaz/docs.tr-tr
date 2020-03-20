---
title: IMetaDataEmit::DefineCustomAttribute Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineCustomAttribute
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineCustomAttribute
helpviewer_keywords:
- DefineCustomAttribute method [.NET Framework metadata]
- IMetaDataEmit::DefineCustomAttribute method [.NET Framework metadata]
ms.assetid: 7dd14854-b756-4401-b167-88ca576dc8f0
topic_type:
- apiref
ms.openlocfilehash: 9c4ed282e259aa46fc0cb0175214dc51d3d5fbee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175895"
---
# <a name="imetadataemitdefinecustomattribute-method"></a>IMetaDataEmit::DefineCustomAttribute Yöntemi
Belirtilen meta veri imzasıyla özel bir öznitelik için, belirtilen nesneye eklenecek bir tanım oluşturur ve bu özel öznitelik tanımına bir belirteç alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT DefineCustomAttribute (
    [in]  mdToken     tkObj,
    [in]  mdToken     tkType,
    [in]  void const  *pCustomAttribute,
    [in]  ULONG       cbCustomAttribute,
    [out] mdCustomAttribute *pcv
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `tkObj`  
 [içinde] Sahibi öğesinin belirteci.  
  
 `tkType`  
 [içinde] Özel özniteliği tanımlayan belirteç.  
  
 `pCustomAttribute`  
 [içinde] Özel öznitelik için bir işaretçi.  
  
 `cbCustomAttribute`  
 [içinde] Bayt `pCustomAttribute`sayısı.  
  
 `pcv`  
 [çıkış] Atanan `mdCustomAttribute` belirteç.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** Cor.h  
  
 **Kütüphane:** MSCorEE.dll'de kaynak olarak kullanılır  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
