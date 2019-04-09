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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0cf1bfa03fd14d6324af60781003a8072a267a7e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59102953"
---
# <a name="couninitiee-enumeration"></a><span data-ttu-id="666e9-102">COUNINITIEE Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="666e9-102">COUNINITIEE Enumeration</span></span>
<span data-ttu-id="666e9-103">Tarafından kullanılan sabitlerini belirtir [CoUninitializeEE](../../../../docs/framework/unmanaged-api/hosting/couninitializeee-function.md) ortak dil çalışma zamanı başlatılırken.</span><span class="sxs-lookup"><span data-stu-id="666e9-103">Specifies constants used by [CoUninitializeEE](../../../../docs/framework/unmanaged-api/hosting/couninitializeee-function.md) when initializing the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="666e9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="666e9-104">Syntax</span></span>  
  
```  
typedef enum tagCOUNINITEE  
{  
    COUNINITEE_DEFAULT  = 0x0,   
    COUNINITEE_DLL      = 0x1  
} COUNINITIEE;  
```  
  
## <a name="members"></a><span data-ttu-id="666e9-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="666e9-105">Members</span></span>  
  
|<span data-ttu-id="666e9-106">Üye</span><span class="sxs-lookup"><span data-stu-id="666e9-106">Member</span></span>|<span data-ttu-id="666e9-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="666e9-107">Description</span></span>|  
|------------|-----------------|  
|`COUNINITEE_DEFAULT`|<span data-ttu-id="666e9-108">Varsayılan başlatmasını geri modunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="666e9-108">Indicates default uninitialization mode.</span></span>|  
|`COUNINITEE_DLL`|<span data-ttu-id="666e9-109">Bir derlemeyi kaldırılması için başlatmasını geri modunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="666e9-109">Indicates uninitialization mode for unloading an assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="666e9-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="666e9-110">Requirements</span></span>  
 <span data-ttu-id="666e9-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="666e9-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="666e9-112">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="666e9-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="666e9-113">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="666e9-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="666e9-114">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="666e9-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="666e9-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="666e9-115">See also</span></span>

- [<span data-ttu-id="666e9-116">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="666e9-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
