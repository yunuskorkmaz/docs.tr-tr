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
ms.openlocfilehash: 5d49ac70aceb76f69711ea4bf514f69697ac156c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447378"
---
# <a name="imetadataemitdefineparam-method"></a>IMetaDataEmit::DefineParam Yöntemi
Belirtilen belirteç tarafından başvurulan yöntemi için belirtilen imzalı bir parametrenin tanımını oluşturur ve bu parametre tanımı için bir belirteç alır.  
  
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
  
#### <a name="parameters"></a>Parametreler  
 `md`  
 [in] Parametresi tanımlı yöntemi için belirteci.  
  
 `ulParamSeq`  
 [in] Parametre sıra numarası.  
  
 `szName`  
 [in] Unicode parametresinin adı.  
  
 `dwParamFlags`  
 [in] Parametresi için işaretler. Bu, bir bit maskesi olan `CorParamAttr` değerleri.  
  
 `dwCPlusTypeFlag`  
 [in] `ELEMENT_TYPE_` *\** sabit değer.  
  
 `pValue`  
 [in] Parametresi için sabit bir değer.  
  
 `cchValue`  
 [in] Unicode karakterler, boyutunu, `pValue`.  
  
 `ppd`  
 [out] `mdParamDef` Atanan simgesi.  
  
## <a name="remarks"></a>Açıklamalar  
 Sıralı değerler `ulParamSeq` parametreleri için 1 ile başlar. Dönüş değeri bir sıra numarası 0 sahiptir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Cor.h  
  
 **Kitaplığı:** MSCorEE.dll kaynak olarak kullanılır  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IMetaDataEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
