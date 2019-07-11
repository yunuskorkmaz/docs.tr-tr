---
title: CorCallingConvention Numaralandırması
ms.date: 03/30/2017
api_name:
- CorCallingConvention
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorCallingConvention
helpviewer_keywords:
- CorCallingConvention enumeration [.NET Framework metadata]
ms.assetid: 69156fbf-7219-43bf-b4b8-b13f1a2fcb86
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 576fb8632818a6b8ffc3e2c0acc50eaafd074de3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67766972"
---
# <a name="corcallingconvention-enumeration"></a><span data-ttu-id="5574f-102">CorCallingConvention Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="5574f-102">CorCallingConvention Enumeration</span></span>
<span data-ttu-id="5574f-103">Yönetilen kodda yapılan çağrı kuralları türlerini açıklayan değerlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="5574f-103">Contains values that describe the types of calling conventions that are made in managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5574f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5574f-104">Syntax</span></span>  
  
```cpp  
typedef enum CorCallingConvention  
{  
    IMAGE_CEE_CS_CALLCONV_DEFAULT       = 0x0,  
  
    IMAGE_CEE_CS_CALLCONV_VARARG        = 0x5,  
    IMAGE_CEE_CS_CALLCONV_FIELD         = 0x6,  
    IMAGE_CEE_CS_CALLCONV_LOCAL_SIG     = 0x7,  
    IMAGE_CEE_CS_CALLCONV_PROPERTY      = 0x8,  
    IMAGE_CEE_CS_CALLCONV_UNMGD         = 0x9,  
    IMAGE_CEE_CS_CALLCONV_GENERICINST   = 0xa,  
    IMAGE_CEE_CS_CALLCONV_NATIVEVARARG  = 0xb,  
    IMAGE_CEE_CS_CALLCONV_MAX           = 0xc,  
  
    IMAGE_CEE_CS_CALLCONV_MASK          = 0x0f,  
    IMAGE_CEE_CS_CALLCONV_HASTHIS       = 0x20,  
    IMAGE_CEE_CS_CALLCONV_EXPLICITTHIS  = 0x40,  
    IMAGE_CEE_CS_CALLCONV_GENERIC       = 0x10  
  
} CorCallingConvention;  
```  
  
## <a name="members"></a><span data-ttu-id="5574f-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="5574f-105">Members</span></span>  
  
|<span data-ttu-id="5574f-106">Üye</span><span class="sxs-lookup"><span data-stu-id="5574f-106">Member</span></span>|<span data-ttu-id="5574f-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5574f-107">Description</span></span>|  
|------------|-----------------|  
|`IMAGE_CEE_CS_CALLCONV_DEFAULT`|<span data-ttu-id="5574f-108">Varsayılan çağırma kuralını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5574f-108">Indicates a default calling convention.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_VARARG`|<span data-ttu-id="5574f-109">Yöntem değişik sayıda parametreyi alır gösterir.</span><span class="sxs-lookup"><span data-stu-id="5574f-109">Indicates that the method takes a variable number of parameters.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_FIELD`|<span data-ttu-id="5574f-110">Arama için bir alan olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="5574f-110">Indicates that the call is to a field.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_LOCAL_SIG`|<span data-ttu-id="5574f-111">Arama için yerel bir yöntem olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="5574f-111">Indicates that the call is to a local method.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_PROPERTY`|<span data-ttu-id="5574f-112">Arama için bir özellik olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="5574f-112">Indicates that the call is to a property.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_UNMGD`|<span data-ttu-id="5574f-113">Çağrı yönetilmeyen olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="5574f-113">Indicates that the call is unmanaged.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_GENERICINST`|<span data-ttu-id="5574f-114">Bir genel yöntem örnekleme gösterir.</span><span class="sxs-lookup"><span data-stu-id="5574f-114">Indicates a generic method instantiation.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_NATIVEVARARG`|<span data-ttu-id="5574f-115">Bir 64-bit PInvoke çağrısına değişken sayıda parametre isteyen bir yöntemi gösterir.</span><span class="sxs-lookup"><span data-stu-id="5574f-115">Indicates a 64-bit PInvoke call to a method that takes a variable number of parameters.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_MAX`|<span data-ttu-id="5574f-116">Geçersiz 4-bit bir değer tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5574f-116">Describes an invalid 4-bit value.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_MASK`|<span data-ttu-id="5574f-117">Çağırma kuralı alt dört bitleri tarafından açıklanan gösterir.</span><span class="sxs-lookup"><span data-stu-id="5574f-117">Indicates that the calling convention is described by the bottom four bits.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_HASTHIS`|<span data-ttu-id="5574f-118">Üst bit açıklayan gösteren bir `this` parametresi.</span><span class="sxs-lookup"><span data-stu-id="5574f-118">Indicates that the top bit describes a `this` parameter.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_EXPLICITTHIS`|<span data-ttu-id="5574f-119">Bildiren bir `this` parametredir imzasında açıkça açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="5574f-119">Indicates that a `this` parameter is explicitly described in the signature.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_GENERIC`|<span data-ttu-id="5574f-120">Açık bir tür bağımsız değişkeni sayısına sahip bir genel metot imzasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="5574f-120">Indicates a generic method signature with an explicit number of type arguments.</span></span> <span data-ttu-id="5574f-121">Bu, bir sıradan parametre sayısı önce gelir.</span><span class="sxs-lookup"><span data-stu-id="5574f-121">This precedes an ordinary parameter count.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5574f-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5574f-122">Requirements</span></span>  
 <span data-ttu-id="5574f-123">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5574f-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5574f-124">**Üst bilgi:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="5574f-124">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="5574f-125">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5574f-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5574f-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5574f-126">See also</span></span>

- [<span data-ttu-id="5574f-127">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="5574f-127">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
