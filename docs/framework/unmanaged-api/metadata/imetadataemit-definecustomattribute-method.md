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
ms.openlocfilehash: 17757df566ba8d141e7adec00dcc1f75959d0e00
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84005635"
---
# <a name="imetadataemitdefinecustomattribute-method"></a>IMetaDataEmit::DefineCustomAttribute Yöntemi
Belirtilen nesneye iliştirililmesi için belirtilen meta veri imzasına sahip özel bir öznitelik için bir tanım oluşturur ve bu özel öznitelik tanımına bir belirteç alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
 'ndaki Sahip öğesi için belirteç.  
  
 `tkType`  
 'ndaki Özel özniteliği tanımlayan belirteç.  
  
 `pCustomAttribute`  
 'ndaki Özel özniteliğe yönelik bir işaretçi.  
  
 `cbCustomAttribute`  
 'ndaki İçindeki bayt sayısı `pCustomAttribute` .  
  
 `pcv`  
 dışı `mdCustomAttribute`Atanan belirteç.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MSCorEE. dll içinde kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit Arabirimi](imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](imetadataemit2-interface.md)
