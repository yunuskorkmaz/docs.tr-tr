---
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
ms.openlocfilehash: 15f573ebc07bcf08a1ab8f5a5bbb88e940c5c8dc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724175"
---
# <a name="cor_native_link-structure"></a><span data-ttu-id="839ae-102">COR_NATIVE_LINK Yapısı</span><span class="sxs-lookup"><span data-stu-id="839ae-102">COR_NATIVE_LINK Structure</span></span>

<span data-ttu-id="839ae-103">Yerel kodu bağlamak için kullanılan bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="839ae-103">Contains information that is used to link native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="839ae-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="839ae-104">Syntax</span></span>  
  
```cpp  
typedef struct
{  
    BYTE        m_linkType;  
    BYTE        m_flags;  
    mdMemberRef m_entryPoint;  
} COR_NATIVE_LINK;  
```  
  
## <a name="members"></a><span data-ttu-id="839ae-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="839ae-105">Members</span></span>  
  
|<span data-ttu-id="839ae-106">Üye</span><span class="sxs-lookup"><span data-stu-id="839ae-106">Member</span></span>|<span data-ttu-id="839ae-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="839ae-107">Description</span></span>|  
|------------|-----------------|  
|`m_linkType`|<span data-ttu-id="839ae-108">Yerel koda bağlanacak tür.</span><span class="sxs-lookup"><span data-stu-id="839ae-108">The type to be linked in native code.</span></span> <span data-ttu-id="839ae-109">Bu değer, [Cornativelınktype](cornativelinktype-enumeration.md) değerlerinden biridir.</span><span class="sxs-lookup"><span data-stu-id="839ae-109">This value is one of the [CorNativeLinkType](cornativelinktype-enumeration.md) values.</span></span>|  
|`m_flags`|<span data-ttu-id="839ae-110">Yerel kod bağlanırken bağlayıcı tarafından kullanılan bayraklar.</span><span class="sxs-lookup"><span data-stu-id="839ae-110">Flags used by the linker when linking native code.</span></span> <span data-ttu-id="839ae-111">Bu değer, [Cornativelınkflags](cornativelinkflags-enumeration.md) değerlerinden biridir.</span><span class="sxs-lookup"><span data-stu-id="839ae-111">This value is one of the [CorNativeLinkFlags](cornativelinkflags-enumeration.md) values.</span></span>|  
|`m_entryPoint`|<span data-ttu-id="839ae-112">Giriş noktasını temsil eden MemberRef meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="839ae-112">The MemberRef metadata token that represents the entry point.</span></span> <span data-ttu-id="839ae-113">Biçim `lib:entrypoint` .</span><span class="sxs-lookup"><span data-stu-id="839ae-113">The format is `lib:entrypoint`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="839ae-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="839ae-114">Requirements</span></span>  

 <span data-ttu-id="839ae-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="839ae-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="839ae-116">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="839ae-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="839ae-117">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="839ae-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="839ae-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="839ae-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="839ae-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="839ae-119">See also</span></span>

- [<span data-ttu-id="839ae-120">Meta Veri Yapıları</span><span class="sxs-lookup"><span data-stu-id="839ae-120">Metadata Structures</span></span>](metadata-structures.md)
- [<span data-ttu-id="839ae-121">CorNativeLinkType Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="839ae-121">CorNativeLinkType Enumeration</span></span>](cornativelinktype-enumeration.md)
- [<span data-ttu-id="839ae-122">CorNativeLinkFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="839ae-122">CorNativeLinkFlags Enumeration</span></span>](cornativelinkflags-enumeration.md)
