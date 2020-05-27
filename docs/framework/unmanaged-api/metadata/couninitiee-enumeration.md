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
ms.openlocfilehash: 14942680a79c4d1fcc69092a4f752738db1fb0b0
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008927"
---
# <a name="couninitiee-enumeration"></a><span data-ttu-id="42f62-102">COUNINITIEE Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="42f62-102">COUNINITIEE Enumeration</span></span>
<span data-ttu-id="42f62-103">Ortak dil çalışma zamanı başlatılırken [Counınitialeee](../hosting/couninitializeee-function.md) tarafından kullanılan sabitleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="42f62-103">Specifies constants used by [CoUninitializeEE](../hosting/couninitializeee-function.md) when initializing the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42f62-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="42f62-104">Syntax</span></span>  
  
```cpp  
typedef enum tagCOUNINITEE  
{  
    COUNINITEE_DEFAULT  = 0x0,
    COUNINITEE_DLL      = 0x1  
} COUNINITIEE;  
```  
  
## <a name="members"></a><span data-ttu-id="42f62-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="42f62-105">Members</span></span>  
  
|<span data-ttu-id="42f62-106">Üye</span><span class="sxs-lookup"><span data-stu-id="42f62-106">Member</span></span>|<span data-ttu-id="42f62-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="42f62-107">Description</span></span>|  
|------------|-----------------|  
|`COUNINITEE_DEFAULT`|<span data-ttu-id="42f62-108">Varsayılan başlatma modunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="42f62-108">Indicates default uninitialization mode.</span></span>|  
|`COUNINITEE_DLL`|<span data-ttu-id="42f62-109">Bir derlemeyi kaldırmak için başlatma modunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="42f62-109">Indicates uninitialization mode for unloading an assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="42f62-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="42f62-110">Requirements</span></span>  
 <span data-ttu-id="42f62-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42f62-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42f62-112">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="42f62-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="42f62-113">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="42f62-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="42f62-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42f62-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42f62-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="42f62-115">See also</span></span>

- [<span data-ttu-id="42f62-116">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="42f62-116">Metadata Enumerations</span></span>](metadata-enumerations.md)
