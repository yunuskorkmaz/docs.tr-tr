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
ms.openlocfilehash: 310319e8fefe80017c58706e2beaee5eb1e78422
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007916"
---
# <a name="corcallingconvention-enumeration"></a><span data-ttu-id="8389e-102">CorCallingConvention Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="8389e-102">CorCallingConvention Enumeration</span></span>
<span data-ttu-id="8389e-103">Yönetilen kodda yapılan çağırma kurallarının türlerini tanımlayan değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="8389e-103">Contains values that describe the types of calling conventions that are made in managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8389e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8389e-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="8389e-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="8389e-105">Members</span></span>  
  
|<span data-ttu-id="8389e-106">Üye</span><span class="sxs-lookup"><span data-stu-id="8389e-106">Member</span></span>|<span data-ttu-id="8389e-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8389e-107">Description</span></span>|  
|------------|-----------------|  
|`IMAGE_CEE_CS_CALLCONV_DEFAULT`|<span data-ttu-id="8389e-108">Varsayılan bir çağırma kuralını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8389e-108">Indicates a default calling convention.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_VARARG`|<span data-ttu-id="8389e-109">Yöntemin değişken sayıda parametre aldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8389e-109">Indicates that the method takes a variable number of parameters.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_FIELD`|<span data-ttu-id="8389e-110">Çağrının bir alana olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="8389e-110">Indicates that the call is to a field.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_LOCAL_SIG`|<span data-ttu-id="8389e-111">Çağrının yerel bir yönteme olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="8389e-111">Indicates that the call is to a local method.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_PROPERTY`|<span data-ttu-id="8389e-112">Çağrının bir özelliğe olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="8389e-112">Indicates that the call is to a property.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_UNMGD`|<span data-ttu-id="8389e-113">Çağrının yönetilmeyen olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="8389e-113">Indicates that the call is unmanaged.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_GENERICINST`|<span data-ttu-id="8389e-114">Genel bir yöntem örneklemeyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="8389e-114">Indicates a generic method instantiation.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_NATIVEVARARG`|<span data-ttu-id="8389e-115">Değişken sayıda parametre alan bir yönteme 64 bitlik bir PInvoke çağrısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8389e-115">Indicates a 64-bit PInvoke call to a method that takes a variable number of parameters.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_MAX`|<span data-ttu-id="8389e-116">Geçersiz 4 bitlik bir değeri açıklar.</span><span class="sxs-lookup"><span data-stu-id="8389e-116">Describes an invalid 4-bit value.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_MASK`|<span data-ttu-id="8389e-117">Çağırma kuralının en alttaki dört bit tarafından açıklandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8389e-117">Indicates that the calling convention is described by the bottom four bits.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_HASTHIS`|<span data-ttu-id="8389e-118">En üstteki bitin bir parametreyi tanımlıyor olduğunu gösterir `this` .</span><span class="sxs-lookup"><span data-stu-id="8389e-118">Indicates that the top bit describes a `this` parameter.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_EXPLICITTHIS`|<span data-ttu-id="8389e-119">Bir `this` parametrenin İmzada açıkça açıklandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8389e-119">Indicates that a `this` parameter is explicitly described in the signature.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_GENERIC`|<span data-ttu-id="8389e-120">Açık sayıda tür bağımsız değişkeni olan bir genel yöntem imzasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8389e-120">Indicates a generic method signature with an explicit number of type arguments.</span></span> <span data-ttu-id="8389e-121">Bu, normal bir parametre sayısından önce gelir.</span><span class="sxs-lookup"><span data-stu-id="8389e-121">This precedes an ordinary parameter count.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8389e-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8389e-122">Requirements</span></span>  
 <span data-ttu-id="8389e-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8389e-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8389e-124">**Üst bilgi:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="8389e-124">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="8389e-125">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8389e-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8389e-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8389e-126">See also</span></span>

- [<span data-ttu-id="8389e-127">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="8389e-127">Metadata Enumerations</span></span>](metadata-enumerations.md)
