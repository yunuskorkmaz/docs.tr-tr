---
description: 'Daha fazla bilgi edinin: COR_NATIVE_LINK yapısı'
title: COR_NATIVE_LINK Yapısı
ms.date: 03/30/2017
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
ms.openlocfilehash: 09c715af698a0614fd4a9a17679df6908a1497a6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99678581"
---
# <a name="cor_native_link-structure"></a><span data-ttu-id="3d622-103">COR_NATIVE_LINK Yapısı</span><span class="sxs-lookup"><span data-stu-id="3d622-103">COR_NATIVE_LINK Structure</span></span>

<span data-ttu-id="3d622-104">Yerel kodu bağlamak için kullanılan bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="3d622-104">Contains information that is used to link native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d622-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="3d622-105">Syntax</span></span>  
  
```cpp  
typedef struct
{  
    BYTE        m_linkType;  
    BYTE        m_flags;  
    mdMemberRef m_entryPoint;  
} COR_NATIVE_LINK;  
```  
  
## <a name="members"></a><span data-ttu-id="3d622-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="3d622-106">Members</span></span>  
  
|<span data-ttu-id="3d622-107">Üye</span><span class="sxs-lookup"><span data-stu-id="3d622-107">Member</span></span>|<span data-ttu-id="3d622-108">Description</span><span class="sxs-lookup"><span data-stu-id="3d622-108">Description</span></span>|  
|------------|-----------------|  
|`m_linkType`|<span data-ttu-id="3d622-109">Yerel koda bağlanacak tür.</span><span class="sxs-lookup"><span data-stu-id="3d622-109">The type to be linked in native code.</span></span> <span data-ttu-id="3d622-110">Bu değer, [Cornativelınktype](cornativelinktype-enumeration.md) değerlerinden biridir.</span><span class="sxs-lookup"><span data-stu-id="3d622-110">This value is one of the [CorNativeLinkType](cornativelinktype-enumeration.md) values.</span></span>|  
|`m_flags`|<span data-ttu-id="3d622-111">Yerel kod bağlanırken bağlayıcı tarafından kullanılan bayraklar.</span><span class="sxs-lookup"><span data-stu-id="3d622-111">Flags used by the linker when linking native code.</span></span> <span data-ttu-id="3d622-112">Bu değer, [Cornativelınkflags](cornativelinkflags-enumeration.md) değerlerinden biridir.</span><span class="sxs-lookup"><span data-stu-id="3d622-112">This value is one of the [CorNativeLinkFlags](cornativelinkflags-enumeration.md) values.</span></span>|  
|`m_entryPoint`|<span data-ttu-id="3d622-113">Giriş noktasını temsil eden MemberRef meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="3d622-113">The MemberRef metadata token that represents the entry point.</span></span> <span data-ttu-id="3d622-114">Biçim `lib:entrypoint` .</span><span class="sxs-lookup"><span data-stu-id="3d622-114">The format is `lib:entrypoint`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3d622-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3d622-115">Requirements</span></span>  

 <span data-ttu-id="3d622-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3d622-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d622-117">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="3d622-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3d622-118">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="3d622-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3d622-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d622-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d622-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3d622-120">See also</span></span>

- [<span data-ttu-id="3d622-121">Meta Veri Yapıları</span><span class="sxs-lookup"><span data-stu-id="3d622-121">Metadata Structures</span></span>](metadata-structures.md)
- [<span data-ttu-id="3d622-122">CorNativeLinkType Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="3d622-122">CorNativeLinkType Enumeration</span></span>](cornativelinktype-enumeration.md)
- [<span data-ttu-id="3d622-123">CorNativeLinkFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="3d622-123">CorNativeLinkFlags Enumeration</span></span>](cornativelinkflags-enumeration.md)
