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
ms.openlocfilehash: 2807458549db02598ba05f2aa80fa6ea6fbc5a13
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177700"
---
# <a name="imetadataemitdefineparam-method"></a>IMetaDataEmit::DefineParam Yöntemi
Belirtilen belirteç tarafından başvurulan yöntem için belirtilen imzaile bir parametre tanımı oluşturur ve bu parametre tanımı için bir belirteç alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
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
 [içinde] Parametresi tanımlanan yöntemin belirteci.  
  
 `ulParamSeq`  
 [içinde] Parametre sıra numarası.  
  
 `szName`  
 [içinde] Unicode'daki parametrenin adı.  
  
 `dwParamFlags`  
 [içinde] Parametre için bayraklar. Bu `CorParamAttr` değerlerin bir bitmask olduğunu.  
  
 `dwCPlusTypeFlag`  
 [içinde] `ELEMENT_TYPE_` sabit değer *\** için.  
  
 `pValue`  
 [içinde] Parametrenin sabit değeri.  
  
 `cchValue`  
 [içinde] Unicode karakterlerinin boyutu. `pValue`  
  
 `ppd`  
 [çıkış] Atanan `mdParamDef` belirteç.  
  
## <a name="remarks"></a>Açıklamalar  
 Parametreler için `ulParamSeq` 1 ile başlarda sıra değerleri. İade değerinin sıra numarası 0'dır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** Cor.h  
  
 **Kütüphane:** MSCorEE.dll'de kaynak olarak kullanılır  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
