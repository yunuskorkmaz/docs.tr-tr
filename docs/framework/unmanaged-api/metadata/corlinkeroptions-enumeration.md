---
description: 'Daha fazla bilgi edinin: CorLinkerOptions numaralandırması'
title: CorLinkerOptions Numaralandırması
ms.date: 03/30/2017
api_name:
- CorLinkerOptions
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorLinkerOptions
helpviewer_keywords:
- CorLinkerOptions enumeration [.NET Framework metadata]
ms.assetid: a656aad6-cc7e-4994-8251-004a6a45e18f
topic_type:
- apiref
ms.openlocfilehash: 40f8ba6382fc937a072e01f9b3f6f89056f628db
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784437"
---
# <a name="corlinkeroptions-enumeration"></a><span data-ttu-id="d39ef-103">CorLinkerOptions Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="d39ef-103">CorLinkerOptions Enumeration</span></span>

<span data-ttu-id="d39ef-104">Meta veri bağlayıcı seçeneklerinin seçilecek bayrakları belirtir.</span><span class="sxs-lookup"><span data-stu-id="d39ef-104">Specifies flags to select options for the metadata linker.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d39ef-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="d39ef-105">Syntax</span></span>  
  
```cpp  
typedef enum CorLinkerOptions {  
    MDAssembly          = 0x00000000,  
    MDNetModule         = 0x00000001,  
} CorLinkerOptions;  
```  
  
## <a name="members"></a><span data-ttu-id="d39ef-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="d39ef-106">Members</span></span>  
  
|<span data-ttu-id="d39ef-107">Üye</span><span class="sxs-lookup"><span data-stu-id="d39ef-107">Member</span></span>|<span data-ttu-id="d39ef-108">Description</span><span class="sxs-lookup"><span data-stu-id="d39ef-108">Description</span></span>|  
|------------|-----------------|  
|`MDAssembly`|<span data-ttu-id="d39ef-109">Özel türler ve genel işlevler korunmaz.</span><span class="sxs-lookup"><span data-stu-id="d39ef-109">The private types and global functions are not preserved.</span></span>|  
|`MDNetModule`|<span data-ttu-id="d39ef-110">Özel türler ve genel işlevler korunur.</span><span class="sxs-lookup"><span data-stu-id="d39ef-110">The private types and global functions are preserved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d39ef-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d39ef-111">Requirements</span></span>  

 <span data-ttu-id="d39ef-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d39ef-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d39ef-113">**Üst bilgi:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="d39ef-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="d39ef-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d39ef-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d39ef-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d39ef-115">See also</span></span>

- [<span data-ttu-id="d39ef-116">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="d39ef-116">Metadata Enumerations</span></span>](metadata-enumerations.md)
