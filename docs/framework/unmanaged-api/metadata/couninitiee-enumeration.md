---
title: COUNINITIEE Numaralandırması
ms.date: 03/30/2017
api_name:
- COUNINITIEE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COUNINITIEE
helpviewer_keywords:
- COUNINITIEE enumeration [.NET Framework metadata]
ms.assetid: c42baa79-f469-4330-95a2-baf7f021c2fc
topic_type:
- apiref
ms.openlocfilehash: e5cbd8c5b1bb048088fe137b1359d0bb9e29af20
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176129"
---
# <a name="couninitiee-enumeration"></a><span data-ttu-id="37f9b-102">COUNINITIEE Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="37f9b-102">COUNINITIEE Enumeration</span></span>
<span data-ttu-id="37f9b-103">Ortak dil çalışma süresini başlatmada [CoUninitializeEE](../../../../docs/framework/unmanaged-api/hosting/couninitializeee-function.md) tarafından kullanılan sabitleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="37f9b-103">Specifies constants used by [CoUninitializeEE](../../../../docs/framework/unmanaged-api/hosting/couninitializeee-function.md) when initializing the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37f9b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="37f9b-104">Syntax</span></span>  
  
```cpp  
typedef enum tagCOUNINITEE  
{  
    COUNINITEE_DEFAULT  = 0x0,
    COUNINITEE_DLL      = 0x1  
} COUNINITIEE;  
```  
  
## <a name="members"></a><span data-ttu-id="37f9b-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="37f9b-105">Members</span></span>  
  
|<span data-ttu-id="37f9b-106">Üye</span><span class="sxs-lookup"><span data-stu-id="37f9b-106">Member</span></span>|<span data-ttu-id="37f9b-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="37f9b-107">Description</span></span>|  
|------------|-----------------|  
|`COUNINITEE_DEFAULT`|<span data-ttu-id="37f9b-108">Varsayılan önbaşlatma modunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="37f9b-108">Indicates default uninitialization mode.</span></span>|  
|`COUNINITEE_DLL`|<span data-ttu-id="37f9b-109">Bir derlemeyi boşaltmak için başlatma modunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="37f9b-109">Indicates uninitialization mode for unloading an assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="37f9b-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="37f9b-110">Requirements</span></span>  
 <span data-ttu-id="37f9b-111">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37f9b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37f9b-112">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="37f9b-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="37f9b-113">**Kütüphane:** MsCorEE.dll bir kaynak olarak dahil</span><span class="sxs-lookup"><span data-stu-id="37f9b-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="37f9b-114">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37f9b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37f9b-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="37f9b-115">See also</span></span>

- [<span data-ttu-id="37f9b-116">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="37f9b-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
