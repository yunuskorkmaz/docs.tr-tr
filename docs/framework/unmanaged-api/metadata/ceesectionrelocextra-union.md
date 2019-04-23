---
title: CeeSectionRelocExtra Birleşimi
ms.date: 03/30/2017
api_name:
- CeeSectionRelocExtra Union
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CeeSectionRelocExtra
helpviewer_keywords:
- CeeSectionRelocExtra union [.NET Framework metadata]
ms.assetid: d9568cf6-7f98-4cd6-ab36-0a2bd509afcc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8a78a4b82d0b2064c90c938a8614b0c7594f7856
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59182279"
---
# <a name="ceesectionrelocextra-union"></a><span data-ttu-id="4abf0-102">CeeSectionRelocExtra Birleşimi</span><span class="sxs-lookup"><span data-stu-id="4abf0-102">CeeSectionRelocExtra Union</span></span>
<span data-ttu-id="4abf0-103">Tarafından kullanılan bir adres farkı gösteren [Iceegen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) bir bölümün dışında yeniden konumlandırmakta arabirimi.</span><span class="sxs-lookup"><span data-stu-id="4abf0-103">Represents an address offset that is used by the [ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) interface to relocate a section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4abf0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4abf0-104">Syntax</span></span>  
  
```  
typedef union  {  
    USHORT highAdj;  
} CeeSectionRelocExtra;  
```  
  
## <a name="members"></a><span data-ttu-id="4abf0-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="4abf0-105">Members</span></span>  
  
|<span data-ttu-id="4abf0-106">Üye</span><span class="sxs-lookup"><span data-stu-id="4abf0-106">Member</span></span>|<span data-ttu-id="4abf0-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4abf0-107">Description</span></span>|  
|------------|-----------------|  
|`highAdj`|<span data-ttu-id="4abf0-108">Bölüm için adres üst ayarlama.</span><span class="sxs-lookup"><span data-stu-id="4abf0-108">The upper address adjustment for the section.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4abf0-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4abf0-109">Requirements</span></span>  
 <span data-ttu-id="4abf0-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4abf0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4abf0-111">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="4abf0-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4abf0-112">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="4abf0-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4abf0-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4abf0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4abf0-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4abf0-114">See also</span></span>

- [<span data-ttu-id="4abf0-115">Meta Veri Birleşimleri</span><span class="sxs-lookup"><span data-stu-id="4abf0-115">Metadata Unions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-unions.md)
