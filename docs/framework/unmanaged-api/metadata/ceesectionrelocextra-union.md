---
title: "CeeSectionRelocExtra Birleşimi"
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9591967dc70d54bd020414077fcc57b8007db9d2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ceesectionrelocextra-union"></a><span data-ttu-id="430ab-102">CeeSectionRelocExtra Birleşimi</span><span class="sxs-lookup"><span data-stu-id="430ab-102">CeeSectionRelocExtra Union</span></span>
<span data-ttu-id="430ab-103">Tarafından kullanılan bir adres farkı temsil eden [Iceegen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) bir bölümü yeniden konumlandırmak için arabirim.</span><span class="sxs-lookup"><span data-stu-id="430ab-103">Represents an address offset that is used by the [ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) interface to relocate a section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="430ab-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="430ab-104">Syntax</span></span>  
  
```  
typedef union  {  
    USHORT highAdj;  
} CeeSectionRelocExtra;  
```  
  
## <a name="members"></a><span data-ttu-id="430ab-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="430ab-105">Members</span></span>  
  
|<span data-ttu-id="430ab-106">Üye</span><span class="sxs-lookup"><span data-stu-id="430ab-106">Member</span></span>|<span data-ttu-id="430ab-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="430ab-107">Description</span></span>|  
|------------|-----------------|  
|`highAdj`|<span data-ttu-id="430ab-108">Bölümü için adres üst ayarlama.</span><span class="sxs-lookup"><span data-stu-id="430ab-108">The upper address adjustment for the section.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="430ab-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="430ab-109">Requirements</span></span>  
 <span data-ttu-id="430ab-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="430ab-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="430ab-111">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="430ab-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="430ab-112">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="430ab-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="430ab-113">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="430ab-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="430ab-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="430ab-114">See Also</span></span>  
 [<span data-ttu-id="430ab-115">Meta Veri Birleşimleri</span><span class="sxs-lookup"><span data-stu-id="430ab-115">Metadata Unions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-unions.md)
