---
title: CorElementType Enumeration1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorElementType
api_location: mscoree.dll
api_type: COM
f1_keywords: CorElementType
helpviewer_keywords: CorElementType enumeration [.NET Framework metadata]
ms.assetid: c3809c8f-1737-4f0f-9442-0c01ee689871
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8932e295aa1a6c6cf961e7b3a218e76984da02cb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="corelementtype-enumeration1"></a><span data-ttu-id="58569-102">CorElementType Enumeration1</span><span class="sxs-lookup"><span data-stu-id="58569-102">CorElementType Enumeration1</span></span>
<span data-ttu-id="58569-103">Ortak dil çalışma zamanı belirtir <xref:System.Type>, bir tür değiştiricisi ya da bir meta veri türü imzada türü hakkında bilgi.</span><span class="sxs-lookup"><span data-stu-id="58569-103">Specifies a common language runtime <xref:System.Type>, a type modifier, or information about a type in a metadata type signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58569-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="58569-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="58569-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="58569-105">Members</span></span>  
  
|<span data-ttu-id="58569-106">Üye</span><span class="sxs-lookup"><span data-stu-id="58569-106">Member</span></span>|<span data-ttu-id="58569-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="58569-107">Description</span></span>|  
|------------|-----------------|  
|`ELEMENT_TYPE_END`|<span data-ttu-id="58569-108">Dahili olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="58569-108">Used internally.</span></span>|  
|`ELEMENT_TYPE_VOID`|<span data-ttu-id="58569-109">Void türü.</span><span class="sxs-lookup"><span data-stu-id="58569-109">A void type.</span></span>|  
|`ELEMENT_TYPE_BOOLEAN`|<span data-ttu-id="58569-110">Bir Boolean türü</span><span class="sxs-lookup"><span data-stu-id="58569-110">A Boolean type</span></span>|  
|`ELEMENT_TYPE_CHAR`|<span data-ttu-id="58569-111">Bir karakter türü.</span><span class="sxs-lookup"><span data-stu-id="58569-111">A character type.</span></span>|  
|`ELEMENT_TYPE_I1`|<span data-ttu-id="58569-112">İmzalı bir 1-bayt tamsayı.</span><span class="sxs-lookup"><span data-stu-id="58569-112">A signed 1-byte integer.</span></span>|  
|`ELEMENT_TYPE_U1`|<span data-ttu-id="58569-113">İmzasız 1-bayt tamsayı.</span><span class="sxs-lookup"><span data-stu-id="58569-113">An unsigned 1-byte integer.</span></span>|  
|`ELEMENT_TYPE_I2`|<span data-ttu-id="58569-114">İmzalı bir 2-bayt tamsayı.</span><span class="sxs-lookup"><span data-stu-id="58569-114">A signed 2-byte integer.</span></span>|  
|`ELEMENT_TYPE_U2`|<span data-ttu-id="58569-115">İmzasız 2-bayt tamsayı.</span><span class="sxs-lookup"><span data-stu-id="58569-115">An unsigned 2-byte integer.</span></span>|  
|`ELEMENT_TYPE_I4`|<span data-ttu-id="58569-116">İmzalı bir 4-bayt tamsayı.</span><span class="sxs-lookup"><span data-stu-id="58569-116">A signed 4-byte integer.</span></span>|  
|`ELEMENT_TYPE_U4`|<span data-ttu-id="58569-117">İmzalanmamış 4-bayt tamsayı.</span><span class="sxs-lookup"><span data-stu-id="58569-117">An unsigned 4-byte integer.</span></span>|  
|`ELEMENT_TYPE_I8`|<span data-ttu-id="58569-118">İşaretli 8-bayt tamsayı.</span><span class="sxs-lookup"><span data-stu-id="58569-118">A signed 8-byte integer.</span></span>|  
|`ELEMENT_TYPE_U8`|<span data-ttu-id="58569-119">İmzalanmamış 8-bayt tamsayı.</span><span class="sxs-lookup"><span data-stu-id="58569-119">An unsigned 8-byte integer.</span></span>|  
|`ELEMENT_TYPE_R4`|<span data-ttu-id="58569-120">4-bayt kayan nokta.</span><span class="sxs-lookup"><span data-stu-id="58569-120">A 4-byte floating point.</span></span>|  
|`ELEMENT_TYPE_R8`|<span data-ttu-id="58569-121">Bir 8-bayt kayan nokta.</span><span class="sxs-lookup"><span data-stu-id="58569-121">An 8-byte floating point.</span></span>|  
|`ELEMENT_TYPE_STRING`|<span data-ttu-id="58569-122">System.String türü.</span><span class="sxs-lookup"><span data-stu-id="58569-122">A System.String type.</span></span>|  
|`ELEMENT_TYPE_PTR`|<span data-ttu-id="58569-123">İşaretçinin tür değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="58569-123">A pointer type modifier.</span></span>|  
|`ELEMENT_TYPE_BYREF`|<span data-ttu-id="58569-124">Bir başvuru türü değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="58569-124">A reference type modifier.</span></span>|  
|`ELEMENT_TYPE_VALUETYPE`|<span data-ttu-id="58569-125">Değer türü değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="58569-125">A value type modifier.</span></span>|  
|`ELEMENT_TYPE_CLASS`|<span data-ttu-id="58569-126">Sınıf türü değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="58569-126">A class type modifier.</span></span>|  
|`ELEMENT_TYPE_VAR`|<span data-ttu-id="58569-127">Bir sınıf değişken türü değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="58569-127">A class variable type modifier.</span></span>|  
|`ELEMENT_TYPE_ARRAY`|<span data-ttu-id="58569-128">Çok boyutlu bir dizi tür değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="58569-128">A multi-dimensional array type modifier.</span></span>|  
|`ELEMENT_TYPE_GENERICINST`|<span data-ttu-id="58569-129">Genel türler için bir tür değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="58569-129">A type modifier for generic types.</span></span>|  
|`ELEMENT_TYPE_TYPEDBYREF`|<span data-ttu-id="58569-130">Belirlenmiş bir başvuru.</span><span class="sxs-lookup"><span data-stu-id="58569-130">A typed reference.</span></span>|  
|`ELEMENT_TYPE_I`|<span data-ttu-id="58569-131">Yerel bir tamsayı cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="58569-131">Size of a native integer.</span></span>|  
|`ELEMENT_TYPE_U`|<span data-ttu-id="58569-132">Yerel bir işaretsiz tamsayı boyutu.</span><span class="sxs-lookup"><span data-stu-id="58569-132">Size of an unsigned native integer.</span></span>|  
|`ELEMENT_TYPE_FNPTR`|<span data-ttu-id="58569-133">Bir işlev işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="58569-133">A pointer to a function.</span></span>|  
|`ELEMENT_TYPE_OBJECT`|<span data-ttu-id="58569-134">System.Object türü.</span><span class="sxs-lookup"><span data-stu-id="58569-134">A System.Object type.</span></span>|  
|`ELEMENT_TYPE_SZARRAY`|<span data-ttu-id="58569-135">Tek boyutlu, sıfır alt sınır dizi tür değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="58569-135">A single-dimensional, zero lower-bound array type modifier.</span></span>|  
|`ELEMENT_TYPE_MVAR`|<span data-ttu-id="58569-136">Bir yöntem değişken türü değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="58569-136">A method variable type modifier.</span></span>|  
|`ELEMENT_TYPE_CMOD_REQD`|<span data-ttu-id="58569-137">C dili değiştiricisi gereklidir.</span><span class="sxs-lookup"><span data-stu-id="58569-137">A C language required modifier.</span></span>|  
|`ELEMENT_TYPE_CMOD_OPT`|<span data-ttu-id="58569-138">Bir C dil isteğe bağlı değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="58569-138">A C language optional modifier.</span></span>|  
|`ELEMENT_TYPE_INTERNAL`|<span data-ttu-id="58569-139">Dahili olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="58569-139">Used internally.</span></span>|  
|`ELEMENT_TYPE_MAX`|<span data-ttu-id="58569-140">Geçersiz bir tür.</span><span class="sxs-lookup"><span data-stu-id="58569-140">An invalid type.</span></span>|  
|`ELEMENT_TYPE_MODIFIER`|<span data-ttu-id="58569-141">Dahili olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="58569-141">Used internally.</span></span>|  
|`ELEMENT_TYPE_SENTINEL`|<span data-ttu-id="58569-142">Sentinel değişken bir dizi parametre listesi olan bir tür değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="58569-142">A type modifier that is a sentinel for a list of a variable number of parameters.</span></span>|  
|`ELEMENT_TYPE_PINNED`|<span data-ttu-id="58569-143">Dahili olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="58569-143">Used internally.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="58569-144">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="58569-144">Remarks</span></span>  
 <span data-ttu-id="58569-145">Türü değiştiricileri daha karmaşık türleri temsil eden temelini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="58569-145">The type modifiers form the basis for representing more complex types.</span></span> <span data-ttu-id="58569-146">A `CorElementType` tür değiştiricisi değeri hemen türü imzada izleyen değere uygulanır.</span><span class="sxs-lookup"><span data-stu-id="58569-146">A `CorElementType` type modifier value is applied to the value that immediately follows it in the type signature.</span></span> <span data-ttu-id="58569-147">Aşağıdaki değeri `CorElementType` tür değiştiricisi değeri olabilir bir `CorElementType` basit tür değeri, meta veri simgesi ya da aşağıdaki tabloda belirtildiği gibi başka bir değer.</span><span class="sxs-lookup"><span data-stu-id="58569-147">The value that follows the `CorElementType` type modifier value can be a `CorElementType` simple type value, a metadata token, or other value, as specified in the following table.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="58569-148">Tüm sayıları (*numarası*, *bağımsız değişken sayısı*, *meta veri simgesi*, *derece*, *sayısı*ve *bağlı*) sıkıştırılmış tamsayı olarak depolanır.</span><span class="sxs-lookup"><span data-stu-id="58569-148">All numbers (*number*, *argument Count*, *metadata token*, *rank*, *count*, and *bound*) are stored as compressed integers.</span></span> <span data-ttu-id="58569-149">Bkz: [standart ECMA-335 - ortak dil altyapısı (CLI)](http://go.microsoft.com/fwlink/?LinkID=116487) Ayrıntılar için ECMA Web sitesinde.</span><span class="sxs-lookup"><span data-stu-id="58569-149">See [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://go.microsoft.com/fwlink/?LinkID=116487) on the ECMA Web site for details.</span></span>  
  
|<span data-ttu-id="58569-150">Tür değiştiricisi</span><span class="sxs-lookup"><span data-stu-id="58569-150">Type modifier</span></span>|<span data-ttu-id="58569-151">Biçimi</span><span class="sxs-lookup"><span data-stu-id="58569-151">Format</span></span>|  
|-------------------|------------|  
|`ELEMENT_TYPE_PTR`|<span data-ttu-id="58569-152">ELEMENT_TYPE_PTR < bir `CorElementType` değer ></span><span class="sxs-lookup"><span data-stu-id="58569-152">ELEMENT_TYPE_PTR <a `CorElementType` value></span></span>|  
|`ELEMENT_TYPE_BYREF`|<span data-ttu-id="58569-153">ELEMENT_TYPE_BYREF < bir `CorElementType` değer ></span><span class="sxs-lookup"><span data-stu-id="58569-153">ELEMENT_TYPE_BYREF <a `CorElementType` value></span></span>|  
|`ELEMENT_TYPE_VALUETYPE`|<span data-ttu-id="58569-154">ELEMENT_TYPE_VALUETYPE < bir `mdTypeDef` meta veri simgesi ></span><span class="sxs-lookup"><span data-stu-id="58569-154">ELEMENT_TYPE_VALUETYPE <an `mdTypeDef` metadata token></span></span>|  
|`ELEMENT_TYPE_CLASS`|<span data-ttu-id="58569-155">ELEMENT_TYPE_CLASS < bir `mdTypeDef` meta veri simgesi ></span><span class="sxs-lookup"><span data-stu-id="58569-155">ELEMENT_TYPE_CLASS <an `mdTypeDef` metadata token></span></span>|  
|`ELEMENT_TYPE_VAR`|<span data-ttu-id="58569-156">ELEMENT_TYPE_VAR \<numarası ></span><span class="sxs-lookup"><span data-stu-id="58569-156">ELEMENT_TYPE_VAR \<number></span></span>|  
|`ELEMENT_TYPE_ARRAY`|<span data-ttu-id="58569-157">ELEMENT_TYPE_ARRAY < bir `CorElementType` değeri > \<derece > \<count1 > \<bound1 >... \<countN > \<boundN ></span><span class="sxs-lookup"><span data-stu-id="58569-157">ELEMENT_TYPE_ARRAY <a `CorElementType` value> \<rank> \<count1> \<bound1> ... \<countN> \<boundN></span></span>|  
|`ELEMENT_TYPE_GENERICINST`|<span data-ttu-id="58569-158">ELEMENT_TYPE_GENERICINST < bir `mdTypeDef` meta veri simgesi > \<bağımsız değişken sayısı > \<arg1 >... \<argN ></span><span class="sxs-lookup"><span data-stu-id="58569-158">ELEMENT_TYPE_GENERICINST <an `mdTypeDef` metadata token> \<argument Count> \<arg1> ... \<argN></span></span>|  
|`ELEMENT_TYPE_FNPTR`|<span data-ttu-id="58569-159">ELEMENT_TYPE_FNPTR \<çağırma dahil olmak üzere bu işlev için tam imza ></span><span class="sxs-lookup"><span data-stu-id="58569-159">ELEMENT_TYPE_FNPTR \<complete signature for the function, including calling convention></span></span>|  
|`ELEMENT_TYPE_SZARRAY`|<span data-ttu-id="58569-160">ELEMENT_TYPE_SZARRAY < bir `CorElementType` değer ></span><span class="sxs-lookup"><span data-stu-id="58569-160">ELEMENT_TYPE_SZARRAY <a `CorElementType` value></span></span>|  
|`ELEMENT_TYPE_MVAR`|<span data-ttu-id="58569-161">ELEMENT_TYPE_MVAR \<numarası ></span><span class="sxs-lookup"><span data-stu-id="58569-161">ELEMENT_TYPE_MVAR \<number></span></span>|  
|`ELEMENT_TYPE_CMOD_REQD`|<span data-ttu-id="58569-162">ELEMENT_TYPE_ < bir `mdTypeRef` veya `mdTypeDef` meta veri simgesi ></span><span class="sxs-lookup"><span data-stu-id="58569-162">ELEMENT_TYPE_<a `mdTypeRef` or `mdTypeDef` metadata token></span></span>|  
|`ELEMENT_TYPE_CMOD_OPT`|<span data-ttu-id="58569-163">E_T_CMOD_OPT < bir `mdTypeRef` veya `mdTypeDef` meta veri simgesi ></span><span class="sxs-lookup"><span data-stu-id="58569-163">E_T_CMOD_OPT <a `mdTypeRef` or `mdTypeDef` metadata token></span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="58569-164">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="58569-164">Requirements</span></span>  
 <span data-ttu-id="58569-165">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="58569-165">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58569-166">**Başlık:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="58569-166">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="58569-167">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58569-167">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58569-168">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="58569-168">See Also</span></span>  
 [<span data-ttu-id="58569-169">Meta veri numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="58569-169">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
