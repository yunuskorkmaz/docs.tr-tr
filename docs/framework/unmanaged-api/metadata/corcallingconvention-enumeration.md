---
description: 'Daha fazla bilgi edinin: CorCallingConvention numaralandırması'
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
ms.openlocfilehash: 2e823fe3566ef7a54f759cd5debbbd7d5dcf3ceb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99678451"
---
# <a name="corcallingconvention-enumeration"></a><span data-ttu-id="898ec-103">CorCallingConvention Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="898ec-103">CorCallingConvention Enumeration</span></span>

<span data-ttu-id="898ec-104">Yönetilen kodda yapılan çağırma kurallarının türlerini tanımlayan değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="898ec-104">Contains values that describe the types of calling conventions that are made in managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="898ec-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="898ec-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="898ec-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="898ec-106">Members</span></span>  
  
|<span data-ttu-id="898ec-107">Üye</span><span class="sxs-lookup"><span data-stu-id="898ec-107">Member</span></span>|<span data-ttu-id="898ec-108">Description</span><span class="sxs-lookup"><span data-stu-id="898ec-108">Description</span></span>|  
|------------|-----------------|  
|`IMAGE_CEE_CS_CALLCONV_DEFAULT`|<span data-ttu-id="898ec-109">Varsayılan bir çağırma kuralını gösterir.</span><span class="sxs-lookup"><span data-stu-id="898ec-109">Indicates a default calling convention.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_VARARG`|<span data-ttu-id="898ec-110">Yöntemin değişken sayıda parametre aldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="898ec-110">Indicates that the method takes a variable number of parameters.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_FIELD`|<span data-ttu-id="898ec-111">Çağrının bir alana olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="898ec-111">Indicates that the call is to a field.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_LOCAL_SIG`|<span data-ttu-id="898ec-112">Çağrının yerel bir yönteme olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="898ec-112">Indicates that the call is to a local method.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_PROPERTY`|<span data-ttu-id="898ec-113">Çağrının bir özelliğe olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="898ec-113">Indicates that the call is to a property.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_UNMGD`|<span data-ttu-id="898ec-114">Çağrının yönetilmeyen olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="898ec-114">Indicates that the call is unmanaged.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_GENERICINST`|<span data-ttu-id="898ec-115">Genel bir yöntem örneklemeyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="898ec-115">Indicates a generic method instantiation.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_NATIVEVARARG`|<span data-ttu-id="898ec-116">Değişken sayıda parametre alan bir yönteme 64 bitlik bir PInvoke çağrısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="898ec-116">Indicates a 64-bit PInvoke call to a method that takes a variable number of parameters.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_MAX`|<span data-ttu-id="898ec-117">Geçersiz 4 bitlik bir değeri açıklar.</span><span class="sxs-lookup"><span data-stu-id="898ec-117">Describes an invalid 4-bit value.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_MASK`|<span data-ttu-id="898ec-118">Çağırma kuralının en alttaki dört bit tarafından açıklandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="898ec-118">Indicates that the calling convention is described by the bottom four bits.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_HASTHIS`|<span data-ttu-id="898ec-119">En üstteki bitin bir parametreyi tanımlıyor olduğunu gösterir `this` .</span><span class="sxs-lookup"><span data-stu-id="898ec-119">Indicates that the top bit describes a `this` parameter.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_EXPLICITTHIS`|<span data-ttu-id="898ec-120">Bir `this` parametrenin İmzada açıkça açıklandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="898ec-120">Indicates that a `this` parameter is explicitly described in the signature.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_GENERIC`|<span data-ttu-id="898ec-121">Açık sayıda tür bağımsız değişkeni olan bir genel yöntem imzasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="898ec-121">Indicates a generic method signature with an explicit number of type arguments.</span></span> <span data-ttu-id="898ec-122">Bu, normal bir parametre sayısından önce gelir.</span><span class="sxs-lookup"><span data-stu-id="898ec-122">This precedes an ordinary parameter count.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="898ec-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="898ec-123">Requirements</span></span>  

 <span data-ttu-id="898ec-124">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="898ec-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="898ec-125">**Üst bilgi:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="898ec-125">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="898ec-126">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="898ec-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="898ec-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="898ec-127">See also</span></span>

- [<span data-ttu-id="898ec-128">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="898ec-128">Metadata Enumerations</span></span>](metadata-enumerations.md)
