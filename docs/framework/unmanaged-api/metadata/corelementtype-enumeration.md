---
title: CorElementType sabit listesi1
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
ms.openlocfilehash: 5112c3c8d5fef6efada4bffdfa575716503515e6
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43488254"
---
# <a name="corelementtype-enumeration1"></a><span data-ttu-id="07fad-102">CorElementType sabit listesi1</span><span class="sxs-lookup"><span data-stu-id="07fad-102">CorElementType Enumeration1</span></span>
<span data-ttu-id="07fad-103">Ortak dil çalışma zamanı belirtir <xref:System.Type>, bir tür değiştiricisi ya da bir türü bir meta veri türü imzada hakkında bilgiler.</span><span class="sxs-lookup"><span data-stu-id="07fad-103">Specifies a common language runtime <xref:System.Type>, a type modifier, or information about a type in a metadata type signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07fad-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="07fad-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="07fad-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="07fad-105">Members</span></span>  
  
|<span data-ttu-id="07fad-106">Üye</span><span class="sxs-lookup"><span data-stu-id="07fad-106">Member</span></span>|<span data-ttu-id="07fad-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="07fad-107">Description</span></span>|  
|------------|-----------------|  
|`ELEMENT_TYPE_END`|<span data-ttu-id="07fad-108">Dahili olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="07fad-108">Used internally.</span></span>|  
|`ELEMENT_TYPE_VOID`|<span data-ttu-id="07fad-109">Void türü.</span><span class="sxs-lookup"><span data-stu-id="07fad-109">A void type.</span></span>|  
|`ELEMENT_TYPE_BOOLEAN`|<span data-ttu-id="07fad-110">Bir Boolean türü</span><span class="sxs-lookup"><span data-stu-id="07fad-110">A Boolean type</span></span>|  
|`ELEMENT_TYPE_CHAR`|<span data-ttu-id="07fad-111">Bir karakter türü.</span><span class="sxs-lookup"><span data-stu-id="07fad-111">A character type.</span></span>|  
|`ELEMENT_TYPE_I1`|<span data-ttu-id="07fad-112">İmzalı bir 1 baytlık tamsayı.</span><span class="sxs-lookup"><span data-stu-id="07fad-112">A signed 1-byte integer.</span></span>|  
|`ELEMENT_TYPE_U1`|<span data-ttu-id="07fad-113">İşaretsiz bir 1 baytlık tamsayı.</span><span class="sxs-lookup"><span data-stu-id="07fad-113">An unsigned 1-byte integer.</span></span>|  
|`ELEMENT_TYPE_I2`|<span data-ttu-id="07fad-114">İmzalı bir 2-bayt tamsayı.</span><span class="sxs-lookup"><span data-stu-id="07fad-114">A signed 2-byte integer.</span></span>|  
|`ELEMENT_TYPE_U2`|<span data-ttu-id="07fad-115">İmzalanmamış 2-bayt tamsayı.</span><span class="sxs-lookup"><span data-stu-id="07fad-115">An unsigned 2-byte integer.</span></span>|  
|`ELEMENT_TYPE_I4`|<span data-ttu-id="07fad-116">İmzalı bir 4 baytlık tamsayı.</span><span class="sxs-lookup"><span data-stu-id="07fad-116">A signed 4-byte integer.</span></span>|  
|`ELEMENT_TYPE_U4`|<span data-ttu-id="07fad-117">İşaretsiz bir 4 baytlık tamsayı.</span><span class="sxs-lookup"><span data-stu-id="07fad-117">An unsigned 4-byte integer.</span></span>|  
|`ELEMENT_TYPE_I8`|<span data-ttu-id="07fad-118">İşaretli 8-bayt tamsayı.</span><span class="sxs-lookup"><span data-stu-id="07fad-118">A signed 8-byte integer.</span></span>|  
|`ELEMENT_TYPE_U8`|<span data-ttu-id="07fad-119">İmzalanmamış 8-bayt tamsayı.</span><span class="sxs-lookup"><span data-stu-id="07fad-119">An unsigned 8-byte integer.</span></span>|  
|`ELEMENT_TYPE_R4`|<span data-ttu-id="07fad-120">4-bayt kayan nokta.</span><span class="sxs-lookup"><span data-stu-id="07fad-120">A 4-byte floating point.</span></span>|  
|`ELEMENT_TYPE_R8`|<span data-ttu-id="07fad-121">Bir 8-bayt kayan nokta.</span><span class="sxs-lookup"><span data-stu-id="07fad-121">An 8-byte floating point.</span></span>|  
|`ELEMENT_TYPE_STRING`|<span data-ttu-id="07fad-122">System.String türü.</span><span class="sxs-lookup"><span data-stu-id="07fad-122">A System.String type.</span></span>|  
|`ELEMENT_TYPE_PTR`|<span data-ttu-id="07fad-123">Bir işaretçi türü değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="07fad-123">A pointer type modifier.</span></span>|  
|`ELEMENT_TYPE_BYREF`|<span data-ttu-id="07fad-124">Bir başvuru türü değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="07fad-124">A reference type modifier.</span></span>|  
|`ELEMENT_TYPE_VALUETYPE`|<span data-ttu-id="07fad-125">Değer tür değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="07fad-125">A value type modifier.</span></span>|  
|`ELEMENT_TYPE_CLASS`|<span data-ttu-id="07fad-126">Bir sınıf türü değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="07fad-126">A class type modifier.</span></span>|  
|`ELEMENT_TYPE_VAR`|<span data-ttu-id="07fad-127">Bir sınıf değişken tür değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="07fad-127">A class variable type modifier.</span></span>|  
|`ELEMENT_TYPE_ARRAY`|<span data-ttu-id="07fad-128">Çok boyutlu dizi tür değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="07fad-128">A multi-dimensional array type modifier.</span></span>|  
|`ELEMENT_TYPE_GENERICINST`|<span data-ttu-id="07fad-129">Genel türler için tür değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="07fad-129">A type modifier for generic types.</span></span>|  
|`ELEMENT_TYPE_TYPEDBYREF`|<span data-ttu-id="07fad-130">Belirlenmiş bir başvuru.</span><span class="sxs-lookup"><span data-stu-id="07fad-130">A typed reference.</span></span>|  
|`ELEMENT_TYPE_I`|<span data-ttu-id="07fad-131">Yerel bir tamsayı boyutu.</span><span class="sxs-lookup"><span data-stu-id="07fad-131">Size of a native integer.</span></span>|  
|`ELEMENT_TYPE_U`|<span data-ttu-id="07fad-132">Yerel bir işaretsiz tamsayı boyutu.</span><span class="sxs-lookup"><span data-stu-id="07fad-132">Size of an unsigned native integer.</span></span>|  
|`ELEMENT_TYPE_FNPTR`|<span data-ttu-id="07fad-133">Bir işlev işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="07fad-133">A pointer to a function.</span></span>|  
|`ELEMENT_TYPE_OBJECT`|<span data-ttu-id="07fad-134">System.Object türü.</span><span class="sxs-lookup"><span data-stu-id="07fad-134">A System.Object type.</span></span>|  
|`ELEMENT_TYPE_SZARRAY`|<span data-ttu-id="07fad-135">Tek boyutlu, sıfır alt sınırı dizi tür değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="07fad-135">A single-dimensional, zero lower-bound array type modifier.</span></span>|  
|`ELEMENT_TYPE_MVAR`|<span data-ttu-id="07fad-136">Bir yöntem değişken tür değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="07fad-136">A method variable type modifier.</span></span>|  
|`ELEMENT_TYPE_CMOD_REQD`|<span data-ttu-id="07fad-137">C dili değiştiricisi gereklidir.</span><span class="sxs-lookup"><span data-stu-id="07fad-137">A C language required modifier.</span></span>|  
|`ELEMENT_TYPE_CMOD_OPT`|<span data-ttu-id="07fad-138">Bir C dili isteğe bağlı bir değiştirici.</span><span class="sxs-lookup"><span data-stu-id="07fad-138">A C language optional modifier.</span></span>|  
|`ELEMENT_TYPE_INTERNAL`|<span data-ttu-id="07fad-139">Dahili olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="07fad-139">Used internally.</span></span>|  
|`ELEMENT_TYPE_MAX`|<span data-ttu-id="07fad-140">Geçersiz bir tür.</span><span class="sxs-lookup"><span data-stu-id="07fad-140">An invalid type.</span></span>|  
|`ELEMENT_TYPE_MODIFIER`|<span data-ttu-id="07fad-141">Dahili olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="07fad-141">Used internally.</span></span>|  
|`ELEMENT_TYPE_SENTINEL`|<span data-ttu-id="07fad-142">Değişken bir dizi parametre listesi için bir sentinel olan bir tür değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="07fad-142">A type modifier that is a sentinel for a list of a variable number of parameters.</span></span>|  
|`ELEMENT_TYPE_PINNED`|<span data-ttu-id="07fad-143">Dahili olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="07fad-143">Used internally.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="07fad-144">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="07fad-144">Remarks</span></span>  
 <span data-ttu-id="07fad-145">Tür değiştiricileri daha karmaşık türleri temsil eden temelini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="07fad-145">The type modifiers form the basis for representing more complex types.</span></span> <span data-ttu-id="07fad-146">A `CorElementType` tür değiştiricisi değeri, türü imzada hemen takip eden değerine uygulanır.</span><span class="sxs-lookup"><span data-stu-id="07fad-146">A `CorElementType` type modifier value is applied to the value that immediately follows it in the type signature.</span></span> <span data-ttu-id="07fad-147">Aşağıdaki değeri `CorElementType` tür değiştiricisi değeri olabilir bir `CorElementType` basit tür değeri, bir metaveri belirteci veya aşağıdaki tabloda belirtildiği gibi başka bir değer.</span><span class="sxs-lookup"><span data-stu-id="07fad-147">The value that follows the `CorElementType` type modifier value can be a `CorElementType` simple type value, a metadata token, or other value, as specified in the following table.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="07fad-148">Tüm sayılar (*numarası*, *bağımsız değişken sayısı*, *meta veri belirteci*, *derece*, *sayısı*ve *bağlı*) sıkıştırılmış tamsayı olarak depolanır.</span><span class="sxs-lookup"><span data-stu-id="07fad-148">All numbers (*number*, *argument Count*, *metadata token*, *rank*, *count*, and *bound*) are stored as compressed integers.</span></span> <span data-ttu-id="07fad-149">Bkz: [standart ECMA-335 - ortak dil altyapısı (CLI)](https://go.microsoft.com/fwlink/?LinkID=116487) ECMA Web sitesinde Ayrıntılar için.</span><span class="sxs-lookup"><span data-stu-id="07fad-149">See [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=116487) on the ECMA Web site for details.</span></span>  
  
|<span data-ttu-id="07fad-150">Tür değiştiricisi</span><span class="sxs-lookup"><span data-stu-id="07fad-150">Type modifier</span></span>|<span data-ttu-id="07fad-151">Biçimi</span><span class="sxs-lookup"><span data-stu-id="07fad-151">Format</span></span>|  
|-------------------|------------|  
|`ELEMENT_TYPE_PTR`|<span data-ttu-id="07fad-152">ELEMENT_TYPE_PTR < bir `CorElementType` değer ></span><span class="sxs-lookup"><span data-stu-id="07fad-152">ELEMENT_TYPE_PTR <a `CorElementType` value></span></span>|  
|`ELEMENT_TYPE_BYREF`|<span data-ttu-id="07fad-153">ELEMENT_TYPE_BYREF < bir `CorElementType` değer ></span><span class="sxs-lookup"><span data-stu-id="07fad-153">ELEMENT_TYPE_BYREF <a `CorElementType` value></span></span>|  
|`ELEMENT_TYPE_VALUETYPE`|<span data-ttu-id="07fad-154">ELEMENT_TYPE_VALUETYPE < bir `mdTypeDef` meta veri belirteci ></span><span class="sxs-lookup"><span data-stu-id="07fad-154">ELEMENT_TYPE_VALUETYPE <an `mdTypeDef` metadata token></span></span>|  
|`ELEMENT_TYPE_CLASS`|<span data-ttu-id="07fad-155">ELEMENT_TYPE_CLASS < bir `mdTypeDef` meta veri belirteci ></span><span class="sxs-lookup"><span data-stu-id="07fad-155">ELEMENT_TYPE_CLASS <an `mdTypeDef` metadata token></span></span>|  
|`ELEMENT_TYPE_VAR`|<span data-ttu-id="07fad-156">ELEMENT_TYPE_VAR \<sayı ></span><span class="sxs-lookup"><span data-stu-id="07fad-156">ELEMENT_TYPE_VAR \<number></span></span>|  
|`ELEMENT_TYPE_ARRAY`|<span data-ttu-id="07fad-157">ELEMENT_TYPE_ARRAY < bir `CorElementType` değer > \<derece > \<count1 > \<bound1 >... \<countN > \<boundN ></span><span class="sxs-lookup"><span data-stu-id="07fad-157">ELEMENT_TYPE_ARRAY <a `CorElementType` value> \<rank> \<count1> \<bound1> ... \<countN> \<boundN></span></span>|  
|`ELEMENT_TYPE_GENERICINST`|<span data-ttu-id="07fad-158">ELEMENT_TYPE_GENERICINST < bir `mdTypeDef` meta veri belirteci > \<bağımsız değişken sayısı > \<arg1 >... \<argN ></span><span class="sxs-lookup"><span data-stu-id="07fad-158">ELEMENT_TYPE_GENERICINST <an `mdTypeDef` metadata token> \<argument Count> \<arg1> ... \<argN></span></span>|  
|`ELEMENT_TYPE_FNPTR`|<span data-ttu-id="07fad-159">ELEMENT_TYPE_FNPTR \<çağırma kuralı dahil olmak üzere işlev için tam imza ></span><span class="sxs-lookup"><span data-stu-id="07fad-159">ELEMENT_TYPE_FNPTR \<complete signature for the function, including calling convention></span></span>|  
|`ELEMENT_TYPE_SZARRAY`|<span data-ttu-id="07fad-160">ELEMENT_TYPE_SZARRAY < bir `CorElementType` değer ></span><span class="sxs-lookup"><span data-stu-id="07fad-160">ELEMENT_TYPE_SZARRAY <a `CorElementType` value></span></span>|  
|`ELEMENT_TYPE_MVAR`|<span data-ttu-id="07fad-161">ELEMENT_TYPE_MVAR \<sayı ></span><span class="sxs-lookup"><span data-stu-id="07fad-161">ELEMENT_TYPE_MVAR \<number></span></span>|  
|`ELEMENT_TYPE_CMOD_REQD`|<span data-ttu-id="07fad-162">ELEMENT_TYPE_ < bir `mdTypeRef` veya `mdTypeDef` meta veri belirteci ></span><span class="sxs-lookup"><span data-stu-id="07fad-162">ELEMENT_TYPE_<a `mdTypeRef` or `mdTypeDef` metadata token></span></span>|  
|`ELEMENT_TYPE_CMOD_OPT`|<span data-ttu-id="07fad-163">E_T_CMOD_OPT < bir `mdTypeRef` veya `mdTypeDef` meta veri belirteci ></span><span class="sxs-lookup"><span data-stu-id="07fad-163">E_T_CMOD_OPT <a `mdTypeRef` or `mdTypeDef` metadata token></span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="07fad-164">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="07fad-164">Requirements</span></span>  
 <span data-ttu-id="07fad-165">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="07fad-165">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07fad-166">**Başlık:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="07fad-166">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="07fad-167">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07fad-167">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07fad-168">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="07fad-168">See Also</span></span>  
 [<span data-ttu-id="07fad-169">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="07fad-169">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
