---
title: CorThreadSafetyOptions Numaralandırması
ms.date: 03/30/2017
api_name:
- CorThreadSafetyOptions
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorThreadSafetyOptions
helpviewer_keywords:
- CorThreadSafetyOptions enumeration [.NET Framework metadata]
ms.assetid: dae07d9b-df51-488c-b17e-52d6e48217bd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3407fcac420b8129dd39eabf84aec84b58651944
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33442851"
---
# <a name="corthreadsafetyoptions-enumeration"></a><span data-ttu-id="f2006-102">CorThreadSafetyOptions Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="f2006-102">CorThreadSafetyOptions Enumeration</span></span>
<span data-ttu-id="f2006-103">İş parçacığı güvenliği seçeneklerini seçmek için bayrakları belirtir.</span><span class="sxs-lookup"><span data-stu-id="f2006-103">Specifies flags to select options for thread safety.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2006-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f2006-104">Syntax</span></span>  
  
```  
typedef enum CorThreadSafetyOptions {  
    MDThreadSafetyDefault       = 0x00000000,  
    MDThreadSafetyOff           = 0x00000000,  
    MDThreadSafetyOn            = 0x00000001,  
} CorThreadSafetyOptions;  
```  
  
## <a name="members"></a><span data-ttu-id="f2006-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="f2006-105">Members</span></span>  
  
|<span data-ttu-id="f2006-106">Üye</span><span class="sxs-lookup"><span data-stu-id="f2006-106">Member</span></span>|<span data-ttu-id="f2006-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f2006-107">Description</span></span>|  
|------------|-----------------|  
|`MDThreadSatetyDefault`|<span data-ttu-id="f2006-108">Varsayılan değer.</span><span class="sxs-lookup"><span data-stu-id="f2006-108">Default value.</span></span> <span data-ttu-id="f2006-109">Aynı `MDThreadSatetyOff`.</span><span class="sxs-lookup"><span data-stu-id="f2006-109">Same as `MDThreadSatetyOff`.</span></span>|  
|`MDThreadSatetyOff`|<span data-ttu-id="f2006-110">Okuyucu/Yazıcı kilit ayarlanamaz gösterir.</span><span class="sxs-lookup"><span data-stu-id="f2006-110">Indicates that a reader/writer lock cannot be set.</span></span>|  
|`MDThreadSatetyOn`|<span data-ttu-id="f2006-111">Okuyucu/Yazıcı kilit ayarlanabilir gösterir.</span><span class="sxs-lookup"><span data-stu-id="f2006-111">Indicates that a reader/writer lock can be set.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f2006-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f2006-112">Requirements</span></span>  
 <span data-ttu-id="f2006-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2006-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2006-114">**Başlık:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="f2006-114">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="f2006-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2006-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2006-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f2006-116">See Also</span></span>  
 [<span data-ttu-id="f2006-117">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="f2006-117">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
