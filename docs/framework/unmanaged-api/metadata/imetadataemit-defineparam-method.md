---
title: IMetaDataEmit::DefineParam Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineParam
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineParam
helpviewer_keywords:
- IMetaDataEmit::DefineParam method [.NET Framework metadata]
- DefineParam method [.NET Framework metadata]
ms.assetid: d86a3d14-4796-4909-9591-dfafe3de5ce4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 86711d107636505ab7aa23f0f72f70bd3e27635d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992660"
---
# <a name="imetadataemitdefineparam-method"></a>IMetaDataEmit::DefineParam Yöntemi
Belirtilen belirteç tarafından başvurulan yöntemi için belirtilen imzaya sahip bir parametre tanımında oluşturur ve bu parametre tanımı için bir belirteç alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT DefineParam (  
    [in]  mdMethodDef md,   
    [in]  ULONG       ulParamSeq,   
    [in]  LPCWSTR     szName,   
    [in]  DWORD       dwParamFlags,   
    [in]  DWORD       dwCPlusTypeFlag,   
    [in]  void const  *pValue,  
    [in]  ULONG       cchValue,   
    [out] mdParamDef  *ppd   
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `md`  
 [in] Parametresi tanımlı yöntem için belirteç.  
  
 `ulParamSeq`  
 [in] Parametre dizisi numarası.  
  
 `szName`  
 [in] Unicode parametrenin adı.  
  
 `dwParamFlags`  
 [in] Parametresi için bayrakları. Bu, bir bit maskesi, `CorParamAttr` değerleri.  
  
 `dwCPlusTypeFlag`  
 [in] `ELEMENT_TYPE_` *\** sabit değer.  
  
 `pValue`  
 [in] Parametresi için sabit bir değer.  
  
 `cchValue`  
 [in] Unicode karakter cinsinden boyutu, `pValue`.  
  
 `ppd`  
 [out] `mdParamDef` Atanan simgesi.  
  
## <a name="remarks"></a>Açıklamalar  
 Sıralı değerleri `ulParamSeq` parametreleri için 1 ile başlar. Dönüş değeri bir sıra numarası 0 sahiptir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** COR.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll kullanılan  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
