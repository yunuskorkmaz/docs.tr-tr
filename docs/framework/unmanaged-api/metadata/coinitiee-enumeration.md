---
title: "COINITIEE Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ad117c3efd31cc176281e571b7fde11229c097e9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="coinitiee-enumeration"></a><span data-ttu-id="80458-102">COINITIEE Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="80458-102">COINITIEE Enumeration</span></span>
<span data-ttu-id="80458-103">Tarafından kullanılan sabitlerini belirtir [Coınitializeee](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) ortak dil çalışma zamanı başlatırken.</span><span class="sxs-lookup"><span data-stu-id="80458-103">Specifies constants used by [CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) when initializing the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80458-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="80458-104">Syntax</span></span>  
  
```  
typedef enum tagCOINITEE {  
   COINITEE_DEFAULT = 0x0,  
   COINITEE_DLL     = 0x1,  
   COINITEE_MAIN    = 0x2  
} COINITIEE;  
```  
  
## <a name="members"></a><span data-ttu-id="80458-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="80458-105">Members</span></span>  
  
|<span data-ttu-id="80458-106">Üye</span><span class="sxs-lookup"><span data-stu-id="80458-106">Member</span></span>|<span data-ttu-id="80458-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="80458-107">Description</span></span>|  
|------------|-----------------|  
|`COINITEE_DEFAULT`|<span data-ttu-id="80458-108">Varsayılan başlatma modu.</span><span class="sxs-lookup"><span data-stu-id="80458-108">Default initialization mode.</span></span> <span data-ttu-id="80458-109">Bu çalışma zamanı başlatır ve varsayılan oluşturur <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="80458-109">This initializes the runtime and creates the default <xref:System.AppDomain>.</span></span>|  
|`COINITEE_DLL`|<span data-ttu-id="80458-110">Yönetilen DLL çalıştırmak için başlatır.</span><span class="sxs-lookup"><span data-stu-id="80458-110">Initializes to run a managed DLL.</span></span>|  
|`COINITEE_MAIN`|<span data-ttu-id="80458-111">Yönetilen bir EXE çalıştırmak için başlatır.</span><span class="sxs-lookup"><span data-stu-id="80458-111">Initializes to run a managed EXE.</span></span> <span data-ttu-id="80458-112">Bu çalışma zamanı başlatır, ancak varsayılan oluşturmaz <xref:System.AppDomain>, hangi EXE ana yordam girdikten sonra oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="80458-112">This initializes the runtime but does not create the default <xref:System.AppDomain>, which is created after entering the main routine of the EXE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="80458-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="80458-113">Requirements</span></span>  
 <span data-ttu-id="80458-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80458-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80458-115">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="80458-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="80458-116">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="80458-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="80458-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80458-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80458-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="80458-118">See Also</span></span>  
 [<span data-ttu-id="80458-119">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="80458-119">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
