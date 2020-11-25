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
ms.openlocfilehash: b0f8c7e6d2acf4d4c080cc147bf6d42bf13cb51b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723837"
---
# <a name="couninitiee-enumeration"></a><span data-ttu-id="13f5d-102">COUNINITIEE Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="13f5d-102">COUNINITIEE Enumeration</span></span>

<span data-ttu-id="13f5d-103">Ortak dil çalışma zamanı başlatılırken [Counınitialeee](../hosting/couninitializeee-function.md) tarafından kullanılan sabitleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="13f5d-103">Specifies constants used by [CoUninitializeEE](../hosting/couninitializeee-function.md) when initializing the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13f5d-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="13f5d-104">Syntax</span></span>  
  
```cpp  
typedef enum tagCOUNINITEE  
{  
    COUNINITEE_DEFAULT  = 0x0,
    COUNINITEE_DLL      = 0x1  
} COUNINITIEE;  
```  
  
## <a name="members"></a><span data-ttu-id="13f5d-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="13f5d-105">Members</span></span>  
  
|<span data-ttu-id="13f5d-106">Üye</span><span class="sxs-lookup"><span data-stu-id="13f5d-106">Member</span></span>|<span data-ttu-id="13f5d-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="13f5d-107">Description</span></span>|  
|------------|-----------------|  
|`COUNINITEE_DEFAULT`|<span data-ttu-id="13f5d-108">Varsayılan başlatma modunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="13f5d-108">Indicates default uninitialization mode.</span></span>|  
|`COUNINITEE_DLL`|<span data-ttu-id="13f5d-109">Bir derlemeyi kaldırmak için başlatma modunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="13f5d-109">Indicates uninitialization mode for unloading an assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="13f5d-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="13f5d-110">Requirements</span></span>  

 <span data-ttu-id="13f5d-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13f5d-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13f5d-112">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="13f5d-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="13f5d-113">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="13f5d-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="13f5d-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13f5d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13f5d-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="13f5d-115">See also</span></span>

- [<span data-ttu-id="13f5d-116">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="13f5d-116">Metadata Enumerations</span></span>](metadata-enumerations.md)
