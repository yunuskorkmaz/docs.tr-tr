---
description: 'Daha fazla bilgi edinin: CorOpenFlags numaralandırması'
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
ms.openlocfilehash: b8bc31b5c2b7ff0c7984aa92c38e96569b80d22e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784307"
---
# <a name="coropenflags-enumeration"></a><span data-ttu-id="22598-103">CorOpenFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="22598-103">CorOpenFlags Enumeration</span></span>

<span data-ttu-id="22598-104">Bildirim dosyalarını açtıktan sonra meta veri davranışını denetleyen bayrak değerlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="22598-104">Contains flag values that control metadata behavior upon opening manifest files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22598-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="22598-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="22598-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="22598-106">Members</span></span>  
  
|<span data-ttu-id="22598-107">Üye</span><span class="sxs-lookup"><span data-stu-id="22598-107">Member</span></span>|<span data-ttu-id="22598-108">Description</span><span class="sxs-lookup"><span data-stu-id="22598-108">Description</span></span>|  
|------------|-----------------|  
|`ofRead`|<span data-ttu-id="22598-109">Dosyanın yalnızca okuma için açılması gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="22598-109">Indicates that the file should be opened for reading only.</span></span>|  
|`ofWrite`|<span data-ttu-id="22598-110">Dosyanın yazma için açılması gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="22598-110">Indicates that the file should be opened for writing.</span></span><br /><br /> <span data-ttu-id="22598-111">`ofWrite`Bir. winmd dosyasını açarken bayrak kullanıyorsanız, bayrağını da geçirmeniz gerekir `ofNoTransform` .</span><span class="sxs-lookup"><span data-stu-id="22598-111">If you are using the `ofWrite` flag when opening a .winmd file, you should also pass the `ofNoTransform` flag.</span></span>|  
|`ofReadWriteMask`|<span data-ttu-id="22598-112">Okuma ve yazma için bir maske.</span><span class="sxs-lookup"><span data-stu-id="22598-112">A mask for reading and writing.</span></span>|  
|`ofCopyMemory`|<span data-ttu-id="22598-113">Dosyanın belleğe okunup okunmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="22598-113">Indicates that the file should be read into memory.</span></span> <span data-ttu-id="22598-114">Meta veriler kendi kopyasını korumalıdır.</span><span class="sxs-lookup"><span data-stu-id="22598-114">Metadata should maintain its own copy.</span></span>|  
|`ofCacheImage`|<span data-ttu-id="22598-115">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="22598-115">Obsolete.</span></span> <span data-ttu-id="22598-116">Bu bayrak yoksayıldı.</span><span class="sxs-lookup"><span data-stu-id="22598-116">This flag is ignored.</span></span>|  
|`ofManifestMetadata`|<span data-ttu-id="22598-117">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="22598-117">Obsolete.</span></span> <span data-ttu-id="22598-118">Bu bayrak yoksayıldı.</span><span class="sxs-lookup"><span data-stu-id="22598-118">This flag is ignored.</span></span>|  
|`ofReadOnly`|<span data-ttu-id="22598-119">Dosyanın okuma için açılması gerektiğini ve bir `QueryInterface` [ımetadatayayın](imetadataemit-interface.md) çağrısı yapılamıyor olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="22598-119">Indicates that the file should be opened for reading, and that a call to `QueryInterface` for an [IMetaDataEmit](imetadataemit-interface.md) cannot be made.</span></span>|  
|`ofTakeOwnership`|<span data-ttu-id="22598-120">Belleğin [CoTaskMemAlloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemalloc) çağrısı kullanılarak ayrıldığını belirtir ve meta veriler tarafından serbest bırakılır.</span><span class="sxs-lookup"><span data-stu-id="22598-120">Indicates that the memory was allocated using a call to [CoTaskMemAlloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemalloc) and will be freed by the metadata.</span></span>|  
|`ofNoTypeLib`|<span data-ttu-id="22598-121">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="22598-121">Obsolete.</span></span> <span data-ttu-id="22598-122">Bu bayrak yoksayıldı.</span><span class="sxs-lookup"><span data-stu-id="22598-122">This flag is ignored.</span></span>|  
|`ofNoTransform`|<span data-ttu-id="22598-123">. Winmd dosyalarının otomatik dönüştürmesinin devre dışı bırakılacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="22598-123">Indicates that automatic transforms of .winmd files should be disabled.</span></span> <span data-ttu-id="22598-124">Diğer bir deyişle, bir Windows Çalışma Zamanı türünün .NET Framework türüne projeksiyonu devre dışı bırakılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="22598-124">In other words, the projection of a Windows Runtime type to a .NET Framework type should be disabled.</span></span> <span data-ttu-id="22598-125">Daha fazla bilgi için bkz. [.net ve Windows çalışma zamanı ile birlikte Windows çalışma zamanı ve clr](/archive/msdn-magazine/2012/windows-8-special-issue/windows-runtime-and-the-clr-underneath-the-hood-with-net-and-the-windows-runtime).</span><span class="sxs-lookup"><span data-stu-id="22598-125">For more information, see [Windows Runtime and the CLR - Underneath the Hood with .NET and the Windows Runtime](/archive/msdn-magazine/2012/windows-8-special-issue/windows-runtime-and-the-clr-underneath-the-hood-with-net-and-the-windows-runtime).</span></span>|  
|`ofReserved1`|<span data-ttu-id="22598-126">Dahili kullanım için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="22598-126">Reserved for internal use.</span></span>|  
|`ofReserved2`|<span data-ttu-id="22598-127">Dahili kullanım için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="22598-127">Reserved for internal use.</span></span>|  
|`ofReserved`|<span data-ttu-id="22598-128">Dahili kullanım için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="22598-128">Reserved for internal use.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="22598-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="22598-129">Requirements</span></span>  

 <span data-ttu-id="22598-130">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="22598-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22598-131">**Üst bilgi:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="22598-131">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="22598-132">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22598-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22598-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="22598-133">See also</span></span>

- [<span data-ttu-id="22598-134">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="22598-134">Metadata Enumerations</span></span>](metadata-enumerations.md)
