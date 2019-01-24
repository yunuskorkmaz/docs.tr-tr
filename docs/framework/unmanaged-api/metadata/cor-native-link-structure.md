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
ms.openlocfilehash: 08d27eb834c1a9a3a5d163bb2d3054f599ae1669
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54719566"
---
# <a name="cornativelink-structure"></a><span data-ttu-id="3d705-102">COR_NATIVE_LINK Yapısı</span><span class="sxs-lookup"><span data-stu-id="3d705-102">COR_NATIVE_LINK Structure</span></span>
<span data-ttu-id="3d705-103">Yerel kod bağlantı için kullanılan bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="3d705-103">Contains information that is used to link native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d705-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3d705-104">Syntax</span></span>  
  
```  
typedef struct   
{  
    BYTE        m_linkType;  
    BYTE        m_flags;  
    mdMemberRef m_entryPoint;  
} COR_NATIVE_LINK;  
```  
  
## <a name="members"></a><span data-ttu-id="3d705-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="3d705-105">Members</span></span>  
  
|<span data-ttu-id="3d705-106">Üye</span><span class="sxs-lookup"><span data-stu-id="3d705-106">Member</span></span>|<span data-ttu-id="3d705-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3d705-107">Description</span></span>|  
|------------|-----------------|  
|`m_linkType`|<span data-ttu-id="3d705-108">Yerel kodda bağlanacak türü.</span><span class="sxs-lookup"><span data-stu-id="3d705-108">The type to be linked in native code.</span></span> <span data-ttu-id="3d705-109">Bu değer biridir [CorNativeLinkType](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md) değerleri.</span><span class="sxs-lookup"><span data-stu-id="3d705-109">This value is one of the [CorNativeLinkType](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md) values.</span></span>|  
|`m_flags`|<span data-ttu-id="3d705-110">Bağlayıcı tarafından yerel kod bağlanırken kullanılan bayraklar.</span><span class="sxs-lookup"><span data-stu-id="3d705-110">Flags used by the linker when linking native code.</span></span> <span data-ttu-id="3d705-111">Bu değer biridir [CorNativeLinkFlags](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md) değerleri.</span><span class="sxs-lookup"><span data-stu-id="3d705-111">This value is one of the [CorNativeLinkFlags](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md) values.</span></span>|  
|`m_entryPoint`|<span data-ttu-id="3d705-112">Giriş noktasını temsil eden MemberRef meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="3d705-112">The MemberRef metadata token that represents the entry point.</span></span> <span data-ttu-id="3d705-113">Biçim `lib:entrypoint`.</span><span class="sxs-lookup"><span data-stu-id="3d705-113">The format is `lib:entrypoint`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3d705-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3d705-114">Requirements</span></span>  
 <span data-ttu-id="3d705-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3d705-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d705-116">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="3d705-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3d705-117">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="3d705-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3d705-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d705-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d705-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3d705-119">See also</span></span>
- [<span data-ttu-id="3d705-120">Meta Veri Yapıları</span><span class="sxs-lookup"><span data-stu-id="3d705-120">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [<span data-ttu-id="3d705-121">CorNativeLinkType Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="3d705-121">CorNativeLinkType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md)
- [<span data-ttu-id="3d705-122">CorNativeLinkFlags Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="3d705-122">CorNativeLinkFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md)
