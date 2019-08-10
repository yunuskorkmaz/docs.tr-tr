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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6057bd48ff4fe3f852f82de2bab972d95fef138c
ms.sourcegitcommit: 9ee6cd851b6e176a5811ea28ed0d5935c71950f9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68868563"
---
# <a name="corelementtype-enumeration"></a>CorElementType Numaralandırması

Ortak dil çalışma zamanını <xref:System.Type>, tür değiştiricisini veya meta veri türü imzasında bir tür hakkındaki bilgileri belirtir.

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

Tür değiştiricileri, daha karmaşık türleri temsil etme temelini oluşturur. Tür `CorElementType` imzasında hemen takip eden değere bir tür değiştirici değeri uygulanır. `CorElementType` Tür değiştirici değerini izleyen değer, aşağıdaki tabloda belirtildiği gibi basit `CorElementType` bir tür değeri, meta veri belirteci veya başka bir değer olabilir.

> [!NOTE]
> Tüm sayılar (*sayı*, *bağımsız değişken sayısı*, *meta veri belirteci*, *derece*, *sayı*ve *bağlantılı*) sıkıştırılmış tamsayılar olarak depolanır. Ayrıntılar için bkz. ECMA Web sitesinde [standart ECMA-335-ortak dil altyapısı (CLI)](https://go.microsoft.com/fwlink/?LinkID=116487) .

|Tür değiştiricisi|Biçimi|
|-------------------|------------|
|`ELEMENT_TYPE_PTR`|Değer ELEMENT_TYPE_PTR \<> `CorElementType`|
|`ELEMENT_TYPE_BYREF`|Değer ELEMENT_TYPE_BYREF \<> `CorElementType`|
|`ELEMENT_TYPE_VALUETYPE`|Element_type_valuetype \< bir`mdTypeDef` meta veri belirteci >|
|`ELEMENT_TYPE_CLASS`|Element_type_class \< bir`mdTypeDef` meta veri belirteci >|
|`ELEMENT_TYPE_VAR`|ELEMENT_TYPE_VAR \<numarası >|
|`ELEMENT_TYPE_ARRAY`|Element_type_array \<count1 `CorElementType` > \< \<bound1 > > >birdeğer\< countn > \<boundn> \<|
|`ELEMENT_TYPE_GENERICINST`|ELEMENT_TYPE_GENERICINST \< \< \<bir `mdTypeDef` meta veri belirteci > bağımsız değişken sayısı > arg1 >... \<argN >|
|`ELEMENT_TYPE_FNPTR`|Element_type_fnptr \<çağırma kuralı da dahil olmak üzere işlev için tamamlanmış imza >|
|`ELEMENT_TYPE_SZARRAY`|Değer element_type_szarray \<> `CorElementType`|
|`ELEMENT_TYPE_MVAR`|ELEMENT_TYPE_MVAR \<numarası >|
|`ELEMENT_TYPE_CMOD_REQD`|ELEMENT_TYPE_\<a `mdTypeRef` veya`mdTypeDef` meta veri belirteci >|
|`ELEMENT_TYPE_CMOD_OPT`|E_T_CMOD_OPT \<a `mdTypeRef` veya`mdTypeDef` meta veri belirteci >|

## <a name="requirements"></a>Gereksinimler

**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).

**Üst bilgi** CorHdr. h

**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Sabit Listeleri](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
