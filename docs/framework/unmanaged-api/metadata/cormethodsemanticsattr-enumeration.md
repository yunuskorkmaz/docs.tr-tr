---
title: CorMethodSemanticsAttr Numaralandırması
ms.date: 03/30/2017
api_name:
- CorMethodSemanticsAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorMethodSemanticsAttr
helpviewer_keywords:
- CorMethodSemanticsAttr enumeration [.NET Framework metadata]
ms.assetid: ca2af325-eb9d-4a91-90e4-267e45b98611
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f888c39160e52e550d07f58b9c5bcd11fd625658
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54564087"
---
# <a name="cormethodsemanticsattr-enumeration"></a><span data-ttu-id="80c5d-102">CorMethodSemanticsAttr Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="80c5d-102">CorMethodSemanticsAttr Enumeration</span></span>
<span data-ttu-id="80c5d-103">Bir yöntem ve özellik veya olay arasındaki ilişkiyi tanımlayan değerlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="80c5d-103">Contains values that describe the relationship between a method and an associated property or event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80c5d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="80c5d-104">Syntax</span></span>  
  
```  
typedef enum CorMethodSemanticsAttr {  
  
    msSetter    =   0x0001,  
    msGetter    =   0x0002,  
    msOther     =   0x0004,  
    msAddOn     =   0x0008,  
    msRemoveOn  =   0x0010,  
    msFire      =   0x0020,  
  
} CorMethodSemanticsAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="80c5d-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="80c5d-105">Members</span></span>  
  
|<span data-ttu-id="80c5d-106">Üye</span><span class="sxs-lookup"><span data-stu-id="80c5d-106">Member</span></span>|<span data-ttu-id="80c5d-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="80c5d-107">Description</span></span>|  
|------------|-----------------|  
|`msSetter`|<span data-ttu-id="80c5d-108">Yöntem olduğunu belirten bir `set` özellik erişimcisi.</span><span class="sxs-lookup"><span data-stu-id="80c5d-108">Specifies that the method is a `set` accessor for a property.</span></span>|  
|`msGetter`|<span data-ttu-id="80c5d-109">Yöntem olduğunu belirten bir `get` özellik erişimcisi.</span><span class="sxs-lookup"><span data-stu-id="80c5d-109">Specifies that the method is a `get` accessor for a property.</span></span>|  
|`msOther`|<span data-ttu-id="80c5d-110">Yöntemi, bir özellik veya olay burada tanımlanan dışındaki bir ilişki olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="80c5d-110">Specifies that the method has a relationship to a property or an event other than those defined here.</span></span>|  
|`msAddOn`|<span data-ttu-id="80c5d-111">Yöntem için bir olay işleyicisi yöntemleri ekler belirtir.</span><span class="sxs-lookup"><span data-stu-id="80c5d-111">Specifies that the method adds handler methods for an event.</span></span>|  
|`msRemoveOn`|<span data-ttu-id="80c5d-112">Yöntemi, bir olay işleyicisi yöntemleri kaldırır belirtir.</span><span class="sxs-lookup"><span data-stu-id="80c5d-112">Specifies that the method removes handler methods for an event.</span></span>|  
|`msFire`|<span data-ttu-id="80c5d-113">Yöntemin bir olay başlatır belirtir.</span><span class="sxs-lookup"><span data-stu-id="80c5d-113">Specifies that the method raises an event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="80c5d-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="80c5d-114">Requirements</span></span>  
 <span data-ttu-id="80c5d-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80c5d-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80c5d-116">**Üst bilgi:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="80c5d-116">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="80c5d-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80c5d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80c5d-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="80c5d-118">See also</span></span>
- [<span data-ttu-id="80c5d-119">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="80c5d-119">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
