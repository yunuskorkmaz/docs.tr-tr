---
title: CorElementType Numaralandırması
ms.date: 03/30/2017
api_name:
- CorElementType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorElementType
helpviewer_keywords:
- CorElementType enumeration [.NET Framework metadata]
ms.assetid: c3809c8f-1737-4f0f-9442-0c01ee689871
topic_type:
- apiref
ms.openlocfilehash: 25fb3278e576ebe4a538379918e868b2e5f87911
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007877"
---
# <a name="corelementtype-enumeration"></a>CorElementType Numaralandırması

Ortak dil çalışma zamanını <xref:System.Type> , tür değiştiricisini veya meta veri türü imzasında bir tür hakkındaki bilgileri belirtir.

## <a name="syntax"></a>Sözdizimi

```cpp
typedef enum CorElementType {
    ELEMENT_TYPE_END            = 0x0,
    ELEMENT_TYPE_VOID           = 0x1,
    ELEMENT_TYPE_BOOLEAN        = 0x2,
    ELEMENT_TYPE_CHAR           = 0x3,
    ELEMENT_TYPE_I1             = 0x4,
    ELEMENT_TYPE_U1             = 0x5,
    ELEMENT_TYPE_I2             = 0x6,
    ELEMENT_TYPE_U2             = 0x7,
    ELEMENT_TYPE_I4             = 0x8,
    ELEMENT_TYPE_U4             = 0x9,
    ELEMENT_TYPE_I8             = 0xa,
    ELEMENT_TYPE_U8             = 0xb,
    ELEMENT_TYPE_R4             = 0xc,
    ELEMENT_TYPE_R8             = 0xd,
    ELEMENT_TYPE_STRING         = 0xe,

    ELEMENT_TYPE_PTR            = 0xf,
    ELEMENT_TYPE_BYREF          = 0x10,

    ELEMENT_TYPE_VALUETYPE      = 0x11,
    ELEMENT_TYPE_CLASS          = 0x12,
    ELEMENT_TYPE_VAR            = 0x13,
    ELEMENT_TYPE_ARRAY          = 0x14,
    ELEMENT_TYPE_GENERICINST    = 0x15,
    ELEMENT_TYPE_TYPEDBYREF     = 0x16,

    ELEMENT_TYPE_I              = 0x18,
    ELEMENT_TYPE_U              = 0x19,
    ELEMENT_TYPE_FNPTR          = 0x1B,
    ELEMENT_TYPE_OBJECT         = 0x1C,
    ELEMENT_TYPE_SZARRAY        = 0x1D,
    ELEMENT_TYPE_MVAR           = 0x1e,

    ELEMENT_TYPE_CMOD_REQD      = 0x1F,
    ELEMENT_TYPE_CMOD_OPT       = 0x20,

    ELEMENT_TYPE_INTERNAL       = 0x21,
    ELEMENT_TYPE_MAX            = 0x22,

    ELEMENT_TYPE_MODIFIER       = 0x40,
    ELEMENT_TYPE_SENTINEL       = 0x01 | ELEMENT_TYPE_MODIFIER,
    ELEMENT_TYPE_PINNED         = 0x05 | ELEMENT_TYPE_MODIFIER

} CorElementType;
```

## <a name="members"></a>Üyeler

|Üye|Açıklama|
|------------|-----------------|
|`ELEMENT_TYPE_END`|Dahili olarak kullanılır.|
|`ELEMENT_TYPE_VOID`|Void türü.|
|`ELEMENT_TYPE_BOOLEAN`|Boole türü|
|`ELEMENT_TYPE_CHAR`|Bir karakter türü.|
|`ELEMENT_TYPE_I1`|İşaretli bir 1 baytlık tamsayı.|
|`ELEMENT_TYPE_U1`|İşaretsiz bir 1 baytlık tamsayı.|
|`ELEMENT_TYPE_I2`|İşaretli bir 2 baytlık tamsayı.|
|`ELEMENT_TYPE_U2`|İşaretsiz bir 2 baytlık tamsayı.|
|`ELEMENT_TYPE_I4`|İşaretli 4 baytlık tamsayı.|
|`ELEMENT_TYPE_U4`|İşaretsiz 4 baytlık tamsayı.|
|`ELEMENT_TYPE_I8`|İşaretli 8 baytlık tamsayı.|
|`ELEMENT_TYPE_U8`|İşaretsiz 8 baytlık tamsayı.|
|`ELEMENT_TYPE_R4`|4 baytlık kayan nokta.|
|`ELEMENT_TYPE_R8`|8 baytlık kayan nokta.|
|`ELEMENT_TYPE_STRING`|Bir System. String türü.|
|`ELEMENT_TYPE_PTR`|Bir işaretçi türü değiştiricisi.|
|`ELEMENT_TYPE_BYREF`|Bir başvuru türü değiştiricisi.|
|`ELEMENT_TYPE_VALUETYPE`|Değer türü değiştiricisi.|
|`ELEMENT_TYPE_CLASS`|Bir sınıf türü değiştiricisi.|
|`ELEMENT_TYPE_VAR`|Sınıf değişkeni tür değiştiricisi.|
|`ELEMENT_TYPE_ARRAY`|Çok boyutlu dizi türü değiştiricisi.|
|`ELEMENT_TYPE_GENERICINST`|Genel türler için tür değiştirici.|
|`ELEMENT_TYPE_TYPEDBYREF`|Türü belirtilmiş bir başvuru.|
|`ELEMENT_TYPE_I`|Yerel tamsayının boyutu.|
|`ELEMENT_TYPE_U`|İşaretsiz yerel tamsayının boyutu.|
|`ELEMENT_TYPE_FNPTR`|İşleve yönelik bir işaretçi.|
|`ELEMENT_TYPE_OBJECT`|Bir System. Object türü.|
|`ELEMENT_TYPE_SZARRAY`|Tek boyutlu, sıfır alt sınır dizisi türü değiştiricisi.|
|`ELEMENT_TYPE_MVAR`|Yöntem değişken türü değiştiricisi.|
|`ELEMENT_TYPE_CMOD_REQD`|C dili için gerekli değiştirici.|
|`ELEMENT_TYPE_CMOD_OPT`|C dili isteğe bağlı değiştirici.|
|`ELEMENT_TYPE_INTERNAL`|Dahili olarak kullanılır.|
|`ELEMENT_TYPE_MAX`|Geçersiz bir tür.|
|`ELEMENT_TYPE_MODIFIER`|Dahili olarak kullanılır.|
|`ELEMENT_TYPE_SENTINEL`|Değişken parametre sayısının bir listesi için Sentinel olan bir tür değiştiricisi.|
|`ELEMENT_TYPE_PINNED`|Dahili olarak kullanılır.|

## <a name="remarks"></a>Açıklamalar

Tür değiştiricileri, daha karmaşık türleri temsil etme temelini oluşturur. Tür `CorElementType` imzasında hemen takip eden değere bir tür değiştirici değeri uygulanır. `CorElementType`Tür değiştirici değerini izleyen değer, `CorElementType` Aşağıdaki tabloda belirtildiği gibi basit bir tür değeri, meta veri belirteci veya başka bir değer olabilir.

> [!NOTE]
> Tüm sayılar (*sayı*, *bağımsız değişken sayısı*, *meta veri belirteci*, *derece*, *sayı*ve *bağlantılı*) sıkıştırılmış tamsayılar olarak depolanır. Ayrıntılar için bkz. ECMA Web sitesinde [standart ECMA-335-ortak dil altyapısı (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm) .

|Tür değiştiricisi|Biçimlendir|
|-------------------|------------|
|`ELEMENT_TYPE_PTR`|ELEMENT_TYPE_PTR\<a `CorElementType` value>|
|`ELEMENT_TYPE_BYREF`|ELEMENT_TYPE_BYREF\<a `CorElementType` value>|
|`ELEMENT_TYPE_VALUETYPE`|ELEMENT_TYPE_VALUETYPE\<an `mdTypeDef` metadata token>|
|`ELEMENT_TYPE_CLASS`|ELEMENT_TYPE_CLASS\<an `mdTypeDef` metadata token>|
|`ELEMENT_TYPE_VAR`|ELEMENT_TYPE_VAR\<number>|
|`ELEMENT_TYPE_ARRAY`|ELEMENT_TYPE_ARRAY \<a `CorElementType` value> \<rank> \<count1> \<bound1> ... \<countN>\<boundN>|
|`ELEMENT_TYPE_GENERICINST`|ELEMENT_TYPE_GENERICINST \<an `mdTypeDef` metadata token> \<argument Count> \<arg1> ...\<argN>|
|`ELEMENT_TYPE_FNPTR`|ELEMENT_TYPE_FNPTR\<complete signature for the function, including calling convention>|
|`ELEMENT_TYPE_SZARRAY`|ELEMENT_TYPE_SZARRAY\<a `CorElementType` value>|
|`ELEMENT_TYPE_MVAR`|ELEMENT_TYPE_MVAR\<number>|
|`ELEMENT_TYPE_CMOD_REQD`|ELEMENT_TYPE_\<a `mdTypeRef` or `mdTypeDef` metadata token>|
|`ELEMENT_TYPE_CMOD_OPT`|E_T_CMOD_OPT\<a `mdTypeRef` or `mdTypeDef` metadata token>|

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).

**Üst bilgi:** CorHdr. h

**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Numaralandırmalar](metadata-enumerations.md)
