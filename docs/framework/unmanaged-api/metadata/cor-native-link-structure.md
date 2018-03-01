---
title: "COR_NATIVE_LINK Yapısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- COR_NATIVE_LINK
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_NATIVE_LINK
helpviewer_keywords:
- COR_NATIVE_LINK structure [.NET Framework metadata]
ms.assetid: 6ef78d3c-1c69-4141-b687-dcb065b7a74d
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 63e5946e98e7c862a2502a71a02e605a38086618
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="cornativelink-structure"></a><span data-ttu-id="2e3fb-102">COR_NATIVE_LINK Yapısı</span><span class="sxs-lookup"><span data-stu-id="2e3fb-102">COR_NATIVE_LINK Structure</span></span>
<span data-ttu-id="2e3fb-103">Yerel kod bağlamak için kullanılan bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="2e3fb-103">Contains information that is used to link native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e3fb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2e3fb-104">Syntax</span></span>  
  
```  
typedef struct   
{  
    BYTE        m_linkType;  
    BYTE        m_flags;  
    mdMemberRef m_entryPoint;  
} COR_NATIVE_LINK;  
```  
  
## <a name="members"></a><span data-ttu-id="2e3fb-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="2e3fb-105">Members</span></span>  
  
|<span data-ttu-id="2e3fb-106">Üye</span><span class="sxs-lookup"><span data-stu-id="2e3fb-106">Member</span></span>|<span data-ttu-id="2e3fb-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2e3fb-107">Description</span></span>|  
|------------|-----------------|  
|`m_linkType`|<span data-ttu-id="2e3fb-108">Yerel kodda bağlanması türü.</span><span class="sxs-lookup"><span data-stu-id="2e3fb-108">The type to be linked in native code.</span></span> <span data-ttu-id="2e3fb-109">Bu değer biri [CorNativeLinkType](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md) değerleri.</span><span class="sxs-lookup"><span data-stu-id="2e3fb-109">This value is one of the [CorNativeLinkType](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md) values.</span></span>|  
|`m_flags`|<span data-ttu-id="2e3fb-110">Yerel kod bağlarken bağlayıcı tarafından kullanılan bayraklar.</span><span class="sxs-lookup"><span data-stu-id="2e3fb-110">Flags used by the linker when linking native code.</span></span> <span data-ttu-id="2e3fb-111">Bu değer biri [CorNativeLinkFlags](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md) değerleri.</span><span class="sxs-lookup"><span data-stu-id="2e3fb-111">This value is one of the [CorNativeLinkFlags](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md) values.</span></span>|  
|`m_entryPoint`|<span data-ttu-id="2e3fb-112">Giriş noktasını temsil eden MemberRef meta veri simgesi.</span><span class="sxs-lookup"><span data-stu-id="2e3fb-112">The MemberRef metadata token that represents the entry point.</span></span> <span data-ttu-id="2e3fb-113">Biçim `lib:entrypoint`.</span><span class="sxs-lookup"><span data-stu-id="2e3fb-113">The format is `lib:entrypoint`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2e3fb-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2e3fb-114">Requirements</span></span>  
 <span data-ttu-id="2e3fb-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e3fb-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e3fb-116">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2e3fb-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2e3fb-117">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="2e3fb-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2e3fb-118">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e3fb-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e3fb-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2e3fb-119">See Also</span></span>  
 [<span data-ttu-id="2e3fb-120">Meta Veri Yapıları</span><span class="sxs-lookup"><span data-stu-id="2e3fb-120">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)  
 [<span data-ttu-id="2e3fb-121">CorNativeLinkType Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="2e3fb-121">CorNativeLinkType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md)  
 [<span data-ttu-id="2e3fb-122">CorNativeLinkFlags Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="2e3fb-122">CorNativeLinkFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md)
