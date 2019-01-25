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
ms.openlocfilehash: 0f946179fc31adebc8e8fc67c394e0b55a876f49
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54641336"
---
# <a name="cornativelinktype-enumeration"></a><span data-ttu-id="8b06a-102">CorNativeLinkType Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="8b06a-102">CorNativeLinkType Enumeration</span></span>
<span data-ttu-id="8b06a-103">Yerel kodda bağlı türü gösteren değerleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="8b06a-103">Provides values that indicate the type linked in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b06a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8b06a-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="8b06a-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="8b06a-105">Members</span></span>  
  
|<span data-ttu-id="8b06a-106">Üye</span><span class="sxs-lookup"><span data-stu-id="8b06a-106">Member</span></span>|<span data-ttu-id="8b06a-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8b06a-107">Description</span></span>|  
|------------|-----------------|  
|`nltNone`|<span data-ttu-id="8b06a-108">Anahtar sözcükler hiçbiri belirtilen gösterir.</span><span class="sxs-lookup"><span data-stu-id="8b06a-108">Indicates that none of the keywords are specified.</span></span>|  
|`nltAnsi`|<span data-ttu-id="8b06a-109">Bir ANSI anahtar sözcüğü belirttiğiniz gösterir.</span><span class="sxs-lookup"><span data-stu-id="8b06a-109">Indicates that an ANSI keyword is specified.</span></span>|  
|`nltUnicode`|<span data-ttu-id="8b06a-110">Unicode anahtar sözcüğü belirttiğiniz gösterir</span><span class="sxs-lookup"><span data-stu-id="8b06a-110">Indicates that a Unicode keyword is specified</span></span>|  
|`nltAuto`|<span data-ttu-id="8b06a-111">Auto anahtar sözcüğü bir belirttiğiniz gösterir.</span><span class="sxs-lookup"><span data-stu-id="8b06a-111">Indicates that an auto keyword is specified.</span></span>|  
|`nltOle`|<span data-ttu-id="8b06a-112">Bir OLE anahtar sözcüğü belirttiğiniz gösterir.</span><span class="sxs-lookup"><span data-stu-id="8b06a-112">Indicates that an OLE keyword is specified.</span></span>|  
|`nltMaxValue`|<span data-ttu-id="8b06a-113">Kullanılmadı.</span><span class="sxs-lookup"><span data-stu-id="8b06a-113">Not used.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8b06a-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8b06a-114">Requirements</span></span>  
 <span data-ttu-id="8b06a-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b06a-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b06a-116">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="8b06a-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8b06a-117">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="8b06a-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8b06a-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b06a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b06a-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8b06a-119">See also</span></span>
- [<span data-ttu-id="8b06a-120">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="8b06a-120">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
