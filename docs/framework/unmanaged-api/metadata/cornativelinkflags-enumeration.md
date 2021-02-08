---
description: 'Daha fazla bilgi edinin: CorNativeLinkFlags numaralandırması'
title: CorNativeLinkFlags Numaralandırması
ms.date: 03/30/2017
api_name:
- CorNativeLinkFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorNativeLinkFlags
helpviewer_keywords:
- CorNativeLinkFlags enumeration [.NET Framework metadata]
ms.assetid: 8027df7c-cfad-4724-bda0-7538d9519070
topic_type:
- apiref
ms.openlocfilehash: 9025d192ca92c1160c1b072b0dcfe045fa3ceab7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784359"
---
# <a name="cornativelinkflags-enumeration"></a><span data-ttu-id="274e0-103">CorNativeLinkFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="274e0-103">CorNativeLinkFlags Enumeration</span></span>

<span data-ttu-id="274e0-104">Yerel kod bağlanırken bağlayıcı tarafından kullanılan bayrak değerlerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="274e0-104">Provides flag values used by the linker when linking native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="274e0-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="274e0-105">Syntax</span></span>  
  
```cpp  
typedef enum  
{  
    nlfNone         = 0x00,  
    nlfLastError    = 0x01,  
    nlfNoMangle     = 0x02,  
    nlfMaxValue     = 0x03  
} CorNativeLinkFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="274e0-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="274e0-106">Members</span></span>  
  
|<span data-ttu-id="274e0-107">Üye</span><span class="sxs-lookup"><span data-stu-id="274e0-107">Member</span></span>|<span data-ttu-id="274e0-108">Description</span><span class="sxs-lookup"><span data-stu-id="274e0-108">Description</span></span>|  
|------------|-----------------|  
|`nlfNone`|<span data-ttu-id="274e0-109">Bayrak olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="274e0-109">Indicates no flags.</span></span>|  
|`nlfLastError`|<span data-ttu-id="274e0-110">Bir `setLastError` anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="274e0-110">Indicates a `setLastError` keyword.</span></span>|  
|`nlfNoMangle`|<span data-ttu-id="274e0-111">Bir `nomangle` anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="274e0-111">Indicates a `nomangle` keyword.</span></span>|  
|`nlfMaxValue`|<span data-ttu-id="274e0-112">Kullanılmadı.</span><span class="sxs-lookup"><span data-stu-id="274e0-112">Not used.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="274e0-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="274e0-113">Requirements</span></span>  

 <span data-ttu-id="274e0-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="274e0-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="274e0-115">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="274e0-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="274e0-116">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="274e0-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="274e0-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="274e0-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="274e0-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="274e0-118">See also</span></span>

- [<span data-ttu-id="274e0-119">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="274e0-119">Metadata Enumerations</span></span>](metadata-enumerations.md)
