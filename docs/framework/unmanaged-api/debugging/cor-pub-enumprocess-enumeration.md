---
title: COR_PUB_ENUMPROCESS Numaralandırması
ms.date: 03/30/2017
api_name:
- COR_PUB_ENUMPROCESS
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_PUB_ENUMPROCESS
helpviewer_keywords:
- COR_PUB_ENUMPROCESS enumeration [.NET Framework debugging]
ms.assetid: 5d3ada6e-feea-47da-a7ed-b664107c137f
topic_type:
- apiref
ms.openlocfilehash: f789105751ae2d498740ab60f326f9c0597483b2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73099205"
---
# <a name="cor_pub_enumprocess-enumeration"></a><span data-ttu-id="aede5-102">COR_PUB_ENUMPROCESS Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="aede5-102">COR_PUB_ENUMPROCESS Enumeration</span></span>
<span data-ttu-id="aede5-103">Numaralandırılacak işlemin türünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="aede5-103">Identifies the type of process to be enumerated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aede5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="aede5-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PUB_MANAGEDONLY    = 0x00000001  
} COR_PUB_ENUMPROCESS;  
```  
  
## <a name="members"></a><span data-ttu-id="aede5-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="aede5-105">Members</span></span>  
  
|<span data-ttu-id="aede5-106">Üye adı</span><span class="sxs-lookup"><span data-stu-id="aede5-106">Member name</span></span>|<span data-ttu-id="aede5-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aede5-107">Description</span></span>|  
|-----------------|-----------------|  
|`COR_PUB_MANAGEDONLY`|<span data-ttu-id="aede5-108">Yönetilen bir işlem.</span><span class="sxs-lookup"><span data-stu-id="aede5-108">A managed process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aede5-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="aede5-109">Remarks</span></span>  
 <span data-ttu-id="aede5-110">Yönetilmeyen hata ayıklama API 'sinin geçerli sürümü yalnızca yönetilen işlemi numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="aede5-110">The current version of the unmanaged debugging API enumerates only managed processes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aede5-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="aede5-111">Requirements</span></span>  
 <span data-ttu-id="aede5-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aede5-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aede5-113">**Üst bilgi:** CorPub. IDL, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="aede5-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="aede5-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="aede5-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aede5-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aede5-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aede5-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aede5-116">See also</span></span>

- [<span data-ttu-id="aede5-117">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="aede5-117">Debugging Enumerations</span></span>](debugging-enumerations.md)
