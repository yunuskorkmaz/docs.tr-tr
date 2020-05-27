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
ms.openlocfilehash: d8d7a43848929e49a8cb48fb957f37213ac78f2e
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007357"
---
# <a name="corregflags-enumeration"></a><span data-ttu-id="0e1a6-102">CorRegFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="0e1a6-102">CorRegFlags Enumeration</span></span>
<span data-ttu-id="0e1a6-103">Modül veya bileşik görüntü yüklerken kayıt için kullanılan bayrak değerlerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="0e1a6-103">Provides flag values used for registration when installing a module or composite image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e1a6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0e1a6-104">Syntax</span></span>  
  
```cpp  
typedef enum
{  
    regNoCopy  = 0x00000001,  
    regConfig  = 0x00000002,  
    regHasRefs = 0x00000004  
} CorRegFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="0e1a6-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="0e1a6-105">Members</span></span>  
  
|<span data-ttu-id="0e1a6-106">Üye</span><span class="sxs-lookup"><span data-stu-id="0e1a6-106">Member</span></span>|<span data-ttu-id="0e1a6-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0e1a6-107">Description</span></span>|  
|------------|-----------------|  
|`regNoCopy`|<span data-ttu-id="0e1a6-108">Dosyaların hedefe kopyalanmaması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0e1a6-108">Specifies that files should not be copied into the destination.</span></span>|  
|`regConfig`|<span data-ttu-id="0e1a6-109">Modülün veya kompozit 'in bir yapılandırma olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="0e1a6-109">Specifies that the module or composite is a configuration.</span></span>|  
|`regHasRefs`|<span data-ttu-id="0e1a6-110">Modülün veya Composite sınıf başvurularına sahip olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="0e1a6-110">Specifies that the module or composite has class references.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0e1a6-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0e1a6-111">Requirements</span></span>  
 <span data-ttu-id="0e1a6-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e1a6-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e1a6-113">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="0e1a6-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0e1a6-114">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="0e1a6-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0e1a6-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e1a6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e1a6-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0e1a6-116">See also</span></span>

- [<span data-ttu-id="0e1a6-117">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="0e1a6-117">Metadata Enumerations</span></span>](metadata-enumerations.md)
