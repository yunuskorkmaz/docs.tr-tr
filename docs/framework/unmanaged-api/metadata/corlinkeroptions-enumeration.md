---
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
ms.openlocfilehash: 188301d31b2fcfaf7b1c6139111e8f1296ccf7e5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677251"
---
# <a name="corlinkeroptions-enumeration"></a><span data-ttu-id="ef0ae-102">CorLinkerOptions Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="ef0ae-102">CorLinkerOptions Enumeration</span></span>

<span data-ttu-id="ef0ae-103">Meta veri bağlayıcı seçeneklerinin seçilecek bayrakları belirtir.</span><span class="sxs-lookup"><span data-stu-id="ef0ae-103">Specifies flags to select options for the metadata linker.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef0ae-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="ef0ae-104">Syntax</span></span>  
  
```cpp  
typedef enum CorLinkerOptions {  
    MDAssembly          = 0x00000000,  
    MDNetModule         = 0x00000001,  
} CorLinkerOptions;  
```  
  
## <a name="members"></a><span data-ttu-id="ef0ae-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="ef0ae-105">Members</span></span>  
  
|<span data-ttu-id="ef0ae-106">Üye</span><span class="sxs-lookup"><span data-stu-id="ef0ae-106">Member</span></span>|<span data-ttu-id="ef0ae-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ef0ae-107">Description</span></span>|  
|------------|-----------------|  
|`MDAssembly`|<span data-ttu-id="ef0ae-108">Özel türler ve genel işlevler korunmaz.</span><span class="sxs-lookup"><span data-stu-id="ef0ae-108">The private types and global functions are not preserved.</span></span>|  
|`MDNetModule`|<span data-ttu-id="ef0ae-109">Özel türler ve genel işlevler korunur.</span><span class="sxs-lookup"><span data-stu-id="ef0ae-109">The private types and global functions are preserved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ef0ae-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ef0ae-110">Requirements</span></span>  

 <span data-ttu-id="ef0ae-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ef0ae-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef0ae-112">**Üst bilgi:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="ef0ae-112">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="ef0ae-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef0ae-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef0ae-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ef0ae-114">See also</span></span>

- [<span data-ttu-id="ef0ae-115">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="ef0ae-115">Metadata Enumerations</span></span>](metadata-enumerations.md)
