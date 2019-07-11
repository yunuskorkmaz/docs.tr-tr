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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ae518e5a736a78a261dc3821d53d93afee95a271
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779988"
---
# <a name="cornativelink-structure"></a><span data-ttu-id="6a955-102">COR_NATIVE_LINK Yapısı</span><span class="sxs-lookup"><span data-stu-id="6a955-102">COR_NATIVE_LINK Structure</span></span>
<span data-ttu-id="6a955-103">Yerel kod bağlantı için kullanılan bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="6a955-103">Contains information that is used to link native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a955-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6a955-104">Syntax</span></span>  
  
```cpp  
typedef struct   
{  
    BYTE        m_linkType;  
    BYTE        m_flags;  
    mdMemberRef m_entryPoint;  
} COR_NATIVE_LINK;  
```  
  
## <a name="members"></a><span data-ttu-id="6a955-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="6a955-105">Members</span></span>  
  
|<span data-ttu-id="6a955-106">Üye</span><span class="sxs-lookup"><span data-stu-id="6a955-106">Member</span></span>|<span data-ttu-id="6a955-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6a955-107">Description</span></span>|  
|------------|-----------------|  
|`m_linkType`|<span data-ttu-id="6a955-108">Yerel kodda bağlanacak türü.</span><span class="sxs-lookup"><span data-stu-id="6a955-108">The type to be linked in native code.</span></span> <span data-ttu-id="6a955-109">Bu değer biridir [CorNativeLinkType](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md) değerleri.</span><span class="sxs-lookup"><span data-stu-id="6a955-109">This value is one of the [CorNativeLinkType](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md) values.</span></span>|  
|`m_flags`|<span data-ttu-id="6a955-110">Bağlayıcı tarafından yerel kod bağlanırken kullanılan bayraklar.</span><span class="sxs-lookup"><span data-stu-id="6a955-110">Flags used by the linker when linking native code.</span></span> <span data-ttu-id="6a955-111">Bu değer biridir [CorNativeLinkFlags](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md) değerleri.</span><span class="sxs-lookup"><span data-stu-id="6a955-111">This value is one of the [CorNativeLinkFlags](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md) values.</span></span>|  
|`m_entryPoint`|<span data-ttu-id="6a955-112">Giriş noktasını temsil eden MemberRef meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="6a955-112">The MemberRef metadata token that represents the entry point.</span></span> <span data-ttu-id="6a955-113">Biçim `lib:entrypoint`.</span><span class="sxs-lookup"><span data-stu-id="6a955-113">The format is `lib:entrypoint`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6a955-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6a955-114">Requirements</span></span>  
 <span data-ttu-id="6a955-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a955-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a955-116">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="6a955-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6a955-117">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="6a955-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6a955-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a955-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a955-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6a955-119">See also</span></span>

- [<span data-ttu-id="6a955-120">Meta Veri Yapıları</span><span class="sxs-lookup"><span data-stu-id="6a955-120">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [<span data-ttu-id="6a955-121">CorNativeLinkType Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="6a955-121">CorNativeLinkType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md)
- [<span data-ttu-id="6a955-122">CorNativeLinkFlags Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="6a955-122">CorNativeLinkFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md)
