---
title: "COUNINITIEE Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COUNINITIEE
api_location: mscoree.dll
api_type: COM
f1_keywords: COUNINITIEE
helpviewer_keywords: COUNINITIEE enumeration [.NET Framework metadata]
ms.assetid: c42baa79-f469-4330-95a2-baf7f021c2fc
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 808320a2034011793429f1805edea82a52add23d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="couninitiee-enumeration"></a><span data-ttu-id="e8298-102">COUNINITIEE Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="e8298-102">COUNINITIEE Enumeration</span></span>
<span data-ttu-id="e8298-103">Tarafından kullanılan sabitlerini belirtir [CoUninitializeEE](../../../../docs/framework/unmanaged-api/hosting/couninitializeee-function.md) ortak dil çalışma zamanı başlatırken.</span><span class="sxs-lookup"><span data-stu-id="e8298-103">Specifies constants used by [CoUninitializeEE](../../../../docs/framework/unmanaged-api/hosting/couninitializeee-function.md) when initializing the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8298-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e8298-104">Syntax</span></span>  
  
```  
typedef enum tagCOUNINITEE  
{  
    COUNINITEE_DEFAULT  = 0x0,   
    COUNINITEE_DLL      = 0x1  
} COUNINITIEE;  
```  
  
## <a name="members"></a><span data-ttu-id="e8298-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="e8298-105">Members</span></span>  
  
|<span data-ttu-id="e8298-106">Üye</span><span class="sxs-lookup"><span data-stu-id="e8298-106">Member</span></span>|<span data-ttu-id="e8298-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e8298-107">Description</span></span>|  
|------------|-----------------|  
|`COUNINITEE_DEFAULT`|<span data-ttu-id="e8298-108">Varsayılan başlatılmaması modunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="e8298-108">Indicates default uninitialization mode.</span></span>|  
|`COUNINITEE_DLL`|<span data-ttu-id="e8298-109">Bir derlemeyi kaldırılması için başlatılmaması modunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="e8298-109">Indicates uninitialization mode for unloading an assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e8298-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e8298-110">Requirements</span></span>  
 <span data-ttu-id="e8298-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e8298-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8298-112">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e8298-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e8298-113">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="e8298-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e8298-114">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8298-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8298-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e8298-115">See Also</span></span>  
 [<span data-ttu-id="e8298-116">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="e8298-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
