---
title: IMetaDataImport2::EnumMethodSpecs Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.EnumMethodSpecs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::EnumMethodSpecs
helpviewer_keywords:
- IMetaDataImport2::EnumMethodSpecs method [.NET Framework metadata]
- EnumMethodSpecs method [.NET Framework metadata]
ms.assetid: b3fc1e6c-bcb6-4915-baf8-7dc0a31b8724
topic_type:
- apiref
ms.openlocfilehash: 8f6fbc570e7ea85aca5b365611d58a1700fb27cd
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490734"
---
# <a name="imetadataimport2enummethodspecs-method"></a>IMetaDataImport2::EnumMethodSpecs Yöntemi
Belirtilen MethodDef veya MemberRef belirteciyle ilişkili bir MethodSpec belirteçleri dizisi için bir Numaralandırıcı alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT EnumMethodSpecs (  
    [in, out] HCORENUM      *phEnum,
    [in]      mdToken       tk,  
    [out]     mdMethodSpec  rMethodSpecs[],  
    [in]      ULONG         cMax,  
    [out]     ULONG         *pcMethodSpecs  
);
```  
  
## <a name="parameters"></a>Parametreler  
 `phEnum`  
 [in, out] İçin numaralandırıcı işaretçisi `rMethodSpecs` .  
  
 `tk`  
 'ndaki MethodSpec belirteçleri numaralandırılmış olan yöntemi temsil eden MemberRef veya MethodDef belirteci. Değeri `tk` 0 (sıfır) ise, kapsamdaki tüm MethodSpec belirteçleri numaralandırılır.  
  
 `rMethodSpecs`  
 dışı Numaralandırılacak MethodSpec belirteçlerinin dizisi.  
  
 `cMax`  
 'ndaki İstenen en fazla belirteç sayısı, içine yerleştirilecek `rMethodSpecs` .  
  
 `pcMethodSpecs`  
 dışı Döndürülen belirteç sayısı döndürüldü `rMethodSpecs` .  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Description|  
|-------------|-----------------|  
|`S_OK`|`EnumMethodSpecs`başarıyla döndürüldü.|  
|`S_FALSE`|`phEnum`Üye öğesi yok. Bu durumda, `pcMethodSpecs` 0 (sıfır) olarak ayarlanır.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport2 Arabirimi](imetadataimport2-interface.md)
- [IMetaDataImport Arabirimi](imetadataimport-interface.md)
