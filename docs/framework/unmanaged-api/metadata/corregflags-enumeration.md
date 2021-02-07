---
description: 'Daha fazla bilgi edinin: CorRegFlags numaralandırması'
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
ms.openlocfilehash: 534b7b4b170d1f586e967807c4cc8a9c82648e8b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753672"
---
# <a name="corregflags-enumeration"></a><span data-ttu-id="2ff3e-103">CorRegFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="2ff3e-103">CorRegFlags Enumeration</span></span>

<span data-ttu-id="2ff3e-104">Modül veya bileşik görüntü yüklerken kayıt için kullanılan bayrak değerlerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="2ff3e-104">Provides flag values used for registration when installing a module or composite image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ff3e-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="2ff3e-105">Syntax</span></span>  
  
```cpp  
typedef enum
{  
    regNoCopy  = 0x00000001,  
    regConfig  = 0x00000002,  
    regHasRefs = 0x00000004  
} CorRegFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="2ff3e-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="2ff3e-106">Members</span></span>  
  
|<span data-ttu-id="2ff3e-107">Üye</span><span class="sxs-lookup"><span data-stu-id="2ff3e-107">Member</span></span>|<span data-ttu-id="2ff3e-108">Description</span><span class="sxs-lookup"><span data-stu-id="2ff3e-108">Description</span></span>|  
|------------|-----------------|  
|`regNoCopy`|<span data-ttu-id="2ff3e-109">Dosyaların hedefe kopyalanmaması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="2ff3e-109">Specifies that files should not be copied into the destination.</span></span>|  
|`regConfig`|<span data-ttu-id="2ff3e-110">Modülün veya kompozit 'in bir yapılandırma olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="2ff3e-110">Specifies that the module or composite is a configuration.</span></span>|  
|`regHasRefs`|<span data-ttu-id="2ff3e-111">Modülün veya Composite sınıf başvurularına sahip olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="2ff3e-111">Specifies that the module or composite has class references.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2ff3e-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2ff3e-112">Requirements</span></span>  

 <span data-ttu-id="2ff3e-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ff3e-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ff3e-114">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="2ff3e-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2ff3e-115">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="2ff3e-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2ff3e-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ff3e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ff3e-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2ff3e-117">See also</span></span>

- [<span data-ttu-id="2ff3e-118">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="2ff3e-118">Metadata Enumerations</span></span>](metadata-enumerations.md)
