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
ms.openlocfilehash: a58e03875ec021b41479085fa9e27a4321ae965e
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84004380"
---
# <a name="imetadataemitdefineparam-method"></a>IMetaDataEmit::DefineParam Yöntemi
Belirtilen belirteç tarafından başvurulan yöntem için belirtilen imzaya sahip bir parametre tanımı oluşturur ve bu parametre tanımı için bir belirteç alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
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
 'ndaki Parametresi tanımlanmakta olan metodun belirteci.  
  
 `ulParamSeq`  
 'ndaki Parametre sıra numarası.  
  
 `szName`  
 'ndaki Parametrenin Unicode olarak adı.  
  
 `dwParamFlags`  
 'ndaki Parametre bayrakları. Bu bir değer bit değeridir `CorParamAttr` .  
  
 `dwCPlusTypeFlag`  
 [in] `ELEMENT_TYPE_` *\** sabit değer için.  
  
 `pValue`  
 'ndaki Parametrenin sabit değeri.  
  
 `cchValue`  
 'ndaki ' Nin Unicode karakterdeki boyutu `pValue` .  
  
 `ppd`  
 dışı `mdParamDef`Atanan belirteç.  
  
## <a name="remarks"></a>Açıklamalar  
 İçindeki sıra değerleri, `ulParamSeq` Parametreler için 1 ile başlar. Dönüş değerinin sıra numarası 0 ' dır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MSCorEE. dll içinde kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit Arabirimi](imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](imetadataemit2-interface.md)
