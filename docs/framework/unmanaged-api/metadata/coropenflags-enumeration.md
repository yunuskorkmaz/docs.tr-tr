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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c08b1f6be41de63886115e5aed6bcad901658bb5
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43509226"
---
# <a name="coropenflags-enumeration"></a><span data-ttu-id="40e61-102">CorOpenFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="40e61-102">CorOpenFlags Enumeration</span></span>
<span data-ttu-id="40e61-103">Bildirim dosyaları açma bağlı meta veri davranışını denetleyen bayrak değerlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="40e61-103">Contains flag values that control metadata behavior upon opening manifest files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40e61-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="40e61-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="40e61-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="40e61-105">Members</span></span>  
  
|<span data-ttu-id="40e61-106">Üye</span><span class="sxs-lookup"><span data-stu-id="40e61-106">Member</span></span>|<span data-ttu-id="40e61-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="40e61-107">Description</span></span>|  
|------------|-----------------|  
|`ofRead`|<span data-ttu-id="40e61-108">Yalnızca okumak için dosyanın açılması gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="40e61-108">Indicates that the file should be opened for reading only.</span></span>|  
|`ofWrite`|<span data-ttu-id="40e61-109">Dosya yazma için açılması gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="40e61-109">Indicates that the file should be opened for writing.</span></span><br /><br /> <span data-ttu-id="40e61-110">Kullanıyorsanız `ofWrite` ne zaman bayrağı da geçmesi bir .winmd dosyası açılırken, `ofNoTransform` bayrağı.</span><span class="sxs-lookup"><span data-stu-id="40e61-110">If you are using the `ofWrite` flag when opening a .winmd file, you should also pass the `ofNoTransform` flag.</span></span>|  
|`ofReadWriteMask`|<span data-ttu-id="40e61-111">Okuma ve yazma için bir maske.</span><span class="sxs-lookup"><span data-stu-id="40e61-111">A mask for reading and writing.</span></span>|  
|`ofCopyMemory`|<span data-ttu-id="40e61-112">Dosya belleğe okunmalıdır gösterir.</span><span class="sxs-lookup"><span data-stu-id="40e61-112">Indicates that the file should be read into memory.</span></span> <span data-ttu-id="40e61-113">Meta verileri kendi kopyalama korumanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="40e61-113">Metadata should maintain its own copy.</span></span>|  
|`ofCacheImage`|<span data-ttu-id="40e61-114">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="40e61-114">Obsolete.</span></span> <span data-ttu-id="40e61-115">Bu bayrak göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="40e61-115">This flag is ignored.</span></span>|  
|`ofManifestMetadata`|<span data-ttu-id="40e61-116">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="40e61-116">Obsolete.</span></span> <span data-ttu-id="40e61-117">Bu bayrak göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="40e61-117">This flag is ignored.</span></span>|  
|`ofReadOnly`|<span data-ttu-id="40e61-118">Okuma ve bu dosyanın açılması gerektiğini belirten bir çağrı `QueryInterface` için bir [Imetadataemit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) yapılamaz.</span><span class="sxs-lookup"><span data-stu-id="40e61-118">Indicates that the file should be opened for reading, and that a call to `QueryInterface` for an [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) cannot be made.</span></span>|  
|`ofTakeOwnership`|<span data-ttu-id="40e61-119">Bellek yapılan bir çağrı kullanılarak ayrıldı gösterir [CoTaskMemAlloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemalloc) ve meta verileri tarafından serbest bırakılacak.</span><span class="sxs-lookup"><span data-stu-id="40e61-119">Indicates that the memory was allocated using a call to [CoTaskMemAlloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemalloc) and will be freed by the metadata.</span></span>|  
|`ofNoTypeLib`|<span data-ttu-id="40e61-120">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="40e61-120">Obsolete.</span></span> <span data-ttu-id="40e61-121">Bu bayrak göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="40e61-121">This flag is ignored.</span></span>|  
|`ofNoTransform`|<span data-ttu-id="40e61-122">Otomatik dönüştürmeler .winmd dosyaları devre dışı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="40e61-122">Indicates that automatic transforms of .winmd files should be disabled.</span></span> <span data-ttu-id="40e61-123">Diğer bir deyişle, bir .NET Framework türü için bir Windows çalışma zamanı tür projeksiyonu devre dışı bırakılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="40e61-123">In other words, the projection of a Windows Runtime type to a .NET Framework type should be disabled.</span></span> <span data-ttu-id="40e61-124">Daha fazla bilgi için [altındaki Seçenekler .NET ve Windows çalışma zamanı ile](https://msdn.microsoft.com/magazine/jj651569.aspx).</span><span class="sxs-lookup"><span data-stu-id="40e61-124">For more information, see [Underneath the Hood with .NET and the Windows Runtime](https://msdn.microsoft.com/magazine/jj651569.aspx).</span></span>|  
|`ofReserved1`|<span data-ttu-id="40e61-125">İç kullanım için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="40e61-125">Reserved for internal use.</span></span>|  
|`ofReserved2`|<span data-ttu-id="40e61-126">İç kullanım için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="40e61-126">Reserved for internal use.</span></span>|  
|`ofReserved`|<span data-ttu-id="40e61-127">İç kullanım için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="40e61-127">Reserved for internal use.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="40e61-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="40e61-128">Requirements</span></span>  
 <span data-ttu-id="40e61-129">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40e61-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40e61-130">**Başlık:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="40e61-130">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="40e61-131">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40e61-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40e61-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="40e61-132">See Also</span></span>  
 [<span data-ttu-id="40e61-133">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="40e61-133">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
