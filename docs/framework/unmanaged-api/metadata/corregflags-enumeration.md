---
title: CorRegFlags Numaralandırması
ms.date: 03/30/2017
api_name:
- CorRegFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorRegFlags
helpviewer_keywords:
- CorRegFlags enumeration [.NET Framework metadata]
ms.assetid: 8d3080ee-39fe-4c57-8950-51323632d045
topic_type:
- apiref
ms.openlocfilehash: 79a9e4513a98a29edc11cc76c599f03c9c3a72b4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450118"
---
# <a name="corregflags-enumeration"></a><span data-ttu-id="4bbe5-102">CorRegFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="4bbe5-102">CorRegFlags Enumeration</span></span>
<span data-ttu-id="4bbe5-103">Provides flag values used for registration when installing a module or composite image.</span><span class="sxs-lookup"><span data-stu-id="4bbe5-103">Provides flag values used for registration when installing a module or composite image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4bbe5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4bbe5-104">Syntax</span></span>  
  
```cpp  
typedef enum   
{  
    regNoCopy  = 0x00000001,  
    regConfig  = 0x00000002,  
    regHasRefs = 0x00000004  
} CorRegFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="4bbe5-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="4bbe5-105">Members</span></span>  
  
|<span data-ttu-id="4bbe5-106">Üye</span><span class="sxs-lookup"><span data-stu-id="4bbe5-106">Member</span></span>|<span data-ttu-id="4bbe5-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4bbe5-107">Description</span></span>|  
|------------|-----------------|  
|`regNoCopy`|<span data-ttu-id="4bbe5-108">Specifies that files should not be copied into the destination.</span><span class="sxs-lookup"><span data-stu-id="4bbe5-108">Specifies that files should not be copied into the destination.</span></span>|  
|`regConfig`|<span data-ttu-id="4bbe5-109">Specifies that the module or composite is a configuration.</span><span class="sxs-lookup"><span data-stu-id="4bbe5-109">Specifies that the module or composite is a configuration.</span></span>|  
|`regHasRefs`|<span data-ttu-id="4bbe5-110">Specifies that the module or composite has class references.</span><span class="sxs-lookup"><span data-stu-id="4bbe5-110">Specifies that the module or composite has class references.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4bbe5-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4bbe5-111">Requirements</span></span>  
 <span data-ttu-id="4bbe5-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4bbe5-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4bbe5-113">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4bbe5-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4bbe5-114">**Library:** Included as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4bbe5-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4bbe5-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4bbe5-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bbe5-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4bbe5-116">See also</span></span>

- [<span data-ttu-id="4bbe5-117">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="4bbe5-117">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
