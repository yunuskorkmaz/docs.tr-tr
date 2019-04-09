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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59182279"
---
# <a name="ceesectionrelocextra-union"></a><span data-ttu-id="892e6-102">CeeSectionRelocExtra Birleşimi</span><span class="sxs-lookup"><span data-stu-id="892e6-102">CeeSectionRelocExtra Union</span></span>
<span data-ttu-id="892e6-103">Tarafından kullanılan bir adres farkı gösteren [Iceegen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) bir bölümün dışında yeniden konumlandırmakta arabirimi.</span><span class="sxs-lookup"><span data-stu-id="892e6-103">Represents an address offset that is used by the [ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) interface to relocate a section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="892e6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="892e6-104">Syntax</span></span>  
  
```  
typedef union  {  
    USHORT highAdj;  
} CeeSectionRelocExtra;  
```  
  
## <a name="members"></a><span data-ttu-id="892e6-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="892e6-105">Members</span></span>  
  
|<span data-ttu-id="892e6-106">Üye</span><span class="sxs-lookup"><span data-stu-id="892e6-106">Member</span></span>|<span data-ttu-id="892e6-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="892e6-107">Description</span></span>|  
|------------|-----------------|  
|`highAdj`|<span data-ttu-id="892e6-108">Bölüm için adres üst ayarlama.</span><span class="sxs-lookup"><span data-stu-id="892e6-108">The upper address adjustment for the section.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="892e6-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="892e6-109">Requirements</span></span>  
 <span data-ttu-id="892e6-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="892e6-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="892e6-111">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="892e6-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="892e6-112">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="892e6-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="892e6-113">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="892e6-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="892e6-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="892e6-114">See also</span></span>

- [<span data-ttu-id="892e6-115">Meta Veri Birleşmeleri</span><span class="sxs-lookup"><span data-stu-id="892e6-115">Metadata Unions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-unions.md)
