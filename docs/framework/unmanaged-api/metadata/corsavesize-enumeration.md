---
title: CorSaveSize Numaralandırması
ms.date: 03/30/2017
api_name:
- CorSaveSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSaveSize
helpviewer_keywords:
- CorSaveSize enumeration [.NET Framework metadata]
ms.assetid: eb95ce39-5688-43c1-a34d-578794b32faa
topic_type:
- apiref
ms.openlocfilehash: 13a4364244f7d0076d77d14c3e3ef161e3872bcb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176142"
---
# <a name="corsavesize-enumeration"></a><span data-ttu-id="64278-102">CorSaveSize Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="64278-102">CorSaveSize Enumeration</span></span>
<span data-ttu-id="64278-103">Bir kaydet işlemi nin boyutunu sorgularken gereken kesinlik düzeyini gösteren değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="64278-103">Contains values indicating the level of precision required when querying for the size of a save operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64278-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="64278-104">Syntax</span></span>  
  
```cpp  
typedef enum CorSaveSize {  
    cssAccurate                = 0x0000,
    cssQuick                   = 0x0001,
    cssDiscardTransientCAs     = 0x0002  
} CorSaveSize;  
```  
  
## <a name="members"></a><span data-ttu-id="64278-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="64278-105">Members</span></span>  
  
|<span data-ttu-id="64278-106">Üye</span><span class="sxs-lookup"><span data-stu-id="64278-106">Member</span></span>|<span data-ttu-id="64278-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="64278-107">Description</span></span>|  
|------------|-----------------|  
|`cssAccurate`|<span data-ttu-id="64278-108">İade değerinin tam olması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="64278-108">Specifies that the return value should be exact.</span></span>|  
|`cssQuick`|<span data-ttu-id="64278-109">İade değerinin tahmin edilmesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="64278-109">Specifies that the return value should be estimated.</span></span>|  
|`cssDiscardTransientCAs`|<span data-ttu-id="64278-110">Atılabilir türlerin kaldırılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="64278-110">Specifies that discardable types should be removed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="64278-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="64278-111">Requirements</span></span>  
 <span data-ttu-id="64278-112">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="64278-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64278-113">**Üstbilgi:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="64278-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="64278-114">**Kütüphane:** MsCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="64278-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="64278-115">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64278-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64278-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="64278-116">See also</span></span>

- [<span data-ttu-id="64278-117">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="64278-117">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
