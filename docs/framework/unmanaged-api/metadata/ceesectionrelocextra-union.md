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
ms.openlocfilehash: 9d6a5673c2aaf287131274b0c590f00a69c64fed
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54517155"
---
# <a name="ceesectionrelocextra-union"></a><span data-ttu-id="bbb9b-102">CeeSectionRelocExtra Birleşimi</span><span class="sxs-lookup"><span data-stu-id="bbb9b-102">CeeSectionRelocExtra Union</span></span>
<span data-ttu-id="bbb9b-103">Tarafından kullanılan bir adres farkı gösteren [Iceegen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) bir bölümün dışında yeniden konumlandırmakta arabirimi.</span><span class="sxs-lookup"><span data-stu-id="bbb9b-103">Represents an address offset that is used by the [ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) interface to relocate a section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbb9b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bbb9b-104">Syntax</span></span>  
  
```  
typedef union  {  
    USHORT highAdj;  
} CeeSectionRelocExtra;  
```  
  
## <a name="members"></a><span data-ttu-id="bbb9b-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="bbb9b-105">Members</span></span>  
  
|<span data-ttu-id="bbb9b-106">Üye</span><span class="sxs-lookup"><span data-stu-id="bbb9b-106">Member</span></span>|<span data-ttu-id="bbb9b-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bbb9b-107">Description</span></span>|  
|------------|-----------------|  
|`highAdj`|<span data-ttu-id="bbb9b-108">Bölüm için adres üst ayarlama.</span><span class="sxs-lookup"><span data-stu-id="bbb9b-108">The upper address adjustment for the section.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bbb9b-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bbb9b-109">Requirements</span></span>  
 <span data-ttu-id="bbb9b-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bbb9b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bbb9b-111">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="bbb9b-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bbb9b-112">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="bbb9b-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bbb9b-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bbb9b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbb9b-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bbb9b-114">See also</span></span>
- [<span data-ttu-id="bbb9b-115">Meta Veri Birleşimleri</span><span class="sxs-lookup"><span data-stu-id="bbb9b-115">Metadata Unions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-unions.md)
