---
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 846c754aeb0a710fa70e906e666f694eaa77c576
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781705"
---
# <a name="cornativetype-enumeration"></a><span data-ttu-id="23918-102">CorNativeType Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="23918-102">CorNativeType Enumeration</span></span>
<span data-ttu-id="23918-103">Yönetilmeyen yerel türleri açıklayan değerlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="23918-103">Contains values that describe native unmanaged types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23918-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="23918-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="23918-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="23918-105">Members</span></span>  
  
|<span data-ttu-id="23918-106">Üye</span><span class="sxs-lookup"><span data-stu-id="23918-106">Member</span></span>|<span data-ttu-id="23918-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="23918-107">Description</span></span>|  
|------------|-----------------|  
|`NATIVE_TYPE_END`|<span data-ttu-id="23918-108">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="23918-108">Obsolete.</span></span>|  
|`NATIVE_TYPE_VOID`|<span data-ttu-id="23918-109">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="23918-109">Obsolete.</span></span>|  
|`NATIVE_TYPE_BOOLEAN`|<span data-ttu-id="23918-110">TRUE sıfır olmayan ve FALSE olduğu bir 4 baytlık Boole değeri sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="23918-110">A 4-byte Boolean value, where TRUE is non-zero and FALSE is zero.</span></span>|  
|`NATIVE_TYPE_I1`|<span data-ttu-id="23918-111">Bir işaretli 8 bit tam sayı değeri.</span><span class="sxs-lookup"><span data-stu-id="23918-111">A signed 8-bit integer value.</span></span>|  
|`NATIVE_TYPE_U1`|<span data-ttu-id="23918-112">İmzalanmamış 8 bit tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="23918-112">An unsigned 8-bit integer value.</span></span>|  
|`NATIVE_TYPE_I2`|<span data-ttu-id="23918-113">Bir 16 bitlik işaretli tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="23918-113">A signed 16-bit integer value.</span></span>|  
|`NATIVE_TYPE_U2`|<span data-ttu-id="23918-114">Bir 16 bitlik işaretsiz tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="23918-114">An unsigned 16-bit integer value.</span></span>|  
|`NATIVE_TYPE_I4`|<span data-ttu-id="23918-115">Bir işaretli 32-bit tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="23918-115">A signed 32-bit integer value.</span></span>|  
|`NATIVE_TYPE_U4`|<span data-ttu-id="23918-116">Bir işaretsiz 32-bit tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="23918-116">An unsigned 32-bit integer value.</span></span>|  
|`NATIVE_TYPE_I8`|<span data-ttu-id="23918-117">Bir 64-bit işaretli tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="23918-117">A signed 64-bit integer value.</span></span>|  
|`NATIVE_TYPE_U8`|<span data-ttu-id="23918-118">İşaretsiz 64-bit tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="23918-118">An unsigned 64-bit integer value.</span></span>|  
|`NATIVE_TYPE_R4`|<span data-ttu-id="23918-119">4-bayt kayan nokta sayısal bir değer.</span><span class="sxs-lookup"><span data-stu-id="23918-119">A 4-byte floating-point numeric value.</span></span>|  
|`NATIVE_TYPE_R8`|<span data-ttu-id="23918-120">Bir 8-bayt kayan nokta sayısal değer.</span><span class="sxs-lookup"><span data-stu-id="23918-120">An 8-byte floating-point numeric value.</span></span>|  
|`NATIVE_TYPE_SYSCHAR`|<span data-ttu-id="23918-121">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="23918-121">Obsolete.</span></span>|  
|`NATIVE_TYPE_VARIANT`|<span data-ttu-id="23918-122">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="23918-122">Obsolete.</span></span>|  
|`NATIVE_TYPE_CURRENCY`|<span data-ttu-id="23918-123">Yönetilen karşılık gelen sayısal bir COM tür <xref:System.Decimal> türü.</span><span class="sxs-lookup"><span data-stu-id="23918-123">A numeric COM type that corresponds to the managed <xref:System.Decimal> type.</span></span>|  
|`NATIVE_TYPE_PTR`|<span data-ttu-id="23918-124">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="23918-124">Obsolete.</span></span>|  
|`NATIVE_TYPE_DECIMAL`|<span data-ttu-id="23918-125">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="23918-125">Obsolete.</span></span>|  
|`NATIVE_TYPE_DATE`|<span data-ttu-id="23918-126">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="23918-126">Obsolete.</span></span>|  
|`NATIVE_TYPE_BSTR`|<span data-ttu-id="23918-127">COM birlikte çalışma.</span><span class="sxs-lookup"><span data-stu-id="23918-127">COM Interop.</span></span>|  
|`NATIVE_TYPE_LPSTR`|<span data-ttu-id="23918-128">LPSTR dize değeri.</span><span class="sxs-lookup"><span data-stu-id="23918-128">An LPSTR string value.</span></span>|  
|`NATIVE_TYPE_LPWSTR`|<span data-ttu-id="23918-129">LPWSTR dize değeri.</span><span class="sxs-lookup"><span data-stu-id="23918-129">An LPWSTR string value.</span></span>|  
|`NATIVE_TYPE_LPTSTR`|<span data-ttu-id="23918-130">LPTSTR dize değeri.</span><span class="sxs-lookup"><span data-stu-id="23918-130">An LPTSTR string value.</span></span>|  
|`NATIVE_TYPE_FIXEDSYSSTRING`|<span data-ttu-id="23918-131">Sabit, sistem tarafından tanımlanan bir dize değeri.</span><span class="sxs-lookup"><span data-stu-id="23918-131">A fixed, system-defined string value.</span></span>|  
|`NATIVE_TYPE_OBJECTREF`|<span data-ttu-id="23918-132">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="23918-132">Obsolete.</span></span>|  
|`NATIVE_TYPE_IUNKNOWN`|<span data-ttu-id="23918-133">COM birlikte çalışma.</span><span class="sxs-lookup"><span data-stu-id="23918-133">COM Interop.</span></span>|  
|`NATIVE_TYPE_IDISPATCH`|<span data-ttu-id="23918-134">COM birlikte çalışma.</span><span class="sxs-lookup"><span data-stu-id="23918-134">COM Interop.</span></span>|  
|`NATIVE_TYPE_STRUCT`|<span data-ttu-id="23918-135">Bir yerel yapısı değeri.</span><span class="sxs-lookup"><span data-stu-id="23918-135">A native structure value.</span></span>|  
|`NATIVE_TYPE_INTF`|<span data-ttu-id="23918-136">COM birlikte çalışma.</span><span class="sxs-lookup"><span data-stu-id="23918-136">COM Interop.</span></span>|  
|`NATIVE_TYPE_SAFEARRAY`|<span data-ttu-id="23918-137">COM birlikte çalışma.</span><span class="sxs-lookup"><span data-stu-id="23918-137">COM Interop.</span></span>|  
|`NATIVE_TYPE_FIXEDARRAY`|<span data-ttu-id="23918-138">Bir sabit uzunluklu dizi değeri.</span><span class="sxs-lookup"><span data-stu-id="23918-138">A fixed-length array value.</span></span>|  
|`NATIVE_TYPE_INT`|<span data-ttu-id="23918-139">Bir yerel 16 bitlik işaretli tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="23918-139">A native 16-bit signed integer value.</span></span>|  
|`NATIVE_TYPE_UINT`|<span data-ttu-id="23918-140">Bir yerel 16 bitlik işaretsiz tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="23918-140">A native 16-bit unsigned integer value.</span></span>|  
|`NATIVE_TYPE_NESTEDSTRUCT`|<span data-ttu-id="23918-141">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="23918-141">Obsolete.</span></span><br /><br /> <span data-ttu-id="23918-142">NATIVE_TYPE_STRUCT kullanın.</span><span class="sxs-lookup"><span data-stu-id="23918-142">Use NATIVE_TYPE_STRUCT.</span></span>|  
|`NATIVE_TYPE_BYVALSTR`|<span data-ttu-id="23918-143">COM birlikte çalışma.</span><span class="sxs-lookup"><span data-stu-id="23918-143">COM Interop.</span></span>|  
|`NATIVE_TYPE_ANSIBSTR`|<span data-ttu-id="23918-144">COM birlikte çalışma.</span><span class="sxs-lookup"><span data-stu-id="23918-144">COM Interop.</span></span>|  
|`NATIVE_TYPE_TBSTR`|<span data-ttu-id="23918-145">COM birlikte çalışma.</span><span class="sxs-lookup"><span data-stu-id="23918-145">COM Interop.</span></span><br /><br /> <span data-ttu-id="23918-146">BSTR veya ANSIBSTR platforma bağlı olarak seçin.</span><span class="sxs-lookup"><span data-stu-id="23918-146">Select BSTR or ANSIBSTR depending on the platform.</span></span>|  
|`NATIVE_TYPE_VARIANTBOOL`|<span data-ttu-id="23918-147">Burada doğru -1 ve sıfırsa yanlış bir 2 baytlık Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="23918-147">A 2-byte Boolean value, where TRUE is -1 and FALSE is zero.</span></span>|  
|`NATIVE_TYPE_FUNC`|<span data-ttu-id="23918-148">Bir işlev işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="23918-148">A function pointer.</span></span>|  
|`NATIVE_TYPE_ASANY`|<span data-ttu-id="23918-149">Herhangi bir yerel tür referansı.</span><span class="sxs-lookup"><span data-stu-id="23918-149">A reference to any native type.</span></span>|  
|`NATIVE_TYPE_ARRAY`|<span data-ttu-id="23918-150">Belirtilmeyen bir türün üyeleri olan bir dizi bir başvuru.</span><span class="sxs-lookup"><span data-stu-id="23918-150">A reference to an array with members of an unspecified type.</span></span>|  
|`NATIVE_TYPE_LPSTRUCT`|<span data-ttu-id="23918-151">Yapı bir 32-bit tamsayı işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="23918-151">A 32-bit integer pointer to a structure.</span></span>|  
|`NATIVE_TYPE_CUSTOMMARSHALER`|<span data-ttu-id="23918-152">Özel bir Sıralayıcı yerel bir tür.</span><span class="sxs-lookup"><span data-stu-id="23918-152">A custom marshaler native type.</span></span><br /><br /> <span data-ttu-id="23918-153">Bu, aşağıdaki biçimde bir dize tarafından izlenen gerekir: "Yerel tür adı/0Custom Sıralayıcı tür adı/0Optional tanımlama bilgisi/0" veya "{yerel türü GUID'i} / 0Custom sıralayıcı türü adı/0Optional tanımlama bilgisi/0"</span><span class="sxs-lookup"><span data-stu-id="23918-153">This must be followed by a string of the following format: "Native type name/0Custom marshaler type name/0Optional cookie/0" or "{Native type GUID}/0Custom marshaler type name/0Optional cookie/0"</span></span>|  
|`NATIVE_TYPE_ERROR`|<span data-ttu-id="23918-154">COM birlikte çalışma.</span><span class="sxs-lookup"><span data-stu-id="23918-154">COM Interop.</span></span><br /><br /> <span data-ttu-id="23918-155">ELEMENT_TYPE_I4 ile bu tür için VT_HRESULT eşler.</span><span class="sxs-lookup"><span data-stu-id="23918-155">With ELEMENT_TYPE_I4 this type maps to VT_HRESULT.</span></span>|  
|`NATIVE_TYPE_IINSPECTABLE`|<span data-ttu-id="23918-156">Yerel `IInspectable` türü.</span><span class="sxs-lookup"><span data-stu-id="23918-156">A native `IInspectable` type.</span></span>|  
|`NATIVE_TYPE_HSTRING`|<span data-ttu-id="23918-157">Yerel `HString`.</span><span class="sxs-lookup"><span data-stu-id="23918-157">A native `HString`.</span></span>|  
|`NATIVE_TYPE_MAX`|<span data-ttu-id="23918-158">Geçersiz bir değer.</span><span class="sxs-lookup"><span data-stu-id="23918-158">An invalid value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="23918-159">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="23918-159">Requirements</span></span>  
 <span data-ttu-id="23918-160">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="23918-160">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23918-161">**Üst bilgi:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="23918-161">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="23918-162">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23918-162">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23918-163">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="23918-163">See also</span></span>

- <xref:System.Runtime.InteropServices.UnmanagedType>
- [<span data-ttu-id="23918-164">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="23918-164">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
