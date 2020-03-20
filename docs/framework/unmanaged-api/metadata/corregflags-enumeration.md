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
ms.openlocfilehash: 8fe6216e11a64ea182d796247d888b862b1e8377
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177936"
---
# <a name="corregflags-enumeration"></a><span data-ttu-id="ffe8e-102">CorRegFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="ffe8e-102">CorRegFlags Enumeration</span></span>
<span data-ttu-id="ffe8e-103">Modül veya bileşik görüntü yüklerken kayıt için kullanılan bayrak değerlerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="ffe8e-103">Provides flag values used for registration when installing a module or composite image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ffe8e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ffe8e-104">Syntax</span></span>  
  
```cpp  
typedef enum
{  
    regNoCopy  = 0x00000001,  
    regConfig  = 0x00000002,  
    regHasRefs = 0x00000004  
} CorRegFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="ffe8e-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="ffe8e-105">Members</span></span>  
  
|<span data-ttu-id="ffe8e-106">Üye</span><span class="sxs-lookup"><span data-stu-id="ffe8e-106">Member</span></span>|<span data-ttu-id="ffe8e-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ffe8e-107">Description</span></span>|  
|------------|-----------------|  
|`regNoCopy`|<span data-ttu-id="ffe8e-108">Dosyaların hedefe kopyalanmaması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ffe8e-108">Specifies that files should not be copied into the destination.</span></span>|  
|`regConfig`|<span data-ttu-id="ffe8e-109">Modülün veya bileşimin bir yapılandırma olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="ffe8e-109">Specifies that the module or composite is a configuration.</span></span>|  
|`regHasRefs`|<span data-ttu-id="ffe8e-110">Modülün veya bileşimin sınıf başvuruları olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="ffe8e-110">Specifies that the module or composite has class references.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ffe8e-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ffe8e-111">Requirements</span></span>  
 <span data-ttu-id="ffe8e-112">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ffe8e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ffe8e-113">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ffe8e-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ffe8e-114">**Kütüphane:** MsCorEE.dll bir kaynak olarak dahil</span><span class="sxs-lookup"><span data-stu-id="ffe8e-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ffe8e-115">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ffe8e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffe8e-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ffe8e-116">See also</span></span>

- [<span data-ttu-id="ffe8e-117">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="ffe8e-117">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
