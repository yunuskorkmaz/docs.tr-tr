---
title: "COR_NATIVE_LINK Yapısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_NATIVE_LINK
api_location: mscoree.dll
api_type: COM
f1_keywords: COR_NATIVE_LINK
helpviewer_keywords: COR_NATIVE_LINK structure [.NET Framework metadata]
ms.assetid: 6ef78d3c-1c69-4141-b687-dcb065b7a74d
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e27b66fce8a78ef0feb7ed10e77cc51fc1fe83c0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="cornativelink-structure"></a><span data-ttu-id="0ee35-102">COR_NATIVE_LINK Yapısı</span><span class="sxs-lookup"><span data-stu-id="0ee35-102">COR_NATIVE_LINK Structure</span></span>
<span data-ttu-id="0ee35-103">Yerel kod bağlamak için kullanılan bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="0ee35-103">Contains information that is used to link native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ee35-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0ee35-104">Syntax</span></span>  
  
```  
typedef struct   
{  
    BYTE        m_linkType;  
    BYTE        m_flags;  
    mdMemberRef m_entryPoint;  
} COR_NATIVE_LINK;  
```  
  
## <a name="members"></a><span data-ttu-id="0ee35-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="0ee35-105">Members</span></span>  
  
|<span data-ttu-id="0ee35-106">Üye</span><span class="sxs-lookup"><span data-stu-id="0ee35-106">Member</span></span>|<span data-ttu-id="0ee35-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0ee35-107">Description</span></span>|  
|------------|-----------------|  
|`m_linkType`|<span data-ttu-id="0ee35-108">Yerel kodda bağlanması türü.</span><span class="sxs-lookup"><span data-stu-id="0ee35-108">The type to be linked in native code.</span></span> <span data-ttu-id="0ee35-109">Bu değer biri [CorNativeLinkType](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md) değerleri.</span><span class="sxs-lookup"><span data-stu-id="0ee35-109">This value is one of the [CorNativeLinkType](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md) values.</span></span>|  
|`m_flags`|<span data-ttu-id="0ee35-110">Yerel kod bağlarken bağlayıcı tarafından kullanılan bayraklar.</span><span class="sxs-lookup"><span data-stu-id="0ee35-110">Flags used by the linker when linking native code.</span></span> <span data-ttu-id="0ee35-111">Bu değer biri [CorNativeLinkFlags](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md) değerleri.</span><span class="sxs-lookup"><span data-stu-id="0ee35-111">This value is one of the [CorNativeLinkFlags](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md) values.</span></span>|  
|`m_entryPoint`|<span data-ttu-id="0ee35-112">Giriş noktasını temsil eden MemberRef meta veri simgesi.</span><span class="sxs-lookup"><span data-stu-id="0ee35-112">The MemberRef metadata token that represents the entry point.</span></span> <span data-ttu-id="0ee35-113">Biçim `lib:entrypoint`.</span><span class="sxs-lookup"><span data-stu-id="0ee35-113">The format is `lib:entrypoint`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0ee35-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0ee35-114">Requirements</span></span>  
 <span data-ttu-id="0ee35-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0ee35-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ee35-116">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0ee35-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0ee35-117">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="0ee35-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0ee35-118">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ee35-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ee35-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0ee35-119">See Also</span></span>  
 [<span data-ttu-id="0ee35-120">Meta veri yapıları</span><span class="sxs-lookup"><span data-stu-id="0ee35-120">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)  
 [<span data-ttu-id="0ee35-121">CorNativeLinkType numaralandırması</span><span class="sxs-lookup"><span data-stu-id="0ee35-121">CorNativeLinkType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md)  
 [<span data-ttu-id="0ee35-122">CorNativeLinkFlags numaralandırması</span><span class="sxs-lookup"><span data-stu-id="0ee35-122">CorNativeLinkFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md)
