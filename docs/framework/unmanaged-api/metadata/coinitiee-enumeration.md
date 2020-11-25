---
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
ms.openlocfilehash: 673450bb8209abede15e3cb65dd764b418073bc2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724201"
---
# <a name="coinitiee-enumeration"></a><span data-ttu-id="ac12c-102">COINITIEE Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="ac12c-102">COINITIEE Enumeration</span></span>

<span data-ttu-id="ac12c-103">Ortak dil çalışma zamanı başlatılırken [Coınitialeee](../hosting/coinitializeee-function.md) tarafından kullanılan sabitleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="ac12c-103">Specifies constants used by [CoInitializeEE](../hosting/coinitializeee-function.md) when initializing the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac12c-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="ac12c-104">Syntax</span></span>  
  
```cpp  
typedef enum tagCOINITEE {  
   COINITEE_DEFAULT = 0x0,  
   COINITEE_DLL     = 0x1,  
   COINITEE_MAIN    = 0x2  
} COINITIEE;  
```  
  
## <a name="members"></a><span data-ttu-id="ac12c-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="ac12c-105">Members</span></span>  
  
|<span data-ttu-id="ac12c-106">Üye</span><span class="sxs-lookup"><span data-stu-id="ac12c-106">Member</span></span>|<span data-ttu-id="ac12c-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ac12c-107">Description</span></span>|  
|------------|-----------------|  
|`COINITEE_DEFAULT`|<span data-ttu-id="ac12c-108">Varsayılan başlatma modu.</span><span class="sxs-lookup"><span data-stu-id="ac12c-108">Default initialization mode.</span></span> <span data-ttu-id="ac12c-109">Bu, çalışma zamanını başlatır ve varsayılan olarak oluşturur <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="ac12c-109">This initializes the runtime and creates the default <xref:System.AppDomain>.</span></span>|  
|`COINITEE_DLL`|<span data-ttu-id="ac12c-110">Yönetilen DLL çalıştırmak için başlatılır.</span><span class="sxs-lookup"><span data-stu-id="ac12c-110">Initializes to run a managed DLL.</span></span>|  
|`COINITEE_MAIN`|<span data-ttu-id="ac12c-111">Yönetilen bir EXE çalıştırmak için başlatılır.</span><span class="sxs-lookup"><span data-stu-id="ac12c-111">Initializes to run a managed EXE.</span></span> <span data-ttu-id="ac12c-112">Bu, çalışma zamanını başlatır, ancak varsayılan <xref:System.AppDomain> olarak exe 'nin ana yordamını girdikten sonra oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="ac12c-112">This initializes the runtime but does not create the default <xref:System.AppDomain>, which is created after entering the main routine of the EXE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ac12c-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ac12c-113">Requirements</span></span>  

 <span data-ttu-id="ac12c-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac12c-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac12c-115">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="ac12c-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ac12c-116">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="ac12c-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ac12c-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac12c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac12c-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ac12c-118">See also</span></span>

- [<span data-ttu-id="ac12c-119">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="ac12c-119">Metadata Enumerations</span></span>](metadata-enumerations.md)
