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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4a84fdfdba96c58671302c723b8a56848b70eb60
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59180031"
---
# <a name="coinitiee-enumeration"></a><span data-ttu-id="ac235-102">COINITIEE Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="ac235-102">COINITIEE Enumeration</span></span>
<span data-ttu-id="ac235-103">Tarafından kullanılan sabitlerini belirtir [Coınitializeee](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) ortak dil çalışma zamanı başlatılırken.</span><span class="sxs-lookup"><span data-stu-id="ac235-103">Specifies constants used by [CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) when initializing the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac235-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ac235-104">Syntax</span></span>  
  
```  
typedef enum tagCOINITEE {  
   COINITEE_DEFAULT = 0x0,  
   COINITEE_DLL     = 0x1,  
   COINITEE_MAIN    = 0x2  
} COINITIEE;  
```  
  
## <a name="members"></a><span data-ttu-id="ac235-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="ac235-105">Members</span></span>  
  
|<span data-ttu-id="ac235-106">Üye</span><span class="sxs-lookup"><span data-stu-id="ac235-106">Member</span></span>|<span data-ttu-id="ac235-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ac235-107">Description</span></span>|  
|------------|-----------------|  
|`COINITEE_DEFAULT`|<span data-ttu-id="ac235-108">Varsayılan başlatma modu.</span><span class="sxs-lookup"><span data-stu-id="ac235-108">Default initialization mode.</span></span> <span data-ttu-id="ac235-109">Bu çalışma zamanı başlatır ve varsayılan oluşturur <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="ac235-109">This initializes the runtime and creates the default <xref:System.AppDomain>.</span></span>|  
|`COINITEE_DLL`|<span data-ttu-id="ac235-110">Yönetilen bir DLL'yi çalıştırılacak başlatır.</span><span class="sxs-lookup"><span data-stu-id="ac235-110">Initializes to run a managed DLL.</span></span>|  
|`COINITEE_MAIN`|<span data-ttu-id="ac235-111">Yönetilen bir EXE çalıştırılacak başlatır.</span><span class="sxs-lookup"><span data-stu-id="ac235-111">Initializes to run a managed EXE.</span></span> <span data-ttu-id="ac235-112">Bu çalışma zamanı başlatır, ancak varsayılan oluşturmaz <xref:System.AppDomain>, hangi EXE dosyasının ana yordam girdikten sonra oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="ac235-112">This initializes the runtime but does not create the default <xref:System.AppDomain>, which is created after entering the main routine of the EXE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ac235-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ac235-113">Requirements</span></span>  
 <span data-ttu-id="ac235-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac235-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac235-115">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="ac235-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ac235-116">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="ac235-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ac235-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac235-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac235-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ac235-118">See also</span></span>

- [<span data-ttu-id="ac235-119">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="ac235-119">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
