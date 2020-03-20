---
title: IMetaDataEmit2::DefineGenericParam Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.DefineGenericParam
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::DefineGenericParam
helpviewer_keywords:
- IMetaDataEmit2::DefineGenericParam method [.NET Framework metadata]
- DefineGenericParam method [.NET Framework metadata]
ms.assetid: 47b2a3b6-907d-43dc-858d-1ae7dca1316a
topic_type:
- apiref
ms.openlocfilehash: 1868d13a9dbb73dbdf64e49c395bdbff02ce89d4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177448"
---
# <a name="imetadataemit2definegenericparam-method"></a>IMetaDataEmit2::DefineGenericParam Yöntemi
Genel bir tür parametresi için bir tanım oluşturur ve bu genel tür parametreiçin bir belirteç alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT DefineGenericParam (
    [in]  mdToken         tk,
    [in]  ULONG           ulParamSeq,
    [in]  DWORD           dwParamFlags,
    [in]  LPCWSTR         szname,
    [in]  DWORD           reserved,
    [in]  mdToken         rtkConstraints[],
    [out] mdGenericParam  *pgp  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `tk`  
 [içinde] Genel `mdTypeDef` `mdMethodDef` bir parametreyi tanımlamak için yöntemi veya oluşturucuyu temsil eden bir veya belirteç.  
  
 `ulParamSeq`  
 [içinde] Genel parametrenin dizini.  
  
 `dwParamFlags`  
 [içinde] Genel parametrenin türünü açıklayan [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) numaralandırmadeğeri.  
  
 `szname`  
 [içinde] Parametrenin adı.  
  
 `reserved`  
 [içinde] Bu parametre gelecekteki genişletilebilirlik için ayrılmıştır.  
  
 `rtkConstraints`  
 [içinde] Sıfır sonlandırılmış tür kısıtlamaları dizisi. Dizi üyeleri bir `mdTypeDef` `mdTypeRef`, `mdTypeSpec` veya meta veri belirteci olmalıdır.  
  
 `pgp`  
 [çıkış] Genel parametreyi temsil eden bir belirteç.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** Cor.h  
  
 **Kütüphane:** MsCorEE.dll'de kaynak olarak kullanılır  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [IMetaDataEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
