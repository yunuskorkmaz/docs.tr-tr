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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62043296"
---
# <a name="ceesectionrelocextra-union"></a><span data-ttu-id="0f10a-102">CeeSectionRelocExtra Birleşimi</span><span class="sxs-lookup"><span data-stu-id="0f10a-102">CeeSectionRelocExtra Union</span></span>
<span data-ttu-id="0f10a-103">Tarafından kullanılan bir adres farkı gösteren [Iceegen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) bir bölümün dışında yeniden konumlandırmakta arabirimi.</span><span class="sxs-lookup"><span data-stu-id="0f10a-103">Represents an address offset that is used by the [ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) interface to relocate a section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f10a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0f10a-104">Syntax</span></span>  
  
```  
typedef union  {  
    USHORT highAdj;  
} CeeSectionRelocExtra;  
```  
  
## <a name="members"></a><span data-ttu-id="0f10a-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="0f10a-105">Members</span></span>  
  
|<span data-ttu-id="0f10a-106">Üye</span><span class="sxs-lookup"><span data-stu-id="0f10a-106">Member</span></span>|<span data-ttu-id="0f10a-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0f10a-107">Description</span></span>|  
|------------|-----------------|  
|`highAdj`|<span data-ttu-id="0f10a-108">Bölüm için adres üst ayarlama.</span><span class="sxs-lookup"><span data-stu-id="0f10a-108">The upper address adjustment for the section.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0f10a-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0f10a-109">Requirements</span></span>  
 <span data-ttu-id="0f10a-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f10a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f10a-111">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="0f10a-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0f10a-112">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="0f10a-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0f10a-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f10a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f10a-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0f10a-114">See also</span></span>

- [<span data-ttu-id="0f10a-115">Meta Veri Birleşimleri</span><span class="sxs-lookup"><span data-stu-id="0f10a-115">Metadata Unions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-unions.md)
