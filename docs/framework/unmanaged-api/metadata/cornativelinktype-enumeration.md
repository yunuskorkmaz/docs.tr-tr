---
description: 'Daha fazla bilgi edinin: Cornativelınktype numaralandırması'
title: CorNativeLinkType Numaralandırması
ms.date: 03/30/2017
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
ms.openlocfilehash: 40efc75a793da8b024eff3d7c2c620123eca08b2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784346"
---
# <a name="cornativelinktype-enumeration"></a><span data-ttu-id="9cf13-103">CorNativeLinkType Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="9cf13-103">CorNativeLinkType Enumeration</span></span>

<span data-ttu-id="9cf13-104">Yerel kodda bağlantılı türü gösteren değerler sağlar.</span><span class="sxs-lookup"><span data-stu-id="9cf13-104">Provides values that indicate the type linked in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9cf13-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="9cf13-105">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="9cf13-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="9cf13-106">Members</span></span>  
  
|<span data-ttu-id="9cf13-107">Üye</span><span class="sxs-lookup"><span data-stu-id="9cf13-107">Member</span></span>|<span data-ttu-id="9cf13-108">Description</span><span class="sxs-lookup"><span data-stu-id="9cf13-108">Description</span></span>|  
|------------|-----------------|  
|`nltNone`|<span data-ttu-id="9cf13-109">Anahtar sözcüklerin hiçbirinin belirtilmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9cf13-109">Indicates that none of the keywords are specified.</span></span>|  
|`nltAnsi`|<span data-ttu-id="9cf13-110">Bir ANSI anahtar sözcüğünün belirtildiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9cf13-110">Indicates that an ANSI keyword is specified.</span></span>|  
|`nltUnicode`|<span data-ttu-id="9cf13-111">Unicode anahtar sözcüğünün belirtildiğini belirtir</span><span class="sxs-lookup"><span data-stu-id="9cf13-111">Indicates that a Unicode keyword is specified</span></span>|  
|`nltAuto`|<span data-ttu-id="9cf13-112">Bir auto anahtar sözcüğünün belirtildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="9cf13-112">Indicates that an auto keyword is specified.</span></span>|  
|`nltOle`|<span data-ttu-id="9cf13-113">OLE anahtar sözcüğünün belirtildiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9cf13-113">Indicates that an OLE keyword is specified.</span></span>|  
|`nltMaxValue`|<span data-ttu-id="9cf13-114">Kullanılmadı.</span><span class="sxs-lookup"><span data-stu-id="9cf13-114">Not used.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9cf13-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9cf13-115">Requirements</span></span>  

 <span data-ttu-id="9cf13-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9cf13-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9cf13-117">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="9cf13-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9cf13-118">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="9cf13-118">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9cf13-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9cf13-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cf13-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9cf13-120">See also</span></span>

- [<span data-ttu-id="9cf13-121">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="9cf13-121">Metadata Enumerations</span></span>](metadata-enumerations.md)
