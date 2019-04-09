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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 66d650adb39a9c7dade0936ec671ae5a8b4aeecd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59170082"
---
# <a name="cornativelinktype-enumeration"></a><span data-ttu-id="90a2e-102">CorNativeLinkType Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="90a2e-102">CorNativeLinkType Enumeration</span></span>
<span data-ttu-id="90a2e-103">Yerel kodda bağlı türü gösteren değerleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="90a2e-103">Provides values that indicate the type linked in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90a2e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="90a2e-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="90a2e-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="90a2e-105">Members</span></span>  
  
|<span data-ttu-id="90a2e-106">Üye</span><span class="sxs-lookup"><span data-stu-id="90a2e-106">Member</span></span>|<span data-ttu-id="90a2e-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="90a2e-107">Description</span></span>|  
|------------|-----------------|  
|`nltNone`|<span data-ttu-id="90a2e-108">Anahtar sözcükler hiçbiri belirtilen gösterir.</span><span class="sxs-lookup"><span data-stu-id="90a2e-108">Indicates that none of the keywords are specified.</span></span>|  
|`nltAnsi`|<span data-ttu-id="90a2e-109">Bir ANSI anahtar sözcüğü belirttiğiniz gösterir.</span><span class="sxs-lookup"><span data-stu-id="90a2e-109">Indicates that an ANSI keyword is specified.</span></span>|  
|`nltUnicode`|<span data-ttu-id="90a2e-110">Unicode anahtar sözcüğü belirttiğiniz gösterir</span><span class="sxs-lookup"><span data-stu-id="90a2e-110">Indicates that a Unicode keyword is specified</span></span>|  
|`nltAuto`|<span data-ttu-id="90a2e-111">Auto anahtar sözcüğü bir belirttiğiniz gösterir.</span><span class="sxs-lookup"><span data-stu-id="90a2e-111">Indicates that an auto keyword is specified.</span></span>|  
|`nltOle`|<span data-ttu-id="90a2e-112">Bir OLE anahtar sözcüğü belirttiğiniz gösterir.</span><span class="sxs-lookup"><span data-stu-id="90a2e-112">Indicates that an OLE keyword is specified.</span></span>|  
|`nltMaxValue`|<span data-ttu-id="90a2e-113">Kullanılmadı.</span><span class="sxs-lookup"><span data-stu-id="90a2e-113">Not used.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="90a2e-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="90a2e-114">Requirements</span></span>  
 <span data-ttu-id="90a2e-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="90a2e-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90a2e-116">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="90a2e-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="90a2e-117">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="90a2e-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="90a2e-118">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="90a2e-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="90a2e-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="90a2e-119">See also</span></span>

- [<span data-ttu-id="90a2e-120">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="90a2e-120">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
