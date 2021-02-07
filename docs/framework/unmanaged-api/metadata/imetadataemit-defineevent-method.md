---
description: 'Şu konuda daha fazla bilgi edinin: ımetadatayayma::D efineEvent yöntemi'
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
ms.openlocfilehash: f96f3a5b2ed16ba83223312af82cac7688cebfa0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753477"
---
# <a name="imetadataemitdefineevent-method"></a>IMetaDataEmit::DefineEvent Yöntemi

Belirtilen meta veri imzasıyla bir olay tanımı oluşturur ve bu olay tanımına bir belirteç alır.  
  
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
 'ndaki Hedef sınıf veya arabirim için belirteç. Bu bir ya da `mdTypeDef` `mdTypeDefNil` token.  
  
 `szEvent`  
 'ndaki Etkinliğin adı.  
  
 `dwEventFlags`  
 'ndaki Olay bayrakları.  
  
 `tkEventType`  
 'ndaki Olay sınıfı için belirteç. Bu bir, `mdTypeDef` veya bir `mdTypeRef` `mdTokenNil` belirteçtir.  
  
 `mdAddOn`  
 'ndaki Olaya abone olmak için kullanılan yöntem veya null.  
  
 `mdRemoveOn`  
 'ndaki Olayın aboneliğini kaldırmak için kullanılan yöntem veya null.  
  
 `mdFire`  
 'ndaki Olayı yükseltmek için kullanılan Yöntem (türetilmiş bir sınıf tarafından).  
  
 `rmdOtherMethods[]`  
 'ndaki Olayla ilişkili diğer yöntemler için bir belirteç dizisi. Dizi bir `mdMethodDefNil` belirteçle sonlandırılır.  
  
 `pmdEvent`  
 dışı Olaya atanan meta veri belirteci.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MSCorEE.dll kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit Arabirimi](imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](imetadataemit2-interface.md)
