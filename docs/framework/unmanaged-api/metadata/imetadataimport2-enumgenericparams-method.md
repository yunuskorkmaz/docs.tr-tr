---
title: IMetaDataImport2::EnumGenericParams Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.EnumGenericParams
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::EnumGenericParams
helpviewer_keywords:
- EnumGenericParams method [.NET Framework metadata]
- IMetaDataImport2::EnumGenericParams method [.NET Framework metadata]
ms.assetid: b50488a5-3cf0-483c-82dc-2892a3ec61ac
topic_type:
- apiref
ms.openlocfilehash: 093e3edf0a3c06222ebc56a4876fca08d1b7578f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490737"
---
# <a name="imetadataimport2enumgenericparams-method"></a>IMetaDataImport2::EnumGenericParams Yöntemi
Belirtilen TypeDef veya MethodDef belirteciyle ilişkili bir genel parametre belirteçleri dizisi için bir Numaralandırıcı alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp
HRESULT EnumGenericParams (  
   [in, out] HCORENUM     *phEnum,
   [in]  mdToken          tk,  
   [out] mdGenericParam   rGenericParams[],
   [in]  ULONG            cMax,
   [out] ULONG            *pcGenericParams  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `phEnum`  
 [in, out] Numaralandırıcı için bir işaretçi.  
  
 `tk`  
 'ndaki Genel parametreleri numaralandırılmış olan TypeDef veya MethodDef belirteci.  
  
 `rGenericParams`  
 dışı Numaralandırılacak genel parametrelerin dizisi.  
  
 `cMax`  
 'ndaki İstenen en fazla belirteç sayısı, içine yerleştirilecek `rGenericParams` .  
  
 `pcGenericParams`  
 dışı Döndürülen belirteç sayısı döndürüldü `rGenericParams` .  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Description|  
|-------------|-----------------|  
|`S_OK`|`EnumGenericParams`başarıyla döndürüldü.|  
|`S_FALSE`|`phEnum`Üye öğesi yok. Bu durumda, `pcGenericParams` 0 (sıfır) olarak ayarlanır.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport2 Arabirimi](imetadataimport2-interface.md)
- [IMetaDataImport Arabirimi](imetadataimport-interface.md)
