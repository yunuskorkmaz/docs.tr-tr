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
ms.openlocfilehash: c7634ec801a30aa7ba07954c1df0c3d37ec279eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33440307"
---
# <a name="ceesectionrelocextra-union"></a><span data-ttu-id="10eac-102">CeeSectionRelocExtra Birleşimi</span><span class="sxs-lookup"><span data-stu-id="10eac-102">CeeSectionRelocExtra Union</span></span>
<span data-ttu-id="10eac-103">Tarafından kullanılan bir adres farkı temsil eden [Iceegen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) bir bölümü yeniden konumlandırmak için arabirim.</span><span class="sxs-lookup"><span data-stu-id="10eac-103">Represents an address offset that is used by the [ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) interface to relocate a section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10eac-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="10eac-104">Syntax</span></span>  
  
```  
typedef union  {  
    USHORT highAdj;  
} CeeSectionRelocExtra;  
```  
  
## <a name="members"></a><span data-ttu-id="10eac-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="10eac-105">Members</span></span>  
  
|<span data-ttu-id="10eac-106">Üye</span><span class="sxs-lookup"><span data-stu-id="10eac-106">Member</span></span>|<span data-ttu-id="10eac-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="10eac-107">Description</span></span>|  
|------------|-----------------|  
|`highAdj`|<span data-ttu-id="10eac-108">Bölümü için adres üst ayarlama.</span><span class="sxs-lookup"><span data-stu-id="10eac-108">The upper address adjustment for the section.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="10eac-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="10eac-109">Requirements</span></span>  
 <span data-ttu-id="10eac-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="10eac-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10eac-111">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="10eac-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="10eac-112">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="10eac-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="10eac-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10eac-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10eac-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="10eac-114">See Also</span></span>  
 [<span data-ttu-id="10eac-115">Meta Veri Birleşimleri</span><span class="sxs-lookup"><span data-stu-id="10eac-115">Metadata Unions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-unions.md)
