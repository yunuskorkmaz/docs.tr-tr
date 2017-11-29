---
title: "CorCallingConvention Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorCallingConvention
api_location: mscoree.dll
api_type: COM
f1_keywords: CorCallingConvention
helpviewer_keywords: CorCallingConvention enumeration [.NET Framework metadata]
ms.assetid: 69156fbf-7219-43bf-b4b8-b13f1a2fcb86
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8c0fbbb5f2c8f73cb6c76137263fa457840cdddc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="corcallingconvention-enumeration"></a><span data-ttu-id="0b40f-102">CorCallingConvention Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="0b40f-102">CorCallingConvention Enumeration</span></span>
<span data-ttu-id="0b40f-103">Yönetilen kodda yapılan çağırma kurallarını türlerini açıklayan değerlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="0b40f-103">Contains values that describe the types of calling conventions that are made in managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b40f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0b40f-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="0b40f-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="0b40f-105">Members</span></span>  
  
|<span data-ttu-id="0b40f-106">Üye</span><span class="sxs-lookup"><span data-stu-id="0b40f-106">Member</span></span>|<span data-ttu-id="0b40f-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0b40f-107">Description</span></span>|  
|------------|-----------------|  
|`IMAGE_CEE_CS_CALLCONV_DEFAULT`|<span data-ttu-id="0b40f-108">Çağırma kuralı varsayılan gösterir.</span><span class="sxs-lookup"><span data-stu-id="0b40f-108">Indicates a default calling convention.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_VARARG`|<span data-ttu-id="0b40f-109">Yöntem değişken sayıda parametre isteyen gösterir.</span><span class="sxs-lookup"><span data-stu-id="0b40f-109">Indicates that the method takes a variable number of parameters.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_FIELD`|<span data-ttu-id="0b40f-110">Aramanın bir alan olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="0b40f-110">Indicates that the call is to a field.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_LOCAL_SIG`|<span data-ttu-id="0b40f-111">Arama için yerel bir yöntemi gösterir.</span><span class="sxs-lookup"><span data-stu-id="0b40f-111">Indicates that the call is to a local method.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_PROPERTY`|<span data-ttu-id="0b40f-112">Çağrı özelliğe olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="0b40f-112">Indicates that the call is to a property.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_UNMGD`|<span data-ttu-id="0b40f-113">Çağrı yönetilmeyen olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="0b40f-113">Indicates that the call is unmanaged.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_GENERICINST`|<span data-ttu-id="0b40f-114">Genel yöntem örnekleme gösterir.</span><span class="sxs-lookup"><span data-stu-id="0b40f-114">Indicates a generic method instantiation.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_NATIVEVARARG`|<span data-ttu-id="0b40f-115">Değişken sayıda parametre isteyen bir yöntem 64-bit PInvoke çağrısı gösterir.</span><span class="sxs-lookup"><span data-stu-id="0b40f-115">Indicates a 64-bit PInvoke call to a method that takes a variable number of parameters.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_MAX`|<span data-ttu-id="0b40f-116">Geçersiz bir 4-bit değer açıklar.</span><span class="sxs-lookup"><span data-stu-id="0b40f-116">Describes an invalid 4-bit value.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_MASK`|<span data-ttu-id="0b40f-117">Çağırma kuralı alt dört BITS tarafından açıklanan gösterir.</span><span class="sxs-lookup"><span data-stu-id="0b40f-117">Indicates that the calling convention is described by the bottom four bits.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_HASTHIS`|<span data-ttu-id="0b40f-118">Üst bit açıklayan gösteren bir `this` parametresi.</span><span class="sxs-lookup"><span data-stu-id="0b40f-118">Indicates that the top bit describes a `this` parameter.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_EXPLICITTHIS`|<span data-ttu-id="0b40f-119">Belirten bir `this` parametredir imzada açıkça açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="0b40f-119">Indicates that a `this` parameter is explicitly described in the signature.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_GENERIC`|<span data-ttu-id="0b40f-120">Bir genel yöntem imza açık sayıda tür bağımsız değişkeni ile gösterir.</span><span class="sxs-lookup"><span data-stu-id="0b40f-120">Indicates a generic method signature with an explicit number of type arguments.</span></span> <span data-ttu-id="0b40f-121">Bu, normal parametre sayısı önce gelir.</span><span class="sxs-lookup"><span data-stu-id="0b40f-121">This precedes an ordinary parameter count.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0b40f-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0b40f-122">Requirements</span></span>  
 <span data-ttu-id="0b40f-123">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b40f-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b40f-124">**Başlık:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="0b40f-124">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="0b40f-125">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b40f-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b40f-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0b40f-126">See Also</span></span>  
 [<span data-ttu-id="0b40f-127">Meta veri numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="0b40f-127">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
