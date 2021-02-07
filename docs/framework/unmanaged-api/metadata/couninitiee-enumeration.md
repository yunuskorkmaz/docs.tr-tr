---
description: 'Daha fazla bilgi edinin: COUNıNITIEE numaralandırması'
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
ms.openlocfilehash: 893ab96851e9c762a888f3c4cac98b486a0b4614
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707241"
---
# <a name="couninitiee-enumeration"></a><span data-ttu-id="317a8-103">COUNINITIEE Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="317a8-103">COUNINITIEE Enumeration</span></span>

<span data-ttu-id="317a8-104">Ortak dil çalışma zamanı başlatılırken [Counınitialeee](../hosting/couninitializeee-function.md) tarafından kullanılan sabitleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="317a8-104">Specifies constants used by [CoUninitializeEE](../hosting/couninitializeee-function.md) when initializing the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="317a8-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="317a8-105">Syntax</span></span>  
  
```cpp  
typedef enum tagCOUNINITEE  
{  
    COUNINITEE_DEFAULT  = 0x0,
    COUNINITEE_DLL      = 0x1  
} COUNINITIEE;  
```  
  
## <a name="members"></a><span data-ttu-id="317a8-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="317a8-106">Members</span></span>  
  
|<span data-ttu-id="317a8-107">Üye</span><span class="sxs-lookup"><span data-stu-id="317a8-107">Member</span></span>|<span data-ttu-id="317a8-108">Description</span><span class="sxs-lookup"><span data-stu-id="317a8-108">Description</span></span>|  
|------------|-----------------|  
|`COUNINITEE_DEFAULT`|<span data-ttu-id="317a8-109">Varsayılan başlatma modunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="317a8-109">Indicates default uninitialization mode.</span></span>|  
|`COUNINITEE_DLL`|<span data-ttu-id="317a8-110">Bir derlemeyi kaldırmak için başlatma modunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="317a8-110">Indicates uninitialization mode for unloading an assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="317a8-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="317a8-111">Requirements</span></span>  

 <span data-ttu-id="317a8-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="317a8-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="317a8-113">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="317a8-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="317a8-114">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="317a8-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="317a8-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="317a8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="317a8-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="317a8-116">See also</span></span>

- [<span data-ttu-id="317a8-117">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="317a8-117">Metadata Enumerations</span></span>](metadata-enumerations.md)
