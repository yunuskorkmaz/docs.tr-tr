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
# <a name="corelementtype-enumeration"></a><span data-ttu-id="58fc6-102">CorElementType Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="58fc6-102">CorElementType Enumeration</span></span>

<span data-ttu-id="58fc6-103">Ortak dil çalışma zamanını <xref:System.Type>, tür değiştiricisini veya meta veri türü imzasında bir tür hakkındaki bilgileri belirtir.</span><span class="sxs-lookup"><span data-stu-id="58fc6-103">Specifies a common language runtime <xref:System.Type>, a type modifier, or information about a type in a metadata type signature.</span></span>

## <a name="syntax"></a><span data-ttu-id="58fc6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="58fc6-104">Syntax</span></span>

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

## <a name="members"></a><span data-ttu-id="58fc6-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="58fc6-105">Members</span></span>

|<span data-ttu-id="58fc6-106">Üye</span><span class="sxs-lookup"><span data-stu-id="58fc6-106">Member</span></span>|<span data-ttu-id="58fc6-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="58fc6-107">Description</span></span>|
|------------|-----------------|
|`ELEMENT_TYPE_END`|<span data-ttu-id="58fc6-108">Dahili olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="58fc6-108">Used internally.</span></span>|
|`ELEMENT_TYPE_VOID`|<span data-ttu-id="58fc6-109">Void türü.</span><span class="sxs-lookup"><span data-stu-id="58fc6-109">A void type.</span></span>|
|`ELEMENT_TYPE_BOOLEAN`|<span data-ttu-id="58fc6-110">Boole türü</span><span class="sxs-lookup"><span data-stu-id="58fc6-110">A Boolean type</span></span>|
|`ELEMENT_TYPE_CHAR`|<span data-ttu-id="58fc6-111">Bir karakter türü.</span><span class="sxs-lookup"><span data-stu-id="58fc6-111">A character type.</span></span>|
|`ELEMENT_TYPE_I1`|<span data-ttu-id="58fc6-112">İşaretli bir 1 baytlık tamsayı.</span><span class="sxs-lookup"><span data-stu-id="58fc6-112">A signed 1-byte integer.</span></span>|
|`ELEMENT_TYPE_U1`|<span data-ttu-id="58fc6-113">İşaretsiz bir 1 baytlık tamsayı.</span><span class="sxs-lookup"><span data-stu-id="58fc6-113">An unsigned 1-byte integer.</span></span>|
|`ELEMENT_TYPE_I2`|<span data-ttu-id="58fc6-114">İşaretli bir 2 baytlık tamsayı.</span><span class="sxs-lookup"><span data-stu-id="58fc6-114">A signed 2-byte integer.</span></span>|
|`ELEMENT_TYPE_U2`|<span data-ttu-id="58fc6-115">İşaretsiz bir 2 baytlık tamsayı.</span><span class="sxs-lookup"><span data-stu-id="58fc6-115">An unsigned 2-byte integer.</span></span>|
|`ELEMENT_TYPE_I4`|<span data-ttu-id="58fc6-116">İşaretli 4 baytlık tamsayı.</span><span class="sxs-lookup"><span data-stu-id="58fc6-116">A signed 4-byte integer.</span></span>|
|`ELEMENT_TYPE_U4`|<span data-ttu-id="58fc6-117">İşaretsiz 4 baytlık tamsayı.</span><span class="sxs-lookup"><span data-stu-id="58fc6-117">An unsigned 4-byte integer.</span></span>|
|`ELEMENT_TYPE_I8`|<span data-ttu-id="58fc6-118">İşaretli 8 baytlık tamsayı.</span><span class="sxs-lookup"><span data-stu-id="58fc6-118">A signed 8-byte integer.</span></span>|
|`ELEMENT_TYPE_U8`|<span data-ttu-id="58fc6-119">İşaretsiz 8 baytlık tamsayı.</span><span class="sxs-lookup"><span data-stu-id="58fc6-119">An unsigned 8-byte integer.</span></span>|
|`ELEMENT_TYPE_R4`|<span data-ttu-id="58fc6-120">4 baytlık kayan nokta.</span><span class="sxs-lookup"><span data-stu-id="58fc6-120">A 4-byte floating point.</span></span>|
|`ELEMENT_TYPE_R8`|<span data-ttu-id="58fc6-121">8 baytlık kayan nokta.</span><span class="sxs-lookup"><span data-stu-id="58fc6-121">An 8-byte floating point.</span></span>|
|`ELEMENT_TYPE_STRING`|<span data-ttu-id="58fc6-122">Bir System. String türü.</span><span class="sxs-lookup"><span data-stu-id="58fc6-122">A System.String type.</span></span>|
|`ELEMENT_TYPE_PTR`|<span data-ttu-id="58fc6-123">Bir işaretçi türü değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="58fc6-123">A pointer type modifier.</span></span>|
|`ELEMENT_TYPE_BYREF`|<span data-ttu-id="58fc6-124">Bir başvuru türü değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="58fc6-124">A reference type modifier.</span></span>|
|`ELEMENT_TYPE_VALUETYPE`|<span data-ttu-id="58fc6-125">Değer türü değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="58fc6-125">A value type modifier.</span></span>|
|`ELEMENT_TYPE_CLASS`|<span data-ttu-id="58fc6-126">Bir sınıf türü değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="58fc6-126">A class type modifier.</span></span>|
|`ELEMENT_TYPE_VAR`|<span data-ttu-id="58fc6-127">Sınıf değişkeni tür değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="58fc6-127">A class variable type modifier.</span></span>|
|`ELEMENT_TYPE_ARRAY`|<span data-ttu-id="58fc6-128">Çok boyutlu dizi türü değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="58fc6-128">A multi-dimensional array type modifier.</span></span>|
|`ELEMENT_TYPE_GENERICINST`|<span data-ttu-id="58fc6-129">Genel türler için tür değiştirici.</span><span class="sxs-lookup"><span data-stu-id="58fc6-129">A type modifier for generic types.</span></span>|
|`ELEMENT_TYPE_TYPEDBYREF`|<span data-ttu-id="58fc6-130">Türü belirtilmiş bir başvuru.</span><span class="sxs-lookup"><span data-stu-id="58fc6-130">A typed reference.</span></span>|
|`ELEMENT_TYPE_I`|<span data-ttu-id="58fc6-131">Yerel tamsayının boyutu.</span><span class="sxs-lookup"><span data-stu-id="58fc6-131">Size of a native integer.</span></span>|
|`ELEMENT_TYPE_U`|<span data-ttu-id="58fc6-132">İşaretsiz yerel tamsayının boyutu.</span><span class="sxs-lookup"><span data-stu-id="58fc6-132">Size of an unsigned native integer.</span></span>|
|`ELEMENT_TYPE_FNPTR`|<span data-ttu-id="58fc6-133">İşleve yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="58fc6-133">A pointer to a function.</span></span>|
|`ELEMENT_TYPE_OBJECT`|<span data-ttu-id="58fc6-134">Bir System. Object türü.</span><span class="sxs-lookup"><span data-stu-id="58fc6-134">A System.Object type.</span></span>|
|`ELEMENT_TYPE_SZARRAY`|<span data-ttu-id="58fc6-135">Tek boyutlu, sıfır alt sınır dizisi türü değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="58fc6-135">A single-dimensional, zero lower-bound array type modifier.</span></span>|
|`ELEMENT_TYPE_MVAR`|<span data-ttu-id="58fc6-136">Yöntem değişken türü değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="58fc6-136">A method variable type modifier.</span></span>|
|`ELEMENT_TYPE_CMOD_REQD`|<span data-ttu-id="58fc6-137">C dili için gerekli değiştirici.</span><span class="sxs-lookup"><span data-stu-id="58fc6-137">A C language required modifier.</span></span>|
|`ELEMENT_TYPE_CMOD_OPT`|<span data-ttu-id="58fc6-138">C dili isteğe bağlı değiştirici.</span><span class="sxs-lookup"><span data-stu-id="58fc6-138">A C language optional modifier.</span></span>|
|`ELEMENT_TYPE_INTERNAL`|<span data-ttu-id="58fc6-139">Dahili olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="58fc6-139">Used internally.</span></span>|
|`ELEMENT_TYPE_MAX`|<span data-ttu-id="58fc6-140">Geçersiz bir tür.</span><span class="sxs-lookup"><span data-stu-id="58fc6-140">An invalid type.</span></span>|
|`ELEMENT_TYPE_MODIFIER`|<span data-ttu-id="58fc6-141">Dahili olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="58fc6-141">Used internally.</span></span>|
|`ELEMENT_TYPE_SENTINEL`|<span data-ttu-id="58fc6-142">Değişken parametre sayısının bir listesi için Sentinel olan bir tür değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="58fc6-142">A type modifier that is a sentinel for a list of a variable number of parameters.</span></span>|
|`ELEMENT_TYPE_PINNED`|<span data-ttu-id="58fc6-143">Dahili olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="58fc6-143">Used internally.</span></span>|

## <a name="remarks"></a><span data-ttu-id="58fc6-144">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="58fc6-144">Remarks</span></span>

<span data-ttu-id="58fc6-145">Tür değiştiricileri, daha karmaşık türleri temsil etme temelini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="58fc6-145">The type modifiers form the basis for representing more complex types.</span></span> <span data-ttu-id="58fc6-146">Tür `CorElementType` imzasında hemen takip eden değere bir tür değiştirici değeri uygulanır.</span><span class="sxs-lookup"><span data-stu-id="58fc6-146">A `CorElementType` type modifier value is applied to the value that immediately follows it in the type signature.</span></span> <span data-ttu-id="58fc6-147">`CorElementType` Tür değiştirici değerini izleyen değer, aşağıdaki tabloda belirtildiği gibi basit `CorElementType` bir tür değeri, meta veri belirteci veya başka bir değer olabilir.</span><span class="sxs-lookup"><span data-stu-id="58fc6-147">The value that follows the `CorElementType` type modifier value can be a `CorElementType` simple type value, a metadata token, or other value, as specified in the following table.</span></span>

> [!NOTE]
> <span data-ttu-id="58fc6-148">Tüm sayılar (*sayı*, *bağımsız değişken sayısı*, *meta veri belirteci*, *derece*, *sayı*ve *bağlantılı*) sıkıştırılmış tamsayılar olarak depolanır.</span><span class="sxs-lookup"><span data-stu-id="58fc6-148">All numbers (*number*, *argument Count*, *metadata token*, *rank*, *count*, and *bound*) are stored as compressed integers.</span></span> <span data-ttu-id="58fc6-149">Ayrıntılar için bkz. ECMA Web sitesinde [standart ECMA-335-ortak dil altyapısı (CLI)](https://go.microsoft.com/fwlink/?LinkID=116487) .</span><span class="sxs-lookup"><span data-stu-id="58fc6-149">See [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=116487) on the ECMA Web site for details.</span></span>

|<span data-ttu-id="58fc6-150">Tür değiştiricisi</span><span class="sxs-lookup"><span data-stu-id="58fc6-150">Type modifier</span></span>|<span data-ttu-id="58fc6-151">Biçimi</span><span class="sxs-lookup"><span data-stu-id="58fc6-151">Format</span></span>|
|-------------------|------------|
|`ELEMENT_TYPE_PTR`|<span data-ttu-id="58fc6-152">Değer ELEMENT_TYPE_PTR \<> `CorElementType`</span><span class="sxs-lookup"><span data-stu-id="58fc6-152">ELEMENT_TYPE_PTR \<a `CorElementType` value></span></span>|
|`ELEMENT_TYPE_BYREF`|<span data-ttu-id="58fc6-153">Değer ELEMENT_TYPE_BYREF \<> `CorElementType`</span><span class="sxs-lookup"><span data-stu-id="58fc6-153">ELEMENT_TYPE_BYREF \<a `CorElementType` value></span></span>|
|`ELEMENT_TYPE_VALUETYPE`|<span data-ttu-id="58fc6-154">Element_type_valuetype \< bir`mdTypeDef` meta veri belirteci ></span><span class="sxs-lookup"><span data-stu-id="58fc6-154">ELEMENT_TYPE_VALUETYPE \<an `mdTypeDef` metadata token></span></span>|
|`ELEMENT_TYPE_CLASS`|<span data-ttu-id="58fc6-155">Element_type_class \< bir`mdTypeDef` meta veri belirteci ></span><span class="sxs-lookup"><span data-stu-id="58fc6-155">ELEMENT_TYPE_CLASS \<an `mdTypeDef` metadata token></span></span>|
|`ELEMENT_TYPE_VAR`|<span data-ttu-id="58fc6-156">ELEMENT_TYPE_VAR \<numarası ></span><span class="sxs-lookup"><span data-stu-id="58fc6-156">ELEMENT_TYPE_VAR \<number></span></span>|
|`ELEMENT_TYPE_ARRAY`|<span data-ttu-id="58fc6-157">Element_type_array \<count1 `CorElementType` > \< \<bound1 > > >birdeğer\< countn > \<boundn> \<</span><span class="sxs-lookup"><span data-stu-id="58fc6-157">ELEMENT_TYPE_ARRAY \<a `CorElementType` value> \<rank> \<count1> \<bound1> ... \<countN> \<boundN></span></span>|
|`ELEMENT_TYPE_GENERICINST`|<span data-ttu-id="58fc6-158">ELEMENT_TYPE_GENERICINST \< \< \<bir `mdTypeDef` meta veri belirteci > bağımsız değişken sayısı > arg1 >... \<argN ></span><span class="sxs-lookup"><span data-stu-id="58fc6-158">ELEMENT_TYPE_GENERICINST \<an `mdTypeDef` metadata token> \<argument Count> \<arg1> ... \<argN></span></span>|
|`ELEMENT_TYPE_FNPTR`|<span data-ttu-id="58fc6-159">Element_type_fnptr \<çağırma kuralı da dahil olmak üzere işlev için tamamlanmış imza ></span><span class="sxs-lookup"><span data-stu-id="58fc6-159">ELEMENT_TYPE_FNPTR \<complete signature for the function, including calling convention></span></span>|
|`ELEMENT_TYPE_SZARRAY`|<span data-ttu-id="58fc6-160">Değer element_type_szarray \<> `CorElementType`</span><span class="sxs-lookup"><span data-stu-id="58fc6-160">ELEMENT_TYPE_SZARRAY \<a `CorElementType` value></span></span>|
|`ELEMENT_TYPE_MVAR`|<span data-ttu-id="58fc6-161">ELEMENT_TYPE_MVAR \<numarası ></span><span class="sxs-lookup"><span data-stu-id="58fc6-161">ELEMENT_TYPE_MVAR \<number></span></span>|
|`ELEMENT_TYPE_CMOD_REQD`|<span data-ttu-id="58fc6-162">ELEMENT_TYPE_\<a `mdTypeRef` veya`mdTypeDef` meta veri belirteci ></span><span class="sxs-lookup"><span data-stu-id="58fc6-162">ELEMENT_TYPE_\<a `mdTypeRef` or `mdTypeDef` metadata token></span></span>|
|`ELEMENT_TYPE_CMOD_OPT`|<span data-ttu-id="58fc6-163">E_T_CMOD_OPT \<a `mdTypeRef` veya`mdTypeDef` meta veri belirteci ></span><span class="sxs-lookup"><span data-stu-id="58fc6-163">E_T_CMOD_OPT \<a `mdTypeRef` or `mdTypeDef` metadata token></span></span>|

## <a name="requirements"></a><span data-ttu-id="58fc6-164">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="58fc6-164">Requirements</span></span>

<span data-ttu-id="58fc6-165">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="58fc6-165">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="58fc6-166">**Üst bilgi** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="58fc6-166">**Header:** CorHdr.h</span></span>

<span data-ttu-id="58fc6-167">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58fc6-167">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="58fc6-168">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="58fc6-168">See also</span></span>

- [<span data-ttu-id="58fc6-169">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="58fc6-169">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
