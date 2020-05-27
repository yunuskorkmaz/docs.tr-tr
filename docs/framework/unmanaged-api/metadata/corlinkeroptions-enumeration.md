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
ms.openlocfilehash: fe5ffbab93df7168015e2a31d6e32ec45dce0960
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007695"
---
# <a name="corlinkeroptions-enumeration"></a><span data-ttu-id="42787-102">CorLinkerOptions Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="42787-102">CorLinkerOptions Enumeration</span></span>
<span data-ttu-id="42787-103">Meta veri bağlayıcı seçeneklerinin seçilecek bayrakları belirtir.</span><span class="sxs-lookup"><span data-stu-id="42787-103">Specifies flags to select options for the metadata linker.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42787-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="42787-104">Syntax</span></span>  
  
```cpp  
typedef enum CorLinkerOptions {  
    MDAssembly          = 0x00000000,  
    MDNetModule         = 0x00000001,  
} CorLinkerOptions;  
```  
  
## <a name="members"></a><span data-ttu-id="42787-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="42787-105">Members</span></span>  
  
|<span data-ttu-id="42787-106">Üye</span><span class="sxs-lookup"><span data-stu-id="42787-106">Member</span></span>|<span data-ttu-id="42787-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="42787-107">Description</span></span>|  
|------------|-----------------|  
|`MDAssembly`|<span data-ttu-id="42787-108">Özel türler ve genel işlevler korunmaz.</span><span class="sxs-lookup"><span data-stu-id="42787-108">The private types and global functions are not preserved.</span></span>|  
|`MDNetModule`|<span data-ttu-id="42787-109">Özel türler ve genel işlevler korunur.</span><span class="sxs-lookup"><span data-stu-id="42787-109">The private types and global functions are preserved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="42787-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="42787-110">Requirements</span></span>  
 <span data-ttu-id="42787-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42787-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42787-112">**Üst bilgi:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="42787-112">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="42787-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42787-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42787-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="42787-114">See also</span></span>

- [<span data-ttu-id="42787-115">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="42787-115">Metadata Enumerations</span></span>](metadata-enumerations.md)
