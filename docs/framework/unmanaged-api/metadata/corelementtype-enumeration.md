---
description: 'Daha fazla bilgi edinin: CorElementType numaralandırması'
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
ms.openlocfilehash: 3eaf75a6d2094ec875ab1861aac49e4382e65801
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784541"
---
# <a name="corelementtype-enumeration"></a><span data-ttu-id="5f6d6-103">CorElementType Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="5f6d6-103">CorElementType Enumeration</span></span>

<span data-ttu-id="5f6d6-104">Ortak dil çalışma zamanını <xref:System.Type> , tür değiştiricisini veya meta veri türü imzasında bir tür hakkındaki bilgileri belirtir.</span><span class="sxs-lookup"><span data-stu-id="5f6d6-104">Specifies a common language runtime <xref:System.Type>, a type modifier, or information about a type in a metadata type signature.</span></span>

## <a name="syntax"></a><span data-ttu-id="5f6d6-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="5f6d6-105">Syntax</span></span>

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

## <a name="members"></a><span data-ttu-id="5f6d6-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="5f6d6-106">Members</span></span>

|<span data-ttu-id="5f6d6-107">Üye</span><span class="sxs-lookup"><span data-stu-id="5f6d6-107">Member</span></span>|<span data-ttu-id="5f6d6-108">Description</span><span class="sxs-lookup"><span data-stu-id="5f6d6-108">Description</span></span>|
|------------|-----------------|
|`ELEMENT_TYPE_END`|<span data-ttu-id="5f6d6-109">Dahili olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5f6d6-109">Used internally.</span></span>|
|`ELEMENT_TYPE_VOID`|<span data-ttu-id="5f6d6-110">Void türü.</span><span class="sxs-lookup"><span data-stu-id="5f6d6-110">A void type.</span></span>|
|`ELEMENT_TYPE_BOOLEAN`|<span data-ttu-id="5f6d6-111">Boole türü</span><span class="sxs-lookup"><span data-stu-id="5f6d6-111">A Boolean type</span></span>|
|`ELEMENT_TYPE_CHAR`|<span data-ttu-id="5f6d6-112">Bir karakter türü.</span><span class="sxs-lookup"><span data-stu-id="5f6d6-112">A character type.</span></span>|
|`ELEMENT_TYPE_I1`|<span data-ttu-id="5f6d6-113">İşaretli bir 1 baytlık tamsayı.</span><span class="sxs-lookup"><span data-stu-id="5f6d6-113">A signed 1-byte integer.</span></span>|
|`ELEMENT_TYPE_U1`|<span data-ttu-id="5f6d6-114">İşaretsiz bir 1 baytlık tamsayı.</span><span class="sxs-lookup"><span data-stu-id="5f6d6-114">An unsigned 1-byte integer.</span></span>|
|`ELEMENT_TYPE_I2`|<span data-ttu-id="5f6d6-115">İşaretli bir 2 baytlık tamsayı.</span><span class="sxs-lookup"><span data-stu-id="5f6d6-115">A signed 2-byte integer.</span></span>|
|`ELEMENT_TYPE_U2`|<span data-ttu-id="5f6d6-116">İşaretsiz bir 2 baytlık tamsayı.</span><span class="sxs-lookup"><span data-stu-id="5f6d6-116">An unsigned 2-byte integer.</span></span>|
|`ELEMENT_TYPE_I4`|<span data-ttu-id="5f6d6-117">İşaretli 4 baytlık tamsayı.</span><span class="sxs-lookup"><span data-stu-id="5f6d6-117">A signed 4-byte integer.</span></span>|
|`ELEMENT_TYPE_U4`|<span data-ttu-id="5f6d6-118">İşaretsiz 4 baytlık tamsayı.</span><span class="sxs-lookup"><span data-stu-id="5f6d6-118">An unsigned 4-byte integer.</span></span>|
|`ELEMENT_TYPE_I8`|<span data-ttu-id="5f6d6-119">İşaretli 8 baytlık tamsayı.</span><span class="sxs-lookup"><span data-stu-id="5f6d6-119">A signed 8-byte integer.</span></span>|
|`ELEMENT_TYPE_U8`|<span data-ttu-id="5f6d6-120">İşaretsiz 8 baytlık tamsayı.</span><span class="sxs-lookup"><span data-stu-id="5f6d6-120">An unsigned 8-byte integer.</span></span>|
|`ELEMENT_TYPE_R4`|<span data-ttu-id="5f6d6-121">4 baytlık kayan nokta.</span><span class="sxs-lookup"><span data-stu-id="5f6d6-121">A 4-byte floating point.</span></span>|
|`ELEMENT_TYPE_R8`|<span data-ttu-id="5f6d6-122">8 baytlık kayan nokta.</span><span class="sxs-lookup"><span data-stu-id="5f6d6-122">An 8-byte floating point.</span></span>|
|`ELEMENT_TYPE_STRING`|<span data-ttu-id="5f6d6-123">Bir System. String türü.</span><span class="sxs-lookup"><span data-stu-id="5f6d6-123">A System.String type.</span></span>|
|`ELEMENT_TYPE_PTR`|<span data-ttu-id="5f6d6-124">Bir işaretçi türü değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="5f6d6-124">A pointer type modifier.</span></span>|
|`ELEMENT_TYPE_BYREF`|<span data-ttu-id="5f6d6-125">Bir başvuru türü değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="5f6d6-125">A reference type modifier.</span></span>|
|`ELEMENT_TYPE_VALUETYPE`|<span data-ttu-id="5f6d6-126">Değer türü değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="5f6d6-126">A value type modifier.</span></span>|
|`ELEMENT_TYPE_CLASS`|<span data-ttu-id="5f6d6-127">Bir sınıf türü değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="5f6d6-127">A class type modifier.</span></span>|
|`ELEMENT_TYPE_VAR`|<span data-ttu-id="5f6d6-128">Sınıf değişkeni tür değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="5f6d6-128">A class variable type modifier.</span></span>|
|`ELEMENT_TYPE_ARRAY`|<span data-ttu-id="5f6d6-129">Çok boyutlu dizi türü değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="5f6d6-129">A multi-dimensional array type modifier.</span></span>|
|`ELEMENT_TYPE_GENERICINST`|<span data-ttu-id="5f6d6-130">Genel türler için tür değiştirici.</span><span class="sxs-lookup"><span data-stu-id="5f6d6-130">A type modifier for generic types.</span></span>|
|`ELEMENT_TYPE_TYPEDBYREF`|<span data-ttu-id="5f6d6-131">Türü belirtilmiş bir başvuru.</span><span class="sxs-lookup"><span data-stu-id="5f6d6-131">A typed reference.</span></span>|
|`ELEMENT_TYPE_I`|<span data-ttu-id="5f6d6-132">Yerel tamsayının boyutu.</span><span class="sxs-lookup"><span data-stu-id="5f6d6-132">Size of a native integer.</span></span>|
|`ELEMENT_TYPE_U`|<span data-ttu-id="5f6d6-133">İşaretsiz yerel tamsayının boyutu.</span><span class="sxs-lookup"><span data-stu-id="5f6d6-133">Size of an unsigned native integer.</span></span>|
|`ELEMENT_TYPE_FNPTR`|<span data-ttu-id="5f6d6-134">İşleve yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5f6d6-134">A pointer to a function.</span></span>|
|`ELEMENT_TYPE_OBJECT`|<span data-ttu-id="5f6d6-135">Bir System. Object türü.</span><span class="sxs-lookup"><span data-stu-id="5f6d6-135">A System.Object type.</span></span>|
|`ELEMENT_TYPE_SZARRAY`|<span data-ttu-id="5f6d6-136">Tek boyutlu, sıfır alt sınır dizisi türü değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="5f6d6-136">A single-dimensional, zero lower-bound array type modifier.</span></span>|
|`ELEMENT_TYPE_MVAR`|<span data-ttu-id="5f6d6-137">Yöntem değişken türü değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="5f6d6-137">A method variable type modifier.</span></span>|
|`ELEMENT_TYPE_CMOD_REQD`|<span data-ttu-id="5f6d6-138">C dili için gerekli değiştirici.</span><span class="sxs-lookup"><span data-stu-id="5f6d6-138">A C language required modifier.</span></span>|
|`ELEMENT_TYPE_CMOD_OPT`|<span data-ttu-id="5f6d6-139">C dili isteğe bağlı değiştirici.</span><span class="sxs-lookup"><span data-stu-id="5f6d6-139">A C language optional modifier.</span></span>|
|`ELEMENT_TYPE_INTERNAL`|<span data-ttu-id="5f6d6-140">Dahili olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5f6d6-140">Used internally.</span></span>|
|`ELEMENT_TYPE_MAX`|<span data-ttu-id="5f6d6-141">Geçersiz bir tür.</span><span class="sxs-lookup"><span data-stu-id="5f6d6-141">An invalid type.</span></span>|
|`ELEMENT_TYPE_MODIFIER`|<span data-ttu-id="5f6d6-142">Dahili olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5f6d6-142">Used internally.</span></span>|
|`ELEMENT_TYPE_SENTINEL`|<span data-ttu-id="5f6d6-143">Değişken parametre sayısının bir listesi için Sentinel olan bir tür değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="5f6d6-143">A type modifier that is a sentinel for a list of a variable number of parameters.</span></span>|
|`ELEMENT_TYPE_PINNED`|<span data-ttu-id="5f6d6-144">Dahili olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5f6d6-144">Used internally.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5f6d6-145">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5f6d6-145">Remarks</span></span>

<span data-ttu-id="5f6d6-146">Tür değiştiricileri, daha karmaşık türleri temsil etme temelini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5f6d6-146">The type modifiers form the basis for representing more complex types.</span></span> <span data-ttu-id="5f6d6-147">Tür `CorElementType` imzasında hemen takip eden değere bir tür değiştirici değeri uygulanır.</span><span class="sxs-lookup"><span data-stu-id="5f6d6-147">A `CorElementType` type modifier value is applied to the value that immediately follows it in the type signature.</span></span> <span data-ttu-id="5f6d6-148">`CorElementType`Tür değiştirici değerini izleyen değer, `CorElementType` Aşağıdaki tabloda belirtildiği gibi basit bir tür değeri, meta veri belirteci veya başka bir değer olabilir.</span><span class="sxs-lookup"><span data-stu-id="5f6d6-148">The value that follows the `CorElementType` type modifier value can be a `CorElementType` simple type value, a metadata token, or other value, as specified in the following table.</span></span>

> [!NOTE]
> <span data-ttu-id="5f6d6-149">Tüm sayılar (*sayı*, *bağımsız değişken sayısı*, *meta veri belirteci*, *derece*, *sayı* ve *bağlantılı*) sıkıştırılmış tamsayılar olarak depolanır.</span><span class="sxs-lookup"><span data-stu-id="5f6d6-149">All numbers (*number*, *argument Count*, *metadata token*, *rank*, *count*, and *bound*) are stored as compressed integers.</span></span> <span data-ttu-id="5f6d6-150">Ayrıntılar için bkz. ECMA Web sitesinde [standart ECMA-335-ortak dil altyapısı (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm) .</span><span class="sxs-lookup"><span data-stu-id="5f6d6-150">See [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm) on the ECMA Web site for details.</span></span>

|<span data-ttu-id="5f6d6-151">Tür değiştiricisi</span><span class="sxs-lookup"><span data-stu-id="5f6d6-151">Type modifier</span></span>|<span data-ttu-id="5f6d6-152">Biçimlendir</span><span class="sxs-lookup"><span data-stu-id="5f6d6-152">Format</span></span>|
|-------------------|------------|
|`ELEMENT_TYPE_PTR`|<span data-ttu-id="5f6d6-153">ELEMENT_TYPE_PTR \<a `CorElementType` value></span><span class="sxs-lookup"><span data-stu-id="5f6d6-153">ELEMENT_TYPE_PTR \<a `CorElementType` value></span></span>|
|`ELEMENT_TYPE_BYREF`|<span data-ttu-id="5f6d6-154">ELEMENT_TYPE_BYREF \<a `CorElementType` value></span><span class="sxs-lookup"><span data-stu-id="5f6d6-154">ELEMENT_TYPE_BYREF \<a `CorElementType` value></span></span>|
|`ELEMENT_TYPE_VALUETYPE`|<span data-ttu-id="5f6d6-155">ELEMENT_TYPE_VALUETYPE \<an `mdTypeDef` metadata token></span><span class="sxs-lookup"><span data-stu-id="5f6d6-155">ELEMENT_TYPE_VALUETYPE \<an `mdTypeDef` metadata token></span></span>|
|`ELEMENT_TYPE_CLASS`|<span data-ttu-id="5f6d6-156">ELEMENT_TYPE_CLASS \<an `mdTypeDef` metadata token></span><span class="sxs-lookup"><span data-stu-id="5f6d6-156">ELEMENT_TYPE_CLASS \<an `mdTypeDef` metadata token></span></span>|
|`ELEMENT_TYPE_VAR`|<span data-ttu-id="5f6d6-157">ELEMENT_TYPE_VAR \<number></span><span class="sxs-lookup"><span data-stu-id="5f6d6-157">ELEMENT_TYPE_VAR \<number></span></span>|
|`ELEMENT_TYPE_ARRAY`|<span data-ttu-id="5f6d6-158">ELEMENT_TYPE_ARRAY \<a `CorElementType` value> \<rank> \<count1> \<bound1> ... \<countN>\<boundN></span><span class="sxs-lookup"><span data-stu-id="5f6d6-158">ELEMENT_TYPE_ARRAY \<a `CorElementType` value> \<rank> \<count1> \<bound1> ... \<countN> \<boundN></span></span>|
|`ELEMENT_TYPE_GENERICINST`|<span data-ttu-id="5f6d6-159">ELEMENT_TYPE_GENERICINST \<an `mdTypeDef` metadata token> \<argument Count> \<arg1> ... \<argN></span><span class="sxs-lookup"><span data-stu-id="5f6d6-159">ELEMENT_TYPE_GENERICINST \<an `mdTypeDef` metadata token> \<argument Count> \<arg1> ... \<argN></span></span>|
|`ELEMENT_TYPE_FNPTR`|<span data-ttu-id="5f6d6-160">ELEMENT_TYPE_FNPTR \<complete signature for the function, including calling convention></span><span class="sxs-lookup"><span data-stu-id="5f6d6-160">ELEMENT_TYPE_FNPTR \<complete signature for the function, including calling convention></span></span>|
|`ELEMENT_TYPE_SZARRAY`|<span data-ttu-id="5f6d6-161">ELEMENT_TYPE_SZARRAY \<a `CorElementType` value></span><span class="sxs-lookup"><span data-stu-id="5f6d6-161">ELEMENT_TYPE_SZARRAY \<a `CorElementType` value></span></span>|
|`ELEMENT_TYPE_MVAR`|<span data-ttu-id="5f6d6-162">ELEMENT_TYPE_MVAR \<number></span><span class="sxs-lookup"><span data-stu-id="5f6d6-162">ELEMENT_TYPE_MVAR \<number></span></span>|
|`ELEMENT_TYPE_CMOD_REQD`|<span data-ttu-id="5f6d6-163">ELEMENT_TYPE_\<a `mdTypeRef` or `mdTypeDef` metadata token></span><span class="sxs-lookup"><span data-stu-id="5f6d6-163">ELEMENT_TYPE_\<a `mdTypeRef` or `mdTypeDef` metadata token></span></span>|
|`ELEMENT_TYPE_CMOD_OPT`|<span data-ttu-id="5f6d6-164">E_T_CMOD_OPT \<a `mdTypeRef` or `mdTypeDef` metadata token></span><span class="sxs-lookup"><span data-stu-id="5f6d6-164">E_T_CMOD_OPT \<a `mdTypeRef` or `mdTypeDef` metadata token></span></span>|

## <a name="requirements"></a><span data-ttu-id="5f6d6-165">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5f6d6-165">Requirements</span></span>

<span data-ttu-id="5f6d6-166">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5f6d6-166">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="5f6d6-167">**Üst bilgi:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="5f6d6-167">**Header:** CorHdr.h</span></span>

<span data-ttu-id="5f6d6-168">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f6d6-168">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="5f6d6-169">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5f6d6-169">See also</span></span>

- [<span data-ttu-id="5f6d6-170">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="5f6d6-170">Metadata Enumerations</span></span>](metadata-enumerations.md)
