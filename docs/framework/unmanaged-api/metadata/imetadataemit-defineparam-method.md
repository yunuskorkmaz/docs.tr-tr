---
title: "IMetaDataEmit::DefineParam Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineParam
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineParam
helpviewer_keywords:
- IMetaDataEmit::DefineParam method [.NET Framework metadata]
- DefineParam method [.NET Framework metadata]
ms.assetid: d86a3d14-4796-4909-9591-dfafe3de5ce4
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5abe9cf0385a42645468bf58c2f81223ac4eeead
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
 [in] `ELEMENT_TYPE_`  *\**  sabit değer.  
  
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
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Imetadataemit arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [Imetadataemit2 arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
