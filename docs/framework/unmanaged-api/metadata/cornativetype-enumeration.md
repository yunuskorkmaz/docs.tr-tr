---
description: 'Hakkında daha fazla bilgi edinin: CorNativeType numaralandırması'
title: CorNativeType Numaralandırması
ms.date: 03/30/2017
api_name:
- CorNativeType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorNativeType
helpviewer_keywords:
- CorNativeType enumeration [.NET Framework metadata]
ms.assetid: e47a72f1-9609-48ed-bb34-97170d7f6890
topic_type:
- apiref
ms.openlocfilehash: d2313eef124f3308c4792b47da8b7c8bba984597
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784333"
---
# <a name="cornativetype-enumeration"></a><span data-ttu-id="481a9-103">CorNativeType Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="481a9-103">CorNativeType Enumeration</span></span>

<span data-ttu-id="481a9-104">Yerel yönetilmeyen türleri tanımlayan değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="481a9-104">Contains values that describe native unmanaged types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="481a9-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="481a9-105">Syntax</span></span>  
  
```cpp  
typedef enum CorNativeType {  
  
    NATIVE_TYPE_END                  = 0x0,  
    NATIVE_TYPE_VOID                 = 0x1,  
    NATIVE_TYPE_BOOLEAN              = 0x2,  
    NATIVE_TYPE_I1                   = 0x3,  
    NATIVE_TYPE_U1                   = 0x4,  
    NATIVE_TYPE_I2                   = 0x5,  
    NATIVE_TYPE_U2                   = 0x6,  
    NATIVE_TYPE_I4                   = 0x7,  
    NATIVE_TYPE_U4                   = 0x8,  
    NATIVE_TYPE_I8                   = 0x9,  
    NATIVE_TYPE_U8                   = 0xa,  
    NATIVE_TYPE_R4                   = 0xb,  
    NATIVE_TYPE_R8                   = 0xc,  
    NATIVE_TYPE_SYSCHAR              = 0xd,  
    NATIVE_TYPE_VARIANT              = 0xe,  
    NATIVE_TYPE_CURRENCY             = 0xf,  
    NATIVE_TYPE_PTR                  = 0x10,  
  
    NATIVE_TYPE_DECIMAL              = 0x11,  
    NATIVE_TYPE_DATE                 = 0x12,  
    NATIVE_TYPE_BSTR                 = 0x13,  
    NATIVE_TYPE_LPSTR                = 0x14,  
    NATIVE_TYPE_LPWSTR               = 0x15,  
    NATIVE_TYPE_LPTSTR               = 0x16,  
    NATIVE_TYPE_FIXEDSYSSTRING       = 0x17,  
    NATIVE_TYPE_OBJECTREF            = 0x18,  
    NATIVE_TYPE_IUNKNOWN             = 0x19,  
    NATIVE_TYPE_IDISPATCH            = 0x1a,  
    NATIVE_TYPE_STRUCT               = 0x1b,  
    NATIVE_TYPE_INTF                 = 0x1c,  
    NATIVE_TYPE_SAFEARRAY            = 0x1d,  
    NATIVE_TYPE_FIXEDARRAY           = 0x1e,  
    NATIVE_TYPE_INT                  = 0x1f,  
    NATIVE_TYPE_UINT                 = 0x20,  
  
    NATIVE_TYPE_NESTEDSTRUCT         = 0x21,  
    NATIVE_TYPE_BYVALSTR             = 0x22,  
    NATIVE_TYPE_ANSIBSTR             = 0x23,  
    NATIVE_TYPE_TBSTR                = 0x24,  
    NATIVE_TYPE_VARIANTBOOL          = 0x25,  
    NATIVE_TYPE_FUNC                 = 0x26,  
  
    NATIVE_TYPE_ASANY                = 0x28,  
    NATIVE_TYPE_ARRAY                = 0x2a,  
    NATIVE_TYPE_LPSTRUCT             = 0x2b,  
    NATIVE_TYPE_CUSTOMMARSHALER      = 0x2c,  
    NATIVE_TYPE_IINSPECTABLE         = 0x2e,  
    NATIVE_TYPE_HSTRING              = 0x2f,  
  
    NATIVE_TYPE_ERROR                = 0x2d,
  
    NATIVE_TYPE_MAX                  = 0x50  
  
} CorNativeType;  
```  
  
## <a name="members"></a><span data-ttu-id="481a9-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="481a9-106">Members</span></span>  
  
|<span data-ttu-id="481a9-107">Üye</span><span class="sxs-lookup"><span data-stu-id="481a9-107">Member</span></span>|<span data-ttu-id="481a9-108">Description</span><span class="sxs-lookup"><span data-stu-id="481a9-108">Description</span></span>|  
|------------|-----------------|  
|`NATIVE_TYPE_END`|<span data-ttu-id="481a9-109">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="481a9-109">Obsolete.</span></span>|  
|`NATIVE_TYPE_VOID`|<span data-ttu-id="481a9-110">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="481a9-110">Obsolete.</span></span>|  
|`NATIVE_TYPE_BOOLEAN`|<span data-ttu-id="481a9-111">Bir 4 baytlık Boole değeri, TRUE sıfır değil ve FALSE sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="481a9-111">A 4-byte Boolean value, where TRUE is non-zero and FALSE is zero.</span></span>|  
|`NATIVE_TYPE_I1`|<span data-ttu-id="481a9-112">İşaretli 8 bit tam sayı değeri.</span><span class="sxs-lookup"><span data-stu-id="481a9-112">A signed 8-bit integer value.</span></span>|  
|`NATIVE_TYPE_U1`|<span data-ttu-id="481a9-113">İşaretsiz 8 bit tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="481a9-113">An unsigned 8-bit integer value.</span></span>|  
|`NATIVE_TYPE_I2`|<span data-ttu-id="481a9-114">İşaretli 16 bit tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="481a9-114">A signed 16-bit integer value.</span></span>|  
|`NATIVE_TYPE_U2`|<span data-ttu-id="481a9-115">İşaretsiz 16 bit tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="481a9-115">An unsigned 16-bit integer value.</span></span>|  
|`NATIVE_TYPE_I4`|<span data-ttu-id="481a9-116">İmzalı 32 bitlik bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="481a9-116">A signed 32-bit integer value.</span></span>|  
|`NATIVE_TYPE_U4`|<span data-ttu-id="481a9-117">İşaretsiz 32 bitlik bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="481a9-117">An unsigned 32-bit integer value.</span></span>|  
|`NATIVE_TYPE_I8`|<span data-ttu-id="481a9-118">İmzalı 64 bitlik bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="481a9-118">A signed 64-bit integer value.</span></span>|  
|`NATIVE_TYPE_U8`|<span data-ttu-id="481a9-119">İşaretsiz 64 bitlik bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="481a9-119">An unsigned 64-bit integer value.</span></span>|  
|`NATIVE_TYPE_R4`|<span data-ttu-id="481a9-120">4 baytlık kayan nokta sayısal değeri.</span><span class="sxs-lookup"><span data-stu-id="481a9-120">A 4-byte floating-point numeric value.</span></span>|  
|`NATIVE_TYPE_R8`|<span data-ttu-id="481a9-121">8 baytlık kayan nokta sayısal değeri.</span><span class="sxs-lookup"><span data-stu-id="481a9-121">An 8-byte floating-point numeric value.</span></span>|  
|`NATIVE_TYPE_SYSCHAR`|<span data-ttu-id="481a9-122">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="481a9-122">Obsolete.</span></span>|  
|`NATIVE_TYPE_VARIANT`|<span data-ttu-id="481a9-123">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="481a9-123">Obsolete.</span></span>|  
|`NATIVE_TYPE_CURRENCY`|<span data-ttu-id="481a9-124">Yönetilen türe karşılık gelen sayısal COM türü <xref:System.Decimal> .</span><span class="sxs-lookup"><span data-stu-id="481a9-124">A numeric COM type that corresponds to the managed <xref:System.Decimal> type.</span></span>|  
|`NATIVE_TYPE_PTR`|<span data-ttu-id="481a9-125">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="481a9-125">Obsolete.</span></span>|  
|`NATIVE_TYPE_DECIMAL`|<span data-ttu-id="481a9-126">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="481a9-126">Obsolete.</span></span>|  
|`NATIVE_TYPE_DATE`|<span data-ttu-id="481a9-127">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="481a9-127">Obsolete.</span></span>|  
|`NATIVE_TYPE_BSTR`|<span data-ttu-id="481a9-128">COM birlikte çalışma.</span><span class="sxs-lookup"><span data-stu-id="481a9-128">COM Interop.</span></span>|  
|`NATIVE_TYPE_LPSTR`|<span data-ttu-id="481a9-129">LPSTR dize değeri.</span><span class="sxs-lookup"><span data-stu-id="481a9-129">An LPSTR string value.</span></span>|  
|`NATIVE_TYPE_LPWSTR`|<span data-ttu-id="481a9-130">LPWSTR dize değeri.</span><span class="sxs-lookup"><span data-stu-id="481a9-130">An LPWSTR string value.</span></span>|  
|`NATIVE_TYPE_LPTSTR`|<span data-ttu-id="481a9-131">LPTSTR dize değeri.</span><span class="sxs-lookup"><span data-stu-id="481a9-131">An LPTSTR string value.</span></span>|  
|`NATIVE_TYPE_FIXEDSYSSTRING`|<span data-ttu-id="481a9-132">Sabit, sistem tarafından tanımlanan bir dize değeri.</span><span class="sxs-lookup"><span data-stu-id="481a9-132">A fixed, system-defined string value.</span></span>|  
|`NATIVE_TYPE_OBJECTREF`|<span data-ttu-id="481a9-133">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="481a9-133">Obsolete.</span></span>|  
|`NATIVE_TYPE_IUNKNOWN`|<span data-ttu-id="481a9-134">COM birlikte çalışma.</span><span class="sxs-lookup"><span data-stu-id="481a9-134">COM Interop.</span></span>|  
|`NATIVE_TYPE_IDISPATCH`|<span data-ttu-id="481a9-135">COM birlikte çalışma.</span><span class="sxs-lookup"><span data-stu-id="481a9-135">COM Interop.</span></span>|  
|`NATIVE_TYPE_STRUCT`|<span data-ttu-id="481a9-136">Yerel bir yapı değeri.</span><span class="sxs-lookup"><span data-stu-id="481a9-136">A native structure value.</span></span>|  
|`NATIVE_TYPE_INTF`|<span data-ttu-id="481a9-137">COM birlikte çalışma.</span><span class="sxs-lookup"><span data-stu-id="481a9-137">COM Interop.</span></span>|  
|`NATIVE_TYPE_SAFEARRAY`|<span data-ttu-id="481a9-138">COM birlikte çalışma.</span><span class="sxs-lookup"><span data-stu-id="481a9-138">COM Interop.</span></span>|  
|`NATIVE_TYPE_FIXEDARRAY`|<span data-ttu-id="481a9-139">Sabit uzunluklu bir dizi değeri.</span><span class="sxs-lookup"><span data-stu-id="481a9-139">A fixed-length array value.</span></span>|  
|`NATIVE_TYPE_INT`|<span data-ttu-id="481a9-140">Yerel bir 16 bit işaretli tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="481a9-140">A native 16-bit signed integer value.</span></span>|  
|`NATIVE_TYPE_UINT`|<span data-ttu-id="481a9-141">Yerel bir 16 bit işaretsiz tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="481a9-141">A native 16-bit unsigned integer value.</span></span>|  
|`NATIVE_TYPE_NESTEDSTRUCT`|<span data-ttu-id="481a9-142">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="481a9-142">Obsolete.</span></span><br /><br /> <span data-ttu-id="481a9-143">NATIVE_TYPE_STRUCT kullanın.</span><span class="sxs-lookup"><span data-stu-id="481a9-143">Use NATIVE_TYPE_STRUCT.</span></span>|  
|`NATIVE_TYPE_BYVALSTR`|<span data-ttu-id="481a9-144">COM birlikte çalışma.</span><span class="sxs-lookup"><span data-stu-id="481a9-144">COM Interop.</span></span>|  
|`NATIVE_TYPE_ANSIBSTR`|<span data-ttu-id="481a9-145">COM birlikte çalışma.</span><span class="sxs-lookup"><span data-stu-id="481a9-145">COM Interop.</span></span>|  
|`NATIVE_TYPE_TBSTR`|<span data-ttu-id="481a9-146">COM birlikte çalışma.</span><span class="sxs-lookup"><span data-stu-id="481a9-146">COM Interop.</span></span><br /><br /> <span data-ttu-id="481a9-147">Platforma bağlı olarak BSTR veya ANSIBSTR seçin.</span><span class="sxs-lookup"><span data-stu-id="481a9-147">Select BSTR or ANSIBSTR depending on the platform.</span></span>|  
|`NATIVE_TYPE_VARIANTBOOL`|<span data-ttu-id="481a9-148">2 baytlık bir Boole değeri; burada TRUE-1 ve FALSE sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="481a9-148">A 2-byte Boolean value, where TRUE is -1 and FALSE is zero.</span></span>|  
|`NATIVE_TYPE_FUNC`|<span data-ttu-id="481a9-149">Bir işlev işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="481a9-149">A function pointer.</span></span>|  
|`NATIVE_TYPE_ASANY`|<span data-ttu-id="481a9-150">Herhangi bir yerel türe başvuru.</span><span class="sxs-lookup"><span data-stu-id="481a9-150">A reference to any native type.</span></span>|  
|`NATIVE_TYPE_ARRAY`|<span data-ttu-id="481a9-151">Belirtilmemiş bir türün üyeleri olan bir diziye başvuru.</span><span class="sxs-lookup"><span data-stu-id="481a9-151">A reference to an array with members of an unspecified type.</span></span>|  
|`NATIVE_TYPE_LPSTRUCT`|<span data-ttu-id="481a9-152">Bir yapıya 32 bitlik bir tamsayı işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="481a9-152">A 32-bit integer pointer to a structure.</span></span>|  
|`NATIVE_TYPE_CUSTOMMARSHALER`|<span data-ttu-id="481a9-153">Özel sıralayıcı yerel türü.</span><span class="sxs-lookup"><span data-stu-id="481a9-153">A custom marshaler native type.</span></span><br /><br /> <span data-ttu-id="481a9-154">Bu, arkasından aşağıdaki biçimdeki bir dize gelmelidir: "Yerel tür adı/0Özel Sıralayıcı türü name/0Optional Cookie/0" veya "{Native Type GUID}/0Özel Sıralayıcı türü ad/0Isteğe bağlı tanımlama bilgisi/0"</span><span class="sxs-lookup"><span data-stu-id="481a9-154">This must be followed by a string of the following format: "Native type name/0Custom marshaler type name/0Optional cookie/0" or "{Native type GUID}/0Custom marshaler type name/0Optional cookie/0"</span></span>|  
|`NATIVE_TYPE_ERROR`|<span data-ttu-id="481a9-155">COM birlikte çalışma.</span><span class="sxs-lookup"><span data-stu-id="481a9-155">COM Interop.</span></span><br /><br /> <span data-ttu-id="481a9-156">ELEMENT_TYPE_I4 bu tür VT_HRESULT eşlenir.</span><span class="sxs-lookup"><span data-stu-id="481a9-156">With ELEMENT_TYPE_I4 this type maps to VT_HRESULT.</span></span>|  
|`NATIVE_TYPE_IINSPECTABLE`|<span data-ttu-id="481a9-157">Yerel bir `IInspectable` tür.</span><span class="sxs-lookup"><span data-stu-id="481a9-157">A native `IInspectable` type.</span></span>|  
|`NATIVE_TYPE_HSTRING`|<span data-ttu-id="481a9-158">Yerel bir `HString` .</span><span class="sxs-lookup"><span data-stu-id="481a9-158">A native `HString`.</span></span>|  
|`NATIVE_TYPE_MAX`|<span data-ttu-id="481a9-159">Geçersiz bir değer.</span><span class="sxs-lookup"><span data-stu-id="481a9-159">An invalid value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="481a9-160">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="481a9-160">Requirements</span></span>  

 <span data-ttu-id="481a9-161">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="481a9-161">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="481a9-162">**Üst bilgi:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="481a9-162">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="481a9-163">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="481a9-163">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="481a9-164">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="481a9-164">See also</span></span>

- <xref:System.Runtime.InteropServices.UnmanagedType>
- [<span data-ttu-id="481a9-165">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="481a9-165">Metadata Enumerations</span></span>](metadata-enumerations.md)
