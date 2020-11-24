---
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
ms.openlocfilehash: c155373f7da47e904c94a44efa2fba42309d4218
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95671362"
---
# <a name="cornativelinktype-enumeration"></a><span data-ttu-id="8b9a9-102">CorNativeLinkType Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="8b9a9-102">CorNativeLinkType Enumeration</span></span>

<span data-ttu-id="8b9a9-103">Yerel kodda bağlantılı türü gösteren değerler sağlar.</span><span class="sxs-lookup"><span data-stu-id="8b9a9-103">Provides values that indicate the type linked in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b9a9-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="8b9a9-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="8b9a9-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="8b9a9-105">Members</span></span>  
  
|<span data-ttu-id="8b9a9-106">Üye</span><span class="sxs-lookup"><span data-stu-id="8b9a9-106">Member</span></span>|<span data-ttu-id="8b9a9-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8b9a9-107">Description</span></span>|  
|------------|-----------------|  
|`nltNone`|<span data-ttu-id="8b9a9-108">Anahtar sözcüklerin hiçbirinin belirtilmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8b9a9-108">Indicates that none of the keywords are specified.</span></span>|  
|`nltAnsi`|<span data-ttu-id="8b9a9-109">Bir ANSI anahtar sözcüğünün belirtildiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8b9a9-109">Indicates that an ANSI keyword is specified.</span></span>|  
|`nltUnicode`|<span data-ttu-id="8b9a9-110">Unicode anahtar sözcüğünün belirtildiğini belirtir</span><span class="sxs-lookup"><span data-stu-id="8b9a9-110">Indicates that a Unicode keyword is specified</span></span>|  
|`nltAuto`|<span data-ttu-id="8b9a9-111">Bir auto anahtar sözcüğünün belirtildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="8b9a9-111">Indicates that an auto keyword is specified.</span></span>|  
|`nltOle`|<span data-ttu-id="8b9a9-112">OLE anahtar sözcüğünün belirtildiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8b9a9-112">Indicates that an OLE keyword is specified.</span></span>|  
|`nltMaxValue`|<span data-ttu-id="8b9a9-113">Kullanılmadı.</span><span class="sxs-lookup"><span data-stu-id="8b9a9-113">Not used.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8b9a9-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8b9a9-114">Requirements</span></span>  

 <span data-ttu-id="8b9a9-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b9a9-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b9a9-116">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="8b9a9-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8b9a9-117">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="8b9a9-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8b9a9-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b9a9-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b9a9-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8b9a9-119">See also</span></span>

- [<span data-ttu-id="8b9a9-120">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="8b9a9-120">Metadata Enumerations</span></span>](metadata-enumerations.md)
