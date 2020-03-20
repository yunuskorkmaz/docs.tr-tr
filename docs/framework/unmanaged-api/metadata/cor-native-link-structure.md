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
ms.openlocfilehash: 812b70a594b5aa933f52d36f32d96d712267ecf4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177955"
---
# <a name="cor_native_link-structure"></a><span data-ttu-id="3f754-102">COR_NATIVE_LINK Yapısı</span><span class="sxs-lookup"><span data-stu-id="3f754-102">COR_NATIVE_LINK Structure</span></span>
<span data-ttu-id="3f754-103">Yerel kodu bağlamak için kullanılan bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="3f754-103">Contains information that is used to link native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f754-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3f754-104">Syntax</span></span>  
  
```cpp  
typedef struct
{  
    BYTE        m_linkType;  
    BYTE        m_flags;  
    mdMemberRef m_entryPoint;  
} COR_NATIVE_LINK;  
```  
  
## <a name="members"></a><span data-ttu-id="3f754-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="3f754-105">Members</span></span>  
  
|<span data-ttu-id="3f754-106">Üye</span><span class="sxs-lookup"><span data-stu-id="3f754-106">Member</span></span>|<span data-ttu-id="3f754-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3f754-107">Description</span></span>|  
|------------|-----------------|  
|`m_linkType`|<span data-ttu-id="3f754-108">Yerel kodda bağlanacak tür.</span><span class="sxs-lookup"><span data-stu-id="3f754-108">The type to be linked in native code.</span></span> <span data-ttu-id="3f754-109">Bu değer [CorNativeLinkType](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md) değerlerinden biridir.</span><span class="sxs-lookup"><span data-stu-id="3f754-109">This value is one of the [CorNativeLinkType](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md) values.</span></span>|  
|`m_flags`|<span data-ttu-id="3f754-110">Yerel kodu bağlarken bağlayıcı tarafından kullanılan bayraklar.</span><span class="sxs-lookup"><span data-stu-id="3f754-110">Flags used by the linker when linking native code.</span></span> <span data-ttu-id="3f754-111">Bu değer [CorNativeLinkFlags](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md) değerlerinden biridir.</span><span class="sxs-lookup"><span data-stu-id="3f754-111">This value is one of the [CorNativeLinkFlags](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md) values.</span></span>|  
|`m_entryPoint`|<span data-ttu-id="3f754-112">Giriş noktasını temsil eden MemberRef meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="3f754-112">The MemberRef metadata token that represents the entry point.</span></span> <span data-ttu-id="3f754-113">Biçim şöyledir: `lib:entrypoint`.</span><span class="sxs-lookup"><span data-stu-id="3f754-113">The format is `lib:entrypoint`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3f754-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3f754-114">Requirements</span></span>  
 <span data-ttu-id="3f754-115">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f754-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f754-116">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3f754-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3f754-117">**Kütüphane:** MsCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="3f754-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3f754-118">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f754-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f754-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3f754-119">See also</span></span>

- [<span data-ttu-id="3f754-120">Meta Veri Yapıları</span><span class="sxs-lookup"><span data-stu-id="3f754-120">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [<span data-ttu-id="3f754-121">CorNativeLinkType Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="3f754-121">CorNativeLinkType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md)
- [<span data-ttu-id="3f754-122">CorNativeLinkFlags Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="3f754-122">CorNativeLinkFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md)
