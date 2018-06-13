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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ce94765467899ac7c906b0dfcdf0ceb78c659b5f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448210"
---
# <a name="imetadataemitdefineevent-method"></a>IMetaDataEmit::DefineEvent Yöntemi
Belirtilen meta veri imzayla bir olay için bir tanım oluşturur ve bu olay tanımı için bir belirteç alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
  
#### <a name="parameters"></a>Parametreler  
 `td`  
 [in] Hedef sınıf veya arabirim için belirteci. Bu olan bir `mdTypeDef` veya `mdTypeDefNil` belirteci.  
  
 `szEvent`  
 [in] Olayın adı.  
  
 `dwEventFlags`  
 [in] Olay bayraklar.  
  
 `tkEventType`  
 [in] Event sınıfı için belirteci. Bu bir `mdTypeDef`, `mdTypeRef`, veya bir `mdTokenNil` belirteci.  
  
 `mdAddOn`  
 [in] Olay ya da null için abone olmak için kullanılan yöntem.  
  
 `mdRemoveOn`  
 [in] Olay ya da null için aboneliğinizi iptal etmek için kullanılan yöntem.  
  
 `mdFire`  
 [in] (Türetilmiş sınıf tarafından) olay yükseltmek için kullanılan yöntem.  
  
 `rmdOtherMethods[]`  
 [in] Olayla ilişkili diğer yöntemleri için belirteçleri dizisi. Dizi ile sonlandırılan bir `mdMethodDefNil` belirteci.  
  
 `pmdEvent`  
 [out] Olaya atanan meta veri simgesi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Cor.h  
  
 **Kitaplığı:** MSCorEE.dll kaynak olarak kullanılır  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IMetaDataEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
