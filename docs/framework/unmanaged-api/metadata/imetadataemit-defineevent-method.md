---
title: IMetaDataEmit::DefineEvent Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineEvent
helpviewer_keywords:
- IMetaDataEmit::DefineEvent method [.NET Framework metadata]
- DefineEvent method [.NET Framework metadata]
ms.assetid: cf064bac-9a9f-41c5-9e1d-108ff7af3afe
topic_type:
- apiref
ms.openlocfilehash: a9598be850604f16ee8cc62187e1fed7ecf3a7e4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175856"
---
# <a name="imetadataemitdefineevent-method"></a>IMetaDataEmit::DefineEvent Yöntemi
Belirtilen meta veri imzasına sahip bir olay için tanım oluşturur ve bu olay tanımına bir belirteç alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT DefineEvent (
    [in]  mdTypeDef    td,
    [in]  LPCWSTR      szEvent,
    [in]  DWORD        dwEventFlags,
    [in]  mdToken      tkEventType,
    [in]  mdMethodDef  mdAddOn,
    [in]  mdMethodDef  mdRemoveOn,
    [in]  mdMethodDef  mdFire,
    [in]  mdMethodDef  rmdOtherMethods[],
    [out] mdEvent      *pmdEvent
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `td`  
 [içinde] Hedef sınıf veya arabirim için belirteç. Bu ya `mdTypeDef` bir `mdTypeDefNil` ya da bir belirteç.  
  
 `szEvent`  
 [içinde] Olayın adı.  
  
 `dwEventFlags`  
 [içinde] Olay bayrakları.  
  
 `tkEventType`  
 [içinde] Olay sınıfının belirteci. Bu bir `mdTypeDef`, `mdTypeRef`a `mdTokenNil` , ya da bir belirteç.  
  
 `mdAddOn`  
 [içinde] Olaya abone olmak için kullanılan yöntem veya null.  
  
 `mdRemoveOn`  
 [içinde] Olaya aboneliğini iptal etmek veya geçersiz kılmak için kullanılan yöntem.  
  
 `mdFire`  
 [içinde] Olayı yükseltmek için (türetilmiş bir sınıf tarafından) kullanılan yöntem.  
  
 `rmdOtherMethods[]`  
 [içinde] Olayla ilişkili diğer yöntemler için bir dizi belirteç. Dizi bir `mdMethodDefNil` belirteç ile sonlandırılır.  
  
 `pmdEvent`  
 [çıkış] Olaya atanan meta veri belirteci.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** Cor.h  
  
 **Kütüphane:** MSCorEE.dll'de kaynak olarak kullanılır  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
