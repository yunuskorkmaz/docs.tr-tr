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
ms.openlocfilehash: a11b7d5939c4c20504b1ff3dfb4613f85bca0db4
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007981"
---
# <a name="cor_native_link-structure"></a><span data-ttu-id="14894-102">COR_NATIVE_LINK Yapısı</span><span class="sxs-lookup"><span data-stu-id="14894-102">COR_NATIVE_LINK Structure</span></span>
<span data-ttu-id="14894-103">Yerel kodu bağlamak için kullanılan bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="14894-103">Contains information that is used to link native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14894-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="14894-104">Syntax</span></span>  
  
```cpp  
typedef struct
{  
    BYTE        m_linkType;  
    BYTE        m_flags;  
    mdMemberRef m_entryPoint;  
} COR_NATIVE_LINK;  
```  
  
## <a name="members"></a><span data-ttu-id="14894-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="14894-105">Members</span></span>  
  
|<span data-ttu-id="14894-106">Üye</span><span class="sxs-lookup"><span data-stu-id="14894-106">Member</span></span>|<span data-ttu-id="14894-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="14894-107">Description</span></span>|  
|------------|-----------------|  
|`m_linkType`|<span data-ttu-id="14894-108">Yerel koda bağlanacak tür.</span><span class="sxs-lookup"><span data-stu-id="14894-108">The type to be linked in native code.</span></span> <span data-ttu-id="14894-109">Bu değer, [Cornativelınktype](cornativelinktype-enumeration.md) değerlerinden biridir.</span><span class="sxs-lookup"><span data-stu-id="14894-109">This value is one of the [CorNativeLinkType](cornativelinktype-enumeration.md) values.</span></span>|  
|`m_flags`|<span data-ttu-id="14894-110">Yerel kod bağlanırken bağlayıcı tarafından kullanılan bayraklar.</span><span class="sxs-lookup"><span data-stu-id="14894-110">Flags used by the linker when linking native code.</span></span> <span data-ttu-id="14894-111">Bu değer, [Cornativelınkflags](cornativelinkflags-enumeration.md) değerlerinden biridir.</span><span class="sxs-lookup"><span data-stu-id="14894-111">This value is one of the [CorNativeLinkFlags](cornativelinkflags-enumeration.md) values.</span></span>|  
|`m_entryPoint`|<span data-ttu-id="14894-112">Giriş noktasını temsil eden MemberRef meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="14894-112">The MemberRef metadata token that represents the entry point.</span></span> <span data-ttu-id="14894-113">Biçim şöyledir: `lib:entrypoint`.</span><span class="sxs-lookup"><span data-stu-id="14894-113">The format is `lib:entrypoint`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="14894-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="14894-114">Requirements</span></span>  
 <span data-ttu-id="14894-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14894-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14894-116">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="14894-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="14894-117">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="14894-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="14894-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14894-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14894-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="14894-119">See also</span></span>

- [<span data-ttu-id="14894-120">Meta Veri Yapıları</span><span class="sxs-lookup"><span data-stu-id="14894-120">Metadata Structures</span></span>](metadata-structures.md)
- [<span data-ttu-id="14894-121">CorNativeLinkType Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="14894-121">CorNativeLinkType Enumeration</span></span>](cornativelinktype-enumeration.md)
- [<span data-ttu-id="14894-122">CorNativeLinkFlags Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="14894-122">CorNativeLinkFlags Enumeration</span></span>](cornativelinkflags-enumeration.md)
