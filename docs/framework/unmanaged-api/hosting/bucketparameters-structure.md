---
title: BucketParameters Yapısı
ms.date: 03/30/2017
api_name:
- BucketParameters
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- BucketParameters
helpviewer_keywords:
- BucketParameters structure [.NET Framework hosting]
ms.assetid: 9432487e-f276-45d6-9a13-9a68024dbd46
topic_type:
- apiref
ms.openlocfilehash: 4d9de489bdeb0ab506f56ff08f4afb4cf6d0ab4f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178281"
---
# <a name="bucketparameters-structure"></a><span data-ttu-id="7ab9d-102">BucketParameters Yapısı</span><span class="sxs-lookup"><span data-stu-id="7ab9d-102">BucketParameters Structure</span></span>
<span data-ttu-id="7ab9d-103">Bir olayın türü ve olayla ilişkili geçerli özel durum parametrelerini depolar.</span><span class="sxs-lookup"><span data-stu-id="7ab9d-103">Stores the type name of an event and the parameters for the current exception that is associated with the event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ab9d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7ab9d-104">Syntax</span></span>  
  
```cpp  
typedef struct _BucketParameters {  
    BOOL  fInited;
    WCHAR pszEventTypeName[255];
    WCHAR pszParams[10][255];
} BucketParameters;  
```  
  
## <a name="members"></a><span data-ttu-id="7ab9d-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="7ab9d-105">Members</span></span>  
  
|<span data-ttu-id="7ab9d-106">Üye</span><span class="sxs-lookup"><span data-stu-id="7ab9d-106">Member</span></span>|<span data-ttu-id="7ab9d-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7ab9d-107">Description</span></span>|  
|------------|-----------------|  
|`fInited`|<span data-ttu-id="7ab9d-108">`true`, Bu yapının geri kalanı geçerliise; aksi `false`takdirde, .</span><span class="sxs-lookup"><span data-stu-id="7ab9d-108">`true`, if the rest of this structure is valid; otherwise, `false`.</span></span>|  
|`pszEventTypeName`|<span data-ttu-id="7ab9d-109">Olay türünün adı.</span><span class="sxs-lookup"><span data-stu-id="7ab9d-109">Name of the event type.</span></span>|  
|`pszParams`|<span data-ttu-id="7ab9d-110">Her biri olayla ilişkili geçerli özel durum için bir parametre belirten bir dizi dize.</span><span class="sxs-lookup"><span data-stu-id="7ab9d-110">An array of strings, each of which specifies a parameter for the current exception associated with the event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7ab9d-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7ab9d-111">Requirements</span></span>  
 <span data-ttu-id="7ab9d-112">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ab9d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ab9d-113">**Üstbilgi:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="7ab9d-113">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="7ab9d-114">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ab9d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ab9d-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7ab9d-115">See also</span></span>

- [<span data-ttu-id="7ab9d-116">Barındırma Yapıları</span><span class="sxs-lookup"><span data-stu-id="7ab9d-116">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
