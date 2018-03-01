---
title: "CorNativeLinkType Numaralandırması"
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
- CorNativeLinkType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorNativeLinkType
helpviewer_keywords:
- CorNativeLinkType enumeration [.NET Framework metadata]
ms.assetid: 4f86ff37-2dab-4e64-819a-76b3bfe828ff
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f19a4366958249881c1f4c33919f239f33c21b21
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="cornativelinktype-enumeration"></a><span data-ttu-id="c2f45-102">CorNativeLinkType Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="c2f45-102">CorNativeLinkType Enumeration</span></span>
<span data-ttu-id="c2f45-103">Yerel kodda bağlı türünü gösteren değerleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="c2f45-103">Provides values that indicate the type linked in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2f45-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c2f45-104">Syntax</span></span>  
  
```  
typedef enum   
{  
    nltNone       = 1,  
    nltAnsi       = 2,  
    nltUnicode    = 3,  
    nltAuto       = 4,  
    nltOle        = 5,  
    nltMaxValue   = 7  
} CorNativeLinkType;  
```  
  
## <a name="members"></a><span data-ttu-id="c2f45-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="c2f45-105">Members</span></span>  
  
|<span data-ttu-id="c2f45-106">Üye</span><span class="sxs-lookup"><span data-stu-id="c2f45-106">Member</span></span>|<span data-ttu-id="c2f45-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c2f45-107">Description</span></span>|  
|------------|-----------------|  
|`nltNone`|<span data-ttu-id="c2f45-108">Anahtar sözcükler hiçbiri belirtilen gösterir.</span><span class="sxs-lookup"><span data-stu-id="c2f45-108">Indicates that none of the keywords are specified.</span></span>|  
|`nltAnsi`|<span data-ttu-id="c2f45-109">ANSI anahtar sözcüğü belirttiğiniz gösterir.</span><span class="sxs-lookup"><span data-stu-id="c2f45-109">Indicates that an ANSI keyword is specified.</span></span>|  
|`nltUnicode`|<span data-ttu-id="c2f45-110">Unicode anahtar sözcüğü belirttiğiniz gösterir</span><span class="sxs-lookup"><span data-stu-id="c2f45-110">Indicates that a Unicode keyword is specified</span></span>|  
|`nltAuto`|<span data-ttu-id="c2f45-111">Auto anahtar sözcüğü belirttiğiniz gösterir.</span><span class="sxs-lookup"><span data-stu-id="c2f45-111">Indicates that an auto keyword is specified.</span></span>|  
|`nltOle`|<span data-ttu-id="c2f45-112">OLE anahtar sözcüğü belirttiğiniz gösterir.</span><span class="sxs-lookup"><span data-stu-id="c2f45-112">Indicates that an OLE keyword is specified.</span></span>|  
|`nltMaxValue`|<span data-ttu-id="c2f45-113">Kullanılmadı.</span><span class="sxs-lookup"><span data-stu-id="c2f45-113">Not used.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c2f45-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c2f45-114">Requirements</span></span>  
 <span data-ttu-id="c2f45-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2f45-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2f45-116">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c2f45-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c2f45-117">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="c2f45-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c2f45-118">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2f45-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2f45-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c2f45-119">See Also</span></span>  
 [<span data-ttu-id="c2f45-120">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="c2f45-120">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
