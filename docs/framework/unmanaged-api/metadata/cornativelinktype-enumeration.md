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
ms.openlocfilehash: 2bf8848851dc99c60b8c151ed34cd536fa9a8fed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33443267"
---
# <a name="cornativelinktype-enumeration"></a><span data-ttu-id="fe81e-102">CorNativeLinkType Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="fe81e-102">CorNativeLinkType Enumeration</span></span>
<span data-ttu-id="fe81e-103">Yerel kodda bağlı türünü gösteren değerleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="fe81e-103">Provides values that indicate the type linked in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe81e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fe81e-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="fe81e-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="fe81e-105">Members</span></span>  
  
|<span data-ttu-id="fe81e-106">Üye</span><span class="sxs-lookup"><span data-stu-id="fe81e-106">Member</span></span>|<span data-ttu-id="fe81e-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fe81e-107">Description</span></span>|  
|------------|-----------------|  
|`nltNone`|<span data-ttu-id="fe81e-108">Anahtar sözcükler hiçbiri belirtilen gösterir.</span><span class="sxs-lookup"><span data-stu-id="fe81e-108">Indicates that none of the keywords are specified.</span></span>|  
|`nltAnsi`|<span data-ttu-id="fe81e-109">ANSI anahtar sözcüğü belirttiğiniz gösterir.</span><span class="sxs-lookup"><span data-stu-id="fe81e-109">Indicates that an ANSI keyword is specified.</span></span>|  
|`nltUnicode`|<span data-ttu-id="fe81e-110">Unicode anahtar sözcüğü belirttiğiniz gösterir</span><span class="sxs-lookup"><span data-stu-id="fe81e-110">Indicates that a Unicode keyword is specified</span></span>|  
|`nltAuto`|<span data-ttu-id="fe81e-111">Auto anahtar sözcüğü belirttiğiniz gösterir.</span><span class="sxs-lookup"><span data-stu-id="fe81e-111">Indicates that an auto keyword is specified.</span></span>|  
|`nltOle`|<span data-ttu-id="fe81e-112">OLE anahtar sözcüğü belirttiğiniz gösterir.</span><span class="sxs-lookup"><span data-stu-id="fe81e-112">Indicates that an OLE keyword is specified.</span></span>|  
|`nltMaxValue`|<span data-ttu-id="fe81e-113">Kullanılmadı.</span><span class="sxs-lookup"><span data-stu-id="fe81e-113">Not used.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fe81e-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fe81e-114">Requirements</span></span>  
 <span data-ttu-id="fe81e-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe81e-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe81e-116">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="fe81e-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fe81e-117">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="fe81e-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fe81e-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe81e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe81e-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fe81e-119">See Also</span></span>  
 [<span data-ttu-id="fe81e-120">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="fe81e-120">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
