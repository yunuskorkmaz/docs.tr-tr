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
ms.openlocfilehash: 3d8189365a73e85c0b9f5efb2aa03074385a3fb8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67750739"
---
# <a name="couninitiee-enumeration"></a><span data-ttu-id="4da62-102">COUNINITIEE Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="4da62-102">COUNINITIEE Enumeration</span></span>
<span data-ttu-id="4da62-103">Tarafından kullanılan sabitlerini belirtir [CoUninitializeEE](../../../../docs/framework/unmanaged-api/hosting/couninitializeee-function.md) ortak dil çalışma zamanı başlatılırken.</span><span class="sxs-lookup"><span data-stu-id="4da62-103">Specifies constants used by [CoUninitializeEE](../../../../docs/framework/unmanaged-api/hosting/couninitializeee-function.md) when initializing the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4da62-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4da62-104">Syntax</span></span>  
  
```cpp  
typedef enum tagCOUNINITEE  
{  
    COUNINITEE_DEFAULT  = 0x0,   
    COUNINITEE_DLL      = 0x1  
} COUNINITIEE;  
```  
  
## <a name="members"></a><span data-ttu-id="4da62-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="4da62-105">Members</span></span>  
  
|<span data-ttu-id="4da62-106">Üye</span><span class="sxs-lookup"><span data-stu-id="4da62-106">Member</span></span>|<span data-ttu-id="4da62-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4da62-107">Description</span></span>|  
|------------|-----------------|  
|`COUNINITEE_DEFAULT`|<span data-ttu-id="4da62-108">Varsayılan başlatmasını geri modunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="4da62-108">Indicates default uninitialization mode.</span></span>|  
|`COUNINITEE_DLL`|<span data-ttu-id="4da62-109">Bir derlemeyi kaldırılması için başlatmasını geri modunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="4da62-109">Indicates uninitialization mode for unloading an assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4da62-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4da62-110">Requirements</span></span>  
 <span data-ttu-id="4da62-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4da62-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4da62-112">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="4da62-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4da62-113">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="4da62-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4da62-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4da62-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4da62-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4da62-115">See also</span></span>

- [<span data-ttu-id="4da62-116">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="4da62-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
