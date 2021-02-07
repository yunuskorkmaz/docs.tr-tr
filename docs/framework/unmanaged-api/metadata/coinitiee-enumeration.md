---
description: 'Daha fazla bilgi edinin: COINITIEE numaralandırması'
title: COINITIEE Numaralandırması
ms.date: 03/30/2017
api_name:
- COINITIEE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COINITIEE
helpviewer_keywords:
- COINITIEE enumeration [.NET Framework metadata]
ms.assetid: 64264238-3b68-4bac-a887-36b552426a6c
topic_type:
- apiref
ms.openlocfilehash: c17980582903a29cdfe33c64200c31f29ddeb17c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99678620"
---
# <a name="coinitiee-enumeration"></a><span data-ttu-id="b3813-103">COINITIEE Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="b3813-103">COINITIEE Enumeration</span></span>

<span data-ttu-id="b3813-104">Ortak dil çalışma zamanı başlatılırken [Coınitialeee](../hosting/coinitializeee-function.md) tarafından kullanılan sabitleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="b3813-104">Specifies constants used by [CoInitializeEE](../hosting/coinitializeee-function.md) when initializing the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3813-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="b3813-105">Syntax</span></span>  
  
```cpp  
typedef enum tagCOINITEE {  
   COINITEE_DEFAULT = 0x0,  
   COINITEE_DLL     = 0x1,  
   COINITEE_MAIN    = 0x2  
} COINITIEE;  
```  
  
## <a name="members"></a><span data-ttu-id="b3813-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="b3813-106">Members</span></span>  
  
|<span data-ttu-id="b3813-107">Üye</span><span class="sxs-lookup"><span data-stu-id="b3813-107">Member</span></span>|<span data-ttu-id="b3813-108">Description</span><span class="sxs-lookup"><span data-stu-id="b3813-108">Description</span></span>|  
|------------|-----------------|  
|`COINITEE_DEFAULT`|<span data-ttu-id="b3813-109">Varsayılan başlatma modu.</span><span class="sxs-lookup"><span data-stu-id="b3813-109">Default initialization mode.</span></span> <span data-ttu-id="b3813-110">Bu, çalışma zamanını başlatır ve varsayılan olarak oluşturur <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="b3813-110">This initializes the runtime and creates the default <xref:System.AppDomain>.</span></span>|  
|`COINITEE_DLL`|<span data-ttu-id="b3813-111">Yönetilen DLL çalıştırmak için başlatılır.</span><span class="sxs-lookup"><span data-stu-id="b3813-111">Initializes to run a managed DLL.</span></span>|  
|`COINITEE_MAIN`|<span data-ttu-id="b3813-112">Yönetilen bir EXE çalıştırmak için başlatılır.</span><span class="sxs-lookup"><span data-stu-id="b3813-112">Initializes to run a managed EXE.</span></span> <span data-ttu-id="b3813-113">Bu, çalışma zamanını başlatır, ancak varsayılan <xref:System.AppDomain> olarak exe 'nin ana yordamını girdikten sonra oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b3813-113">This initializes the runtime but does not create the default <xref:System.AppDomain>, which is created after entering the main routine of the EXE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b3813-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b3813-114">Requirements</span></span>  

 <span data-ttu-id="b3813-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b3813-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3813-116">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="b3813-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b3813-117">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="b3813-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b3813-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3813-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3813-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b3813-119">See also</span></span>

- [<span data-ttu-id="b3813-120">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="b3813-120">Metadata Enumerations</span></span>](metadata-enumerations.md)
