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
ms.workload: dotnet
ms.openlocfilehash: 154fbcc393bb56ab2c249a4928a4451dced9761a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="corcallingconvention-enumeration"></a><span data-ttu-id="3da8b-102">CorCallingConvention Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="3da8b-102">CorCallingConvention Enumeration</span></span>
<span data-ttu-id="3da8b-103">Yönetilen kodda yapılan çağırma kurallarını türlerini açıklayan değerlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="3da8b-103">Contains values that describe the types of calling conventions that are made in managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3da8b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3da8b-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="3da8b-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="3da8b-105">Members</span></span>  
  
|<span data-ttu-id="3da8b-106">Üye</span><span class="sxs-lookup"><span data-stu-id="3da8b-106">Member</span></span>|<span data-ttu-id="3da8b-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3da8b-107">Description</span></span>|  
|------------|-----------------|  
|`IMAGE_CEE_CS_CALLCONV_DEFAULT`|<span data-ttu-id="3da8b-108">Çağırma kuralı varsayılan gösterir.</span><span class="sxs-lookup"><span data-stu-id="3da8b-108">Indicates a default calling convention.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_VARARG`|<span data-ttu-id="3da8b-109">Yöntem değişken sayıda parametre isteyen gösterir.</span><span class="sxs-lookup"><span data-stu-id="3da8b-109">Indicates that the method takes a variable number of parameters.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_FIELD`|<span data-ttu-id="3da8b-110">Aramanın bir alan olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="3da8b-110">Indicates that the call is to a field.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_LOCAL_SIG`|<span data-ttu-id="3da8b-111">Arama için yerel bir yöntemi gösterir.</span><span class="sxs-lookup"><span data-stu-id="3da8b-111">Indicates that the call is to a local method.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_PROPERTY`|<span data-ttu-id="3da8b-112">Çağrı özelliğe olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="3da8b-112">Indicates that the call is to a property.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_UNMGD`|<span data-ttu-id="3da8b-113">Çağrı yönetilmeyen olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="3da8b-113">Indicates that the call is unmanaged.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_GENERICINST`|<span data-ttu-id="3da8b-114">Genel yöntem örnekleme gösterir.</span><span class="sxs-lookup"><span data-stu-id="3da8b-114">Indicates a generic method instantiation.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_NATIVEVARARG`|<span data-ttu-id="3da8b-115">Değişken sayıda parametre isteyen bir yöntem 64-bit PInvoke çağrısı gösterir.</span><span class="sxs-lookup"><span data-stu-id="3da8b-115">Indicates a 64-bit PInvoke call to a method that takes a variable number of parameters.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_MAX`|<span data-ttu-id="3da8b-116">Geçersiz bir 4-bit değer açıklar.</span><span class="sxs-lookup"><span data-stu-id="3da8b-116">Describes an invalid 4-bit value.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_MASK`|<span data-ttu-id="3da8b-117">Çağırma kuralı alt dört BITS tarafından açıklanan gösterir.</span><span class="sxs-lookup"><span data-stu-id="3da8b-117">Indicates that the calling convention is described by the bottom four bits.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_HASTHIS`|<span data-ttu-id="3da8b-118">Üst bit açıklayan gösteren bir `this` parametresi.</span><span class="sxs-lookup"><span data-stu-id="3da8b-118">Indicates that the top bit describes a `this` parameter.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_EXPLICITTHIS`|<span data-ttu-id="3da8b-119">Belirten bir `this` parametredir imzada açıkça açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="3da8b-119">Indicates that a `this` parameter is explicitly described in the signature.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_GENERIC`|<span data-ttu-id="3da8b-120">Bir genel yöntem imza açık sayıda tür bağımsız değişkeni ile gösterir.</span><span class="sxs-lookup"><span data-stu-id="3da8b-120">Indicates a generic method signature with an explicit number of type arguments.</span></span> <span data-ttu-id="3da8b-121">Bu, normal parametre sayısı önce gelir.</span><span class="sxs-lookup"><span data-stu-id="3da8b-121">This precedes an ordinary parameter count.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3da8b-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3da8b-122">Requirements</span></span>  
 <span data-ttu-id="3da8b-123">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3da8b-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3da8b-124">**Başlık:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="3da8b-124">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="3da8b-125">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3da8b-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3da8b-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3da8b-126">See Also</span></span>  
 [<span data-ttu-id="3da8b-127">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="3da8b-127">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
