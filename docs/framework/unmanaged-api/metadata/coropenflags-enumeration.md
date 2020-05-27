---
title: CorOpenFlags Numaralandırması
ms.date: 03/30/2017
api_name:
- CorOpenFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorOpenFlags
helpviewer_keywords:
- CorOpenFlags enumeration [.NET Framework metadata]
ms.assetid: e27a83b5-2698-4996-9032-1e0fed8b91ca
topic_type:
- apiref
ms.openlocfilehash: 7318a7ea3eb1ddb047a799e58ebdfd9ce6cd76d1
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007591"
---
# <a name="coropenflags-enumeration"></a><span data-ttu-id="11e03-102">CorOpenFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="11e03-102">CorOpenFlags Enumeration</span></span>
<span data-ttu-id="11e03-103">Bildirim dosyalarını açtıktan sonra meta veri davranışını denetleyen bayrak değerlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="11e03-103">Contains flag values that control metadata behavior upon opening manifest files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11e03-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="11e03-104">Syntax</span></span>  
  
```cpp  
typedef enum CorOpenFlags  
{  
    ofRead              =   0x00000000,  
    ofWrite             =   0x00000001,  
    ofReadWriteMask     =   0x00000001,  
    ofCopyMemory        =   0x00000002,  
    ofCacheImage        =   0x00000004,  
    ofManifestMetadata  =   0x00000008,  
    ofReadOnly          =   0x00000010,  
    ofTakeOwnership     =   0x00000020,  
    ofCacheImage        =   0x00000004,  
    ofNoTypeLib         =   0x00000080,  
    ofNoTransform       =   0x00001000,  
    ofReserved1         =   0x00000100,  
    ofReserved2         =   0x00000200,  
    ofReserved          =   0xffffff40  
} CorOpenFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="11e03-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="11e03-105">Members</span></span>  
  
|<span data-ttu-id="11e03-106">Üye</span><span class="sxs-lookup"><span data-stu-id="11e03-106">Member</span></span>|<span data-ttu-id="11e03-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="11e03-107">Description</span></span>|  
|------------|-----------------|  
|`ofRead`|<span data-ttu-id="11e03-108">Dosyanın yalnızca okuma için açılması gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="11e03-108">Indicates that the file should be opened for reading only.</span></span>|  
|`ofWrite`|<span data-ttu-id="11e03-109">Dosyanın yazma için açılması gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="11e03-109">Indicates that the file should be opened for writing.</span></span><br /><br /> <span data-ttu-id="11e03-110">`ofWrite`Bir. winmd dosyasını açarken bayrak kullanıyorsanız, bayrağını da geçirmeniz gerekir `ofNoTransform` .</span><span class="sxs-lookup"><span data-stu-id="11e03-110">If you are using the `ofWrite` flag when opening a .winmd file, you should also pass the `ofNoTransform` flag.</span></span>|  
|`ofReadWriteMask`|<span data-ttu-id="11e03-111">Okuma ve yazma için bir maske.</span><span class="sxs-lookup"><span data-stu-id="11e03-111">A mask for reading and writing.</span></span>|  
|`ofCopyMemory`|<span data-ttu-id="11e03-112">Dosyanın belleğe okunup okunmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="11e03-112">Indicates that the file should be read into memory.</span></span> <span data-ttu-id="11e03-113">Meta veriler kendi kopyasını korumalıdır.</span><span class="sxs-lookup"><span data-stu-id="11e03-113">Metadata should maintain its own copy.</span></span>|  
|`ofCacheImage`|<span data-ttu-id="11e03-114">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="11e03-114">Obsolete.</span></span> <span data-ttu-id="11e03-115">Bu bayrak yoksayıldı.</span><span class="sxs-lookup"><span data-stu-id="11e03-115">This flag is ignored.</span></span>|  
|`ofManifestMetadata`|<span data-ttu-id="11e03-116">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="11e03-116">Obsolete.</span></span> <span data-ttu-id="11e03-117">Bu bayrak yoksayıldı.</span><span class="sxs-lookup"><span data-stu-id="11e03-117">This flag is ignored.</span></span>|  
|`ofReadOnly`|<span data-ttu-id="11e03-118">Dosyanın okuma için açılması gerektiğini ve bir `QueryInterface` [ımetadatayayın](imetadataemit-interface.md) çağrısı yapılamıyor olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="11e03-118">Indicates that the file should be opened for reading, and that a call to `QueryInterface` for an [IMetaDataEmit](imetadataemit-interface.md) cannot be made.</span></span>|  
|`ofTakeOwnership`|<span data-ttu-id="11e03-119">Belleğin [CoTaskMemAlloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemalloc) çağrısı kullanılarak ayrıldığını belirtir ve meta veriler tarafından serbest bırakılır.</span><span class="sxs-lookup"><span data-stu-id="11e03-119">Indicates that the memory was allocated using a call to [CoTaskMemAlloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemalloc) and will be freed by the metadata.</span></span>|  
|`ofNoTypeLib`|<span data-ttu-id="11e03-120">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="11e03-120">Obsolete.</span></span> <span data-ttu-id="11e03-121">Bu bayrak yoksayıldı.</span><span class="sxs-lookup"><span data-stu-id="11e03-121">This flag is ignored.</span></span>|  
|`ofNoTransform`|<span data-ttu-id="11e03-122">. Winmd dosyalarının otomatik dönüştürmesinin devre dışı bırakılacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="11e03-122">Indicates that automatic transforms of .winmd files should be disabled.</span></span> <span data-ttu-id="11e03-123">Diğer bir deyişle, bir Windows Çalışma Zamanı türünün .NET Framework türüne projeksiyonu devre dışı bırakılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="11e03-123">In other words, the projection of a Windows Runtime type to a .NET Framework type should be disabled.</span></span> <span data-ttu-id="11e03-124">Daha fazla bilgi için bkz. [.net ve Windows çalışma zamanı ile birlikte Windows çalışma zamanı ve clr](https://docs.microsoft.com/archive/msdn-magazine/2012/windows-8-special-issue/windows-runtime-and-the-clr-underneath-the-hood-with-net-and-the-windows-runtime).</span><span class="sxs-lookup"><span data-stu-id="11e03-124">For more information, see [Windows Runtime and the CLR - Underneath the Hood with .NET and the Windows Runtime](https://docs.microsoft.com/archive/msdn-magazine/2012/windows-8-special-issue/windows-runtime-and-the-clr-underneath-the-hood-with-net-and-the-windows-runtime).</span></span>|  
|`ofReserved1`|<span data-ttu-id="11e03-125">Dahili kullanım için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="11e03-125">Reserved for internal use.</span></span>|  
|`ofReserved2`|<span data-ttu-id="11e03-126">Dahili kullanım için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="11e03-126">Reserved for internal use.</span></span>|  
|`ofReserved`|<span data-ttu-id="11e03-127">Dahili kullanım için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="11e03-127">Reserved for internal use.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="11e03-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="11e03-128">Requirements</span></span>  
 <span data-ttu-id="11e03-129">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11e03-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11e03-130">**Üst bilgi:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="11e03-130">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="11e03-131">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11e03-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11e03-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="11e03-132">See also</span></span>

- [<span data-ttu-id="11e03-133">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="11e03-133">Metadata Enumerations</span></span>](metadata-enumerations.md)
